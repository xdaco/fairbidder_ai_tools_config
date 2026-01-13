# AI Tools Configuration

> Central repository for **coding standards**, **project-specific guidelines**, **AI agent configuration**, and **Model Context Protocol (MCP) settings** for Fairbidder projects.

This directory ensures **consistency**, **quality**, and **maintainability** across all development work, providing clear expectations for:
- Code formatting and TypeScript strictness
- React component design and best practices
- Styling conventions with Tailwind CSS
- Project-specific rules for Fairbidder
- Authentication and security standards
- Database design with Supabase
- AI agent workflows and context

---

## 📁 Directory Structure

```
ai_tools_config/
├── rules/                      # Global and project-specific coding rules
│   ├── claude.md              # Global Claude context and coding preferences
│   ├── cursor.md              # Project-agnostic rules (formatting, git, security)
│   ├── fairbidder.md          # Fairbidder-specific branding, auth, and architecture
│   └── agent.md               # Agent-specific rules and guidelines
├── shared/                     # Shared standards applicable across projects
│   ├── coding-standards.md    # React coding standards (adapted from Airbnb style guide)
│   ├── react-tailwind.md      # React & Tailwind CSS best practices
│   └── supabase-rules.md      # Supabase security, schema, and production guidelines
├── agents/                     # AI agent configuration and project guidelines
│   ├── _index.md              # Central hub for agents and project guidelines
│   └── fairbidder_agent.yml   # Fairbidder project agent configuration
├── mcp/                        # Model Context Protocol configurations
│   ├── filesystem.json        # Filesystem MCP configuration
│   ├── github.json            # GitHub MCP configuration
│   └── supabase.json          # Supabase MCP configuration
└── README.md                   # This file
```

---

## 🎯 Quick Start Guide

### 1. **For New Contributors**
Start with the **global rules** to understand baseline expectations:
- Read [rules/claude.md](rules/claude.md) for coding philosophy and critical rules
- Review [rules/cursor.md](rules/cursor.md) for formatting, git, and security standards
- Check [shared/coding-standards.md](shared/coding-standards.md) for React conventions

### 2. **For Fairbidder Project Work**
Apply project-specific standards in addition to global rules:
- Review [rules/fairbidder.md](rules/fairbidder.md) for branding, auth, and UI conventions
- Follow [shared/supabase-rules.md](shared/supabase-rules.md) for database design
- Use [shared/react-tailwind.md](shared/react-tailwind.md) for styling consistency

### 3. **For AI Agents**
- Reference [agents/_index.md](agents/_index.md) for agent selection and guidelines
- Use [agents/fairbidder_agent.yml](agents/fairbidder_agent.yml) for Fairbidder projects
- Follow the **Minimum Coding Policy (MCP)** defined in agents/_index.md

---

## 📚 Detailed Documentation

### **Rules Directory**

#### [claude.md](rules/claude.md)
**Global coding preferences and philosophy**

Key Topics:
- Critical rules (8 non-negotiable principles)
- Working style (incremental, focused changes)
- TypeScript preferences (strict mode, interfaces vs types)
- React conventions (functional components, hooks)
- Styling approach (Tailwind primary)
- Error handling and logging patterns

**Who uses it:** All developers using Claude for code assistance

---

#### [cursor.md](rules/cursor.md)
**Project-agnostic rules for code quality and consistency**

Key Topics:
- Code formatting with Prettier
- TypeScript strictness (`strict` mode, no implicit `any`)
- Git and commit conventions (conventional commits)
- Code quality standards (no console.log, error handling)
- Security practices (input validation, secret management)
- Performance optimization (lazy loading, bundle size)
- Forbidden practices (❌ guessing, large refactors without approval)

**Who uses it:** All contributors to any project

---

#### [fairbidder.md](rules/fairbidder.md)
**Fairbidder-specific coding rules and architecture**

Key Topics:
- Branding and naming conventions (`Fairbidder` lowercase 'b')
- Package naming (`@fairbidder-dk/shared_ui`)
- File naming (PascalCase for components, kebab-case for utilities)
- Shared UI library rules (no embedded env variables, runtime config)
- Authentication standards (`SharedLogin` component, glass variant)
- TypeScript enforcement
- Error handling and logging policies
- Role-based access control
- Database and API conventions

**Who uses it:** Fairbidder project developers

---

#### [agent.md](rules/agent.md)
**Agent-specific workflow guidelines**

Key Topics:
- Agent roles and responsibilities
- Interaction protocols
- Decision-making frameworks
- Escalation procedures
- Documentation requirements

**Who uses it:** AI agents and automated systems

---

### **Shared Standards Directory**

#### [coding-standards.md](shared/coding-standards.md)
**React coding standards (fork of Airbnb style guide)**

Key Topics:
- Basic rules (one component per file, functional components, JSX syntax)
- Naming conventions (PascalCase for components, camelCase for instances)
- Props and state management
- Hooks usage and custom hooks
- JSX spacing, alignment, and formatting
- Comments and documentation
- Performance optimization
- Accessibility and security
- Testing conventions
- File and folder structure

**Sections:**
1. Basic Rules
2. Naming Conventions
3. Component Structure
4. Props
5. State
6. Hooks & Custom Hooks
7. JSX Conventions
8. Comments & Documentation
9. Performance
10. Accessibility & Security
11. Testing
12. Folder Structure

**Who uses it:** React developers building components

---

#### [react-tailwind.md](shared/react-tailwind.md)
**React & Tailwind CSS best practices**

Key Topics:
- Why Tailwind works with React (component-driven design)
- Project setup and configuration
- Componentization (wrapping utility classes)
- Design tokens and configuration
- Responsive design patterns
- Common pitfalls and solutions
- Advanced techniques (custom plugins, animations)
- Performance optimization
- Accessibility with Tailwind
- Tips for large projects

**Sections:**
1. Why Tailwind Works Well with React
2. Project Setup
3. Best Practices
4. Componentization
5. Design Tokens & Config
6. Responsive Design
7. Common Pitfalls & Solutions
8. Advanced Techniques
9. Performance
10. Accessibility
11. Tips for Large Projects

**Who uses it:** Frontend developers styling React components

---

#### [supabase-rules.md](shared/supabase-rules.md)
**Supabase production guidelines and best practices**

Key Topics:
- Security & access control (RLS, API keys, authentication)
- Schema design & data modeling (normalization, indexing, partitioning)
- Multi-tenant considerations
- Real-time subscriptions and edge functions
- Monitoring, logging, and debugging
- Cost optimization
- Migration strategies
- Common pitfalls and production checklist

**Sections:**
1. Security & Access Control
2. Schema Design & Data Modeling
3. Real-Time & Edge Functions
4. Performance & Monitoring
5. Cost Optimization
6. Migration Strategies
7. Production Checklist
8. Common Pitfalls

**Who uses it:** Backend developers and database architects using Supabase

---

### **Agents Directory**

#### [_index.md](agents/_index.md)
**Central hub for global guidelines and agent selection**

Key Topics:
- Global guidelines overview
- Project-specific agents
- Agent selection guidelines (global vs project-specific)
- Conflict resolution
- Minimum Coding Policy (MCP) baseline rules

**MCP Baseline Rules:**
- Code formatting (Prettier)
- TypeScript strictness (`strict` mode)
- React best practices (functional components, hooks)
- Error handling with Error Boundaries
- Accessibility (semantic HTML, ARIA roles)
- Security (no secrets, input validation)

**Who uses it:** AI agents, developers selecting agents, project leads

---

#### [fairbidder_agent.yml](agents/fairbidder_agent.yml)
**Fairbidder project AI agent configuration**

*Currently empty but intended for:*
- Agent-specific prompts and instructions
- Project context initialization
- Tool availability and permissions
- Fallback behaviors
- Integration with Fairbidder-specific tools

---

### **MCP Directory**

#### [filesystem.json](mcp/filesystem.json)
**Filesystem Model Context Protocol configuration**

*Enables AI tools to:*
- Navigate the filesystem
- Read and write files
- Create directories
- Manage file permissions and metadata

---

#### [github.json](mcp/github.json)
**GitHub Model Context Protocol configuration**

*Enables AI tools to:*
- Query repository information
- Create and manage pull requests
- Access commit history
- Manage issues and discussions
- Authenticate with GitHub API

---

#### [supabase.json](mcp/supabase.json)
**Supabase Model Context Protocol configuration**

*Enables AI tools to:*
- Query and manage database tables
- Execute SQL migrations
- Configure RLS policies
- Manage authentication settings
- Access real-time events

---

## 🔑 Key Principles

### **Minimum Coding Policy (MCP)**
These **non-negotiable baseline rules** apply across all projects:

1. **Code Formatting** → Enforce via Prettier
2. **TypeScript Strictness** → `strict` mode enabled
3. **React Best Practices** → Functional components, hooks-based
4. **Error Handling** → Cover all async operations, use Error Boundaries
5. **Accessibility** → Semantic HTML, ARIA roles, alt text
6. **Security** → No hardcoded secrets, input validation, parameterized queries

### **Critical Rules** (from claude.md)
1. ✅ **Read code before answering** – never speculate
2. ✅ **Check in before major changes** – present plans for approval
3. ✅ **Simplicity first** – minimal, incremental changes
4. ✅ **Maintain documentation** – update architecture docs
5. ✅ **Format & build** – always validate before marking complete
6. ✅ **Investigate, don't guess** – base on actual files
7. ✅ **Never commit secrets** – no API keys or passwords

### **Fairbidder-Specific Principles**
- Use `Fairbidder` (lowercase 'b') consistently
- Maintain `@fairbidder-dk/shared_ui` as environment-agnostic
- Use `SharedLogin` component for all authentication
- Apply glass panel variant (`variant="glass"`) for auth pages
- Enforce role-based access control via `useLoginRedirect` hook

---

## 🛠️ How to Use These Guidelines

### **For Code Review**
1. Check if the code follows the **MCP baseline rules**
2. Verify against **project-specific rules** (Fairbidder rules)
3. Confirm **formatting** via Prettier
4. Validate **TypeScript strictness**
5. Check for **security issues** (no secrets, input validation)

### **For Writing New Code**
1. Read relevant rule files for your task
2. Follow naming conventions from **coding-standards.md**
3. Use component patterns from **react-tailwind.md**
4. Apply database practices from **supabase-rules.md**
5. Format with Prettier before committing
6. Ensure TypeScript strictness passes

### **For AI Agents**
1. Load global rules (claude.md, cursor.md)
2. Load project rules (fairbidder.md for Fairbidder projects)
3. Apply MCP baseline rules
4. Use appropriate MCP configurations for database/filesystem access
5. Validate against specific agent configuration (fairbidder_agent.yml)

---

## 📋 Checklist for Contributors

Before submitting code:

- [ ] Code is **formatted** with Prettier
- [ ] **TypeScript** passes strict mode (`npm run type-check`)
- [ ] **Build** passes without errors (`npm run build`)
- [ ] **No console.log** statements in production code
- [ ] **No hardcoded secrets** (API keys, passwords)
- [ ] **Comments explain why, not what** (for complex logic)
- [ ] **File naming** follows conventions (PascalCase for components)
- [ ] **Components are functional** (no class components)
- [ ] **Props are properly typed**
- [ ] **Error handling** is implemented for async operations
- [ ] **Accessibility** basics are covered (alt text, ARIA roles)
- [ ] **Tests** pass (if applicable)
- [ ] **Commit message** uses conventional format

---

## 🔗 Related Resources

### **External References**
- [Airbnb React Style Guide](https://github.com/airbnb/javascript/tree/master/react)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [Supabase Documentation](https://supabase.com/docs)
- [React Documentation](https://react.dev)
- [TypeScript Handbook](https://www.typescriptlang.org/docs)
- [Conventional Commits](https://www.conventionalcommits.org)

### **Internal Documentation**
- Project README files in each application folder
- Architecture documentation in individual projects
- Database schema documentation in `supabase/` folder

---

## 📝 Updates and Maintenance

### **When to Update These Guidelines**
- Major framework version upgrades
- New tooling or dependency changes
- Lessons learned from production issues
- Team feedback on existing standards
- New project requirements or constraints

### **Who Can Update**
- Project leads and architects
- Senior developers with consensus
- DevOps/Platform teams for infrastructure
- Security team for security-related rules

**Process:**
1. Create a branch for the guideline update
2. Document the change and rationale
3. Get approval from relevant stakeholders
4. Update documentation and tag version
5. Communicate changes to the team

---

## ❓ FAQ

**Q: Can I override these rules for my project?**
A: Project-specific rules (like fairbidder.md) can extend global rules, but **MCP baseline rules cannot be overridden**. Contact your project lead if you need an exception.

**Q: What if there's a conflict between rules?**
A: Priority order is:
1. MCP baseline rules (non-negotiable)
2. Project-specific rules
3. Global rules
4. Personal preferences (not allowed)

**Q: How often are these guidelines updated?**
A: Typically when major framework versions upgrade or significant lessons are learned. Check git history for recent changes.

**Q: Where do I ask questions about these guidelines?**
A: File an issue or discussion in the project repository with the tag `[guidelines]`.

---

## 📧 Contact & Support

For questions or suggestions:
- **General coding questions:** Open an issue with `[guidelines]` tag
- **Fairbidder-specific questions:** Contact the Fairbidder team
- **Security concerns:** Report to the security team
- **Tool configuration:** Contact DevOps/Platform team

---

**Last Updated:** January 13, 2026  
**Version:** 1.0  
**Maintained By:** Fairbidder Development Team
