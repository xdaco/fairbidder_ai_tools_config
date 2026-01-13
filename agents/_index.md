---
title: "Agents & Project Guidelines"
description: "Central hub for global coding standards, project-specific agents, and workflow guidelines"
lastUpdated: "2026-01-13"
---

# Agents & Project Guidelines

This directory contains **global** and **project-specific** guidance for coding, development, and agent usage. It ensures **consistency**, **quality**, and **maintainability** across all projects.  

---

## Global Guidelines

- **Claude Context**: [claude.md](../claude.md)  
  Defines global coding preferences, workflow conventions, and best practices for all projects.

- **Cursor Rules**: [cursor.md](../cursor.md)  
  Defines project-agnostic rules covering:
  - TypeScript configuration and strictness
  - React best practices and component patterns
  - Tailwind and CSS usage
  - Import ordering and linting
  - Testing and error handling
  - Security, accessibility, and performance

- **React Style Guide**: [react_coding_standard.md](react_coding_standard.md)  
  Covers:
  - Component design and folder structure
  - Hooks usage and state management
  - Custom hooks for reusable logic
  - JSX conventions and props handling
  - Error handling and logging
  - Lazy-loading and code splitting
  - TypeScript integration and typing rules
  - Key prop uniqueness and avoiding prop drilling
  - Security (XSS prevention) and accessibility

---

## Project-Specific Agents

### Fairbidder Project Agent
- **Agent File**: [fairbidder_agent.yml](fairbidder_agent.yml)  
- **Purpose**: Apply Fairbidder-specific rules, including:
  - UI conventions, branding, and theming
  - Authentication and security standards
  - TypeScript enforcement and React patterns
  - Error handling and logging policies
  - Git commit and workflow conventions
  - Performance optimization best practices

- **Usage**:
  1. Auto-select this agent for Fairbidder projects.
  2. Apply the MCP (Minimum Coding Policy) defined in `fairbidder_agent.yml`.
  3. Validate that project rules do not conflict with global cursor rules.

---

## Agent Selection Guidelines

1. **Global vs Project Agent**:
   - Global agents (Claude & Cursor) apply by default.
   - Project-specific agents **override or extend** global rules for their projects.

2. **Conflict Resolution**:
   - Project-specific rules take priority unless explicitly restricted by MCP.
   - MCP policies **cannot be overridden** and must be followed.

3. **Validation**:
   - Ensure that selected agent rules do not break builds, linting, or formatting.
   - TypeScript, Prettier, and Tailwind conventions must be consistently applied.

---

## Minimum Coding Policy (MCP)

> Baseline rules applied across all projects to ensure maintainable, secure, and high-quality code.

- **Code Formatting**: Enforce via Prettier.
- **TypeScript Strictness**: `strict` mode and `noImplicitAny`.
- **React Best Practices**:
  - Functional components only
  - Hooks usage according to React docs
  - Minimal, composable, and testable components
  - Unique `key` props in lists, avoid array indices
  - Use custom hooks for reusable logic
  - Lazy-loading and code splitting
- **Error Handling**:
  - Cover all async operations
  - Use Error Boundaries for UI errors
  - Log errors to persistent service (e.g., Sentry)
- **Accessibility**:
  - Semantic HTML, ARIA roles, alt text
  - Avoid abstract or redundant attributes
- **Security**:
  - No hardcoded secrets
  - Validate all inputs
  - Parameterized database queries
  - Sanitize HTML to prevent XSS

> MCP is applied globally and **cannot** be overridden by project agents.

---

## References

- [Global Claude Context](../claude.md)  
- [Global Cursor Rules](../cursor.md)  
- [React Coding Standard](react_coding_standard.md)  
- [Fairbidder Agent](fairbidder_agent.yml)
