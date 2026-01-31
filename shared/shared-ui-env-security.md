# Shared UI: No Supabase env in library (MUST FOLLOW)

## Why this rule exists

The `shared_ui` package is a **library** consumed by multiple applications (buyer, seller, affiliate, admin). If shared_ui source code reads `import.meta.env.VITE_SUPABASE_URL` or `VITE_SUPABASE_ANON_KEY`, those values can be **baked into shared_ui's dist** when the library is built. Every app that uses the pre-built shared_ui dist would then ship those credentials in its deployed JavaScript, leaking configuration and creating a security risk. Credentials must come from the **consuming app** at runtime via `initEnvConfig()`, not from the library build environment.

## Must-follow rules

- **MUST**: In `shared_ui` source code, **never** use `import.meta.env.VITE_SUPABASE_URL` or `import.meta.env.VITE_SUPABASE_ANON_KEY`.
- **MUST**: **Always** get Supabase URL and anon key via `getEnvConfig()` from `@/config/env-config` (after the consuming app has called `initEnvConfig()`).
- **Exception**: Type declarations only (e.g. `vite-env.d.ts`) that declare the existence of these env vars for TypeScript—no runtime usage of `import.meta.env.VITE_SUPABASE_*` in shared_ui.
- **When adding new code**: Any new Supabase URL or anon key usage in shared_ui must use `getEnvConfig()`; do not add new `import.meta.env.VITE_SUPABASE_*` references.

## Allowed

- `getEnvConfig()`, `initEnvConfig()`, `isEnvConfigInitialized()` from `@/config/env-config`.

## Forbidden

- `import.meta.env.VITE_SUPABASE_URL`, `import.meta.env.VITE_SUPABASE_ANON_KEY` in shared_ui `src/` (except type-only declaration files).

## API server and Supabase usage

- **All data and business APIs** go through the Fairbidder **api_server** (RFQ, bids, messages, auth/me, security events, etc.). The shared_ui API client is initialized with `initAPI({ baseURL: getAPIBaseURL() })` in each app; `getAuthToken` returns the API JWT (from login/refresh).
- **Supabase** is used only for **auth flows** (OAuth redirect, session, `getSession`, `onAuthStateChange`) and **optional realtime** (e.g. messages table subscription). Supabase URL and anon key are injected at runtime by the host app via `initEnvConfig()`.

## Enforcement

- The shared_ui build runs `check:no-supabase-env` before building; the build fails if the forbidden pattern is found.
- CI should run this check (or the full shared_ui build) so PRs cannot introduce violations.
