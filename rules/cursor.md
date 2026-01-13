# Global Cursor Rules

> Generic coding rules and project conventions applied across all projects.

---

## Code Formatting

- **Always format with Prettier** before saving, after editing, and before committing.
- Use project-specific Prettier config if available; otherwise:
  - Print width: 80
  - Tab width: 4 spaces
  - Semicolons: true
  - Quotes: double
  - Trailing commas: all
  - Bracket spacing: true
  - Arrow function parentheses: always
- Apply formatting to all supported files: JS, TS, JSX, TSX, JSON, CSS/SCSS, HTML, Markdown, YAML.

---

## TypeScript Rules

- Avoid implicit `any`.
- Use strict typing; prefer `interface` over `type` for objects.
- Always fix TypeScript errors; only use `@ts-expect-error` when unavoidable.

---

## Git & Commits

- Commit only formatted, build-passing code.
- Use conventional commit format: `feat:`, `fix:`, `docs:`, `refactor:`, `test:`.
- Keep commits small and focused.
- Never commit secrets or API keys.

---

## Code Quality

- No `console.log` in production.
- Handle all errors; no empty try-catch blocks.
- Use meaningful variable names; avoid single letters except in loops.
- Keep functions small and focused.
- Follow DRY principle; extract common logic.

---

## Security

- Never commit sensitive data.
- Validate all input; sanitize before database queries.
- Implement proper authentication/authorization checks.

---

## Performance

- Lazy-load routes and heavy components.
- Optimize images and assets.
- Minimize bundle size.
- Use memoization for expensive components.
- Avoid unnecessary re-renders.

---

## FORBIDDEN

- ❌ Guessing about code
- ❌ Large refactors without approval
- ❌ Over-engineering
- ❌ Truncated code (`...`)
- ❌ `var` in JavaScript
