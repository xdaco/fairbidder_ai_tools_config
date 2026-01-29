# Fairbidder Project Rules

> Project-specific coding rules, branding, and architecture conventions for all Fairbidder apps.
> These rules extend the global `cursor.md` rules and should be followed in addition to them.

---

## Branding & Naming

- Always use `Fairbidder` (lowercase 'b') in code.
- Preserve legal company name: `Fairbidder ApS`.
- Preserve package names: `@fairbidder-dk/shared_ui`, `@fairbidder-dk/...`.
- File naming conventions:
  - Components: `PascalCase.tsx`
  - Non-components: `kebab-case.ts` or `.ts`

---

## Shared UI (`@fairbidder-dk/shared_ui`)

- **Never embed environment variables** in the `shared_ui` build.
- Use runtime configuration with `initEnvConfig()` / `getEnvConfig()`.
- Supabase config in shared_ui must come only from `getEnvConfig()`; see ai_tools_config/shared/shared-ui-env-security.md for the mandatory rule.
- Keep `envDir: false` and the Supabase `define` overrides in `shared_ui/vite.config.ts`. Supabase in shared_ui: use getEnvConfig() only; see ai_tools_config/shared/shared-ui-env-security.md.
- Auth components: always use `SharedLogin`.
- Visual consistency: maintain glass panels and animated gradient backgrounds for auth pages.

---

## Authentication & Roles

- All apps must use `SharedLogin`.
- Admin users can log in to any app.
- Role-based access via `useLoginRedirect` hook.
- Use `variant="glass"` for all auth pages (Login, Register, EmailConfirm).
- Maintain consistent visual design across Buyer, Seller, and Affiliate apps.

---

## TypeScript & Code Practices

- Always use strict typing.
- Avoid `any`; use `unknown` if necessary.
- Add `@ts-expect-error` only for unavoidable module resolution issues.
- Never leave TypeScript errors unfixed.
- Functions should be small, focused, and single-purpose.
- Add comments explaining **why**, not **what**, for complex logic.
- Keep variable names meaningful; avoid single letters (except loop counters).

---

## Code Quality Standards

- **No `console.log` in production** – use proper logging utilities.
- Always handle errors; never leave empty try-catch blocks.
- Follow DRY principle; extract shared logic.
- Keep components and functions small and maintainable.
- Run Prettier before saving and committing files.

---

## Git & Commits

- Commit messages must be descriptive and follow conventional commit format.
- Never commit unformatted or build-failing code.
- Run linter and formatter before pushing.

---

## Performance

- Lazy-load heavy components and routes.
- Optimize images and assets (compression, WebP).
- Minimize bundle size.
- Use `React.memo` or `useMemo` for expensive components.
- Avoid unnecessary re-renders.

---

## Security

- Never commit sensitive data (API keys, passwords, etc.).
- Always validate user input.
- Use parameterized queries for database operations.
- Implement proper authentication and authorization.

---

## Visual Design & UX

- Glass-panel design with animated gradient backgrounds for auth pages.
- Consistent component design across all apps.
- Prefer simplicity and clarity in UI.
- Use Tailwind or shared UI styles for consistent spacing, colors, and typography.

---

## Notes

- These rules **override generic rules** in `cursor.md` where applicable.
- Always follow both global and project-specific rules.
- For new shared features or UI components, document and align with these standards.
