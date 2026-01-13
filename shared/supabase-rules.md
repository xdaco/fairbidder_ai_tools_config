# Supabase Best Practices & Production Rules

Supabase combines **PostgreSQL**, **authentication**, **real-time APIs**, **storage**, and **edge functions** into a unified backend platform. While it’s easy to prototype with, production usage requires careful attention to **security**, **performance**, **scalability**, and **maintenance**.

This document provides guidelines for configuring Supabase safely and efficiently for production workloads.  

---

## 1. Security & Access Control

### 1.1 Row-Level Security (RLS)
RLS is critical for production — it ensures that users can only access rows they are authorized to view.  

**Best Practices:**
- Enable RLS on all user-facing tables:

```sql
ALTER TABLE users ENABLE ROW LEVEL SECURITY;
````

* Define simple, granular policies:

```sql
CREATE POLICY "Users can access own data"
ON users FOR SELECT
USING (auth.uid() = id);
```

* Test policies with different user contexts.
* Avoid overly complex policies with multiple joins or subqueries.
* Combine RLS with **role-based access control (RBAC)** for fine-grained permissions.

### 1.2 API Keys & Secrets

Supabase provides two key types:

* `anon` — safe for client-side use, respects RLS.
* `service_role` — server-side only, bypasses RLS.

**Best Practices:**

* Never expose `service_role` keys in client code.
* Store all keys in environment variables, not in code.
* Rotate keys periodically and revoke compromised keys.
* Use short-lived JWTs for sessions.

### 1.3 Authentication

* Use Supabase Auth instead of custom auth logic.
* Require email confirmation and strong passwords.
* Consider passwordless login with magic links for user experience and security.
* Rate-limit authentication attempts to prevent brute-force attacks.

---

## 2. Schema Design & Data Modeling

### 2.1 Normalization & Denormalization

* Start with a normalized schema.
* Denormalize only when read performance dominates.
* Use foreign keys for relationships; duplicate data cautiously.

### 2.2 Indexing & Partitioning

* Index columns frequently used in `WHERE`, `JOIN`, or `ORDER BY`.
* Partition large tables (e.g., logs) by date or logical groups.
* Use `EXPLAIN ANALYZE` to check query performance.

### 2.3 Multi-Tenant Considerations

* Prefer row-level isolation using a tenant identifier column.
* Apply RLS policies to filter by tenant.
* Schema-per-tenant only if complete data separation is required.

### 2.4 Unique Identifiers & Time-Series Data

* Use UUIDs or ULIDs for distributed systems.
* Include timestamps for events.
* Archive old data to maintain index efficiency.

---

## 3. Real-Time & Edge Functions

### 3.1 Real-Time Subscriptions

* Subscribe only to required tables or filtered rows:

```javascript
supabase
  .from('messages')
  .on('INSERT', payload => { /* ... */ })
  .filter('room_id', 'eq', roomId)
  .subscribe()
```

* Limit payload sizes; unsubscribe when components unmount.
* Debounce or batch events on the client.

### 3.2 Edge Functions

* Keep functions short, stateless, and under ~50ms for low latency.
* Authenticate requests inside functions.
* Offload long-running tasks to external queues or triggers.

---

## 4. Backups & Disaster Recovery

* Enable automated backups and verify restoration.
* Trigger manual backups before schema changes.
* Export backups to separate cloud storage (S3, GCS).
* Document recovery procedures and test them regularly.

---

## 5. CI/CD, Migrations & Deployment

* Manage schema and edge function migrations via Supabase CLI:

```bash
supabase migration new add_user_roles
supabase db push
supabase functions deploy
```

* Version migrations in Git; deploy to staging before production.
* Automate with CI/CD pipelines (GitHub Actions, GitLab CI, etc.).
* Never make manual schema changes directly in production.

---

## 6. Monitoring & Performance

* Enable `pg_stat_statements` for slow query analysis.
* Monitor query duration, connection counts, error rates.
* Use Supabase logs or integrate with external observability tools (Grafana, Datadog, OpenTelemetry).
* Track audit logs for critical actions (user_id, action type, timestamp).

---

## 7. Security & Network Hardening

* Ensure all connections use TLS/SSL.
* Optionally restrict access via IP whitelisting.
* Implement rate limiting on API endpoints.
* Set secure headers in edge functions.

---

## 8. Production Readiness Checklist

Before going live:

* [ ] RLS enabled on all tables
* [ ] Backup strategy tested
* [ ] Service_role keys secured server-side
* [ ] Monitoring and alerting configured
* [ ] CI/CD for schema & functions in place
* [ ] Rate limiting applied
* [ ] SSL enforced
* [ ] Error tracking implemented

---

## 9. Hosting Considerations

* **Supabase Cloud**: Easy to use, great defaults, limited regions/plans.
* **Self-Hosting**: Full control, ideal for enterprise/regulatory requirements, requires DevOps expertise.
* Choose based on compliance, scale, and operational responsibility.

---

## 10. Common Pitfalls

* Skipping RLS during prototyping.
* Exposing `service_role` keys in client code.
* No backup or recovery testing.
* Making manual schema changes in production.
* Overusing real-time subscriptions without filters.

---

## 11. Additional Tips

* Test RLS policies locally before production.
* Use `EXPLAIN ANALYZE` to optimize queries.
* Batch writes and debounce real-time events to reduce load.
* Monitor Supabase free tier limits to prevent throttling or paused projects.
