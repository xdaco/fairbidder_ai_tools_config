# Global Claude Context

> This file defines my general coding preferences, style, conventions, and working rules across all projects.

## Purpose
- Provide a global reference for coding philosophy, workflows, and AI collaboration.
- Individual projects may have their own `claude.md` that overrides project-specific rules.

---

## Critical Rules (Non-Negotiable)
1. **Read code before answering** – never speculate about code you haven’t inspected.
2. **Check in before major changes** – present plans for approval.
3. **Simplicity first** – prefer minimal, incremental changes.
4. **High-level summaries** – always explain **what changed** and **why**.
5. **Maintain documentation** – update architecture docs for any significant change.
6. **Format & build** – always format code (Prettier) and verify builds before marking tasks complete.
7. **Investigate, don’t guess** – base all answers on actual files and evidence.
8. **Never commit secrets** – no API keys, passwords, or sensitive data.

---

## Working Style
- Incremental, focused changes that touch minimal code.
- Break complex tasks into smaller steps.
- Prefer readable, maintainable, and type-safe solutions.
- Always explain reasoning, potential impact, and alternatives.

---

## Coding Preferences

### TypeScript
- Always use TypeScript (strict mode enabled).
- Prefer `interface` for object shapes, `type` for unions/intersections/primitives.
- Avoid `any`; use `unknown` if necessary.
- Always type all function parameters and return values.

### React
- Functional components only; use hooks (`useState`, `useEffect`, `useMemo`, `useCallback`).
- Keep components small, reusable, and composable.
- Prefer composition over prop drilling.

### Styling
- Primary: Tailwind CSS.
- Avoid inline styles unless dynamic.
- Use CSS modules or styled-components for complex styling.
- Mobile-first responsive design.

### Error Handling & Logging
- Always handle errors; never leave try-catch blocks empty.
- Display user-friendly messages.
- Log detailed errors in development only.

### Testing
- Write tests for critical business logic.
- Use descriptive test names.
- Prefer integration tests where practical.
- Mock external services as needed.

### Git Practices
- Conventional commit messages (`feat:`, `fix:`, `docs:`, `refactor:`, `test:`).
- Small, focused commits.
- Always review code before pushing.

### Documentation
- Inline comments for complex logic.
- README.md with setup instructions.
- JSDoc for public APIs.

### Security
- Never hardcode secrets.
- Validate and sanitize all user input.
- Follow OWASP guidelines.
- Keep dependencies updated.

### Performance & Optimization
- Optimize only when necessary (measure first).
- Lazy load heavy components/routes.
- Use memoization (`React.memo`) where needed.
- Optimize images and assets.

### Accessibility
- Semantic HTML and ARIA labels.
- Keyboard navigation support.
- Sufficient color contrast and alt text.

---

## Project Interaction Protocol
- Investigate all relevant files before answering.
- Base answers on actual code, not assumptions.
- Present plans before implementing major changes.
- Keep all changes small and focused.
- Update architecture documentation when significant changes occur.

---

## Communication Style
- High-level explanation first; low-level details only when asked.
- Focus on **what** changed and **why**, not every line.
- Use technical language suitable for a senior developer.
- Avoid unnecessary verbosity; flag critical warnings clearly.

---


