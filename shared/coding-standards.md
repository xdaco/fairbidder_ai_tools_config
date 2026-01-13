# React Coding Standard

> This style guide is a fork of Airbnb's React style guide, adapted for Dynatrace Apps. It aims to improve maintainability, scalability, and developer efficiency.

---

## 1. **Basic Rules**

* Only **one React component per file**. Multiple stateless or pure components are allowed.
* Always use **JSX syntax**.
* Prefer **functional components** over class components.
* Use **TypeScript** (`.tsx`) wherever possible. At minimum, use `prop-types` and `defaultProps`.
* Write clean, maintainable, and reusable code. Avoid overusing ternaries, switch statements, or deeply nested conditional rendering.
* Ensure every component has a clear single responsibility.

---

## 2. **Naming Conventions**

### **Files and Extensions**

* React components: `.tsx`
* Tests: `.test.tsx`
* Stories: `.stories.tsx`
* Markdown: `SNAKE_CASE` (`README.md`)

### **Components**

* Component filenames: `PascalCase` (e.g., `ReservationCard.tsx`)
* Component references/instances: `camelCase`
* Hooks: `camelCase` (e.g., `useWindowSize`)

**Example:**

```tsx
// Component
import FooBar from './FooBar';

// Instance
const fooBar = <FooBar />;
```

### **Props**

* Use `camelCase` for prop names.
* Use `PascalCase` only if the prop is a React component.
* Avoid using HTML attribute names for custom props (`style`, `className`).

**Example:**

```tsx
// Bad
<Foo style="fancy" className="fancy" />
<Foo UserName="hello" phone_number={12345678} />

// Good
<Foo variant="fancy" />
<Foo userName="hello" phoneNumber={12345678} Component={SomeComponent} />
```

---

## 3. **Quotes**

* JSX attributes: **double quotes** (`"`)
* JS strings: **single quotes** (`'`)

**Example:**

```tsx
// Bad
<Foo bar='bar' />
<Foo style={{ left: "20px" }} />

// Good
<Foo bar="bar" />
<Foo style={{ left: '20px' }} />
```

---

## 4. **Props & State**

* Omit boolean prop values when true:

```tsx
<Foo hidden /> // Good
<Foo hidden={true} /> // Bad
```

* Avoid array index as `key`. Use a stable ID.

```tsx
todos.map(todo => <Todo {...todo} key={todo.id} />)
```

* Use **spread props** sparingly. Always filter unnecessary props:

```tsx
const { ignoredProp, ...barProps } = props;
return <Bar {...barProps} />;
```

---

## 5. **JSX & Components**

* Wrap multiline JSX in parentheses:

```tsx
return (
  <Bar>
    <Baz />
  </Bar>
);
```

* Self-close tags with no children:

```tsx
<Foo variant="stuff" />
```

* Close multiline prop tags on a new line:

```tsx
<Foo
  bar="bar"
  baz="baz"
/>
```

* Use **fragments** instead of unnecessary divs:

```tsx
<>
  <h1>Title</h1>
  <p>Text</p>
</>
```

* Extract reusable logic into **custom hooks**. Avoid duplicating stateful logic.
* Prefer `useReducer` over multiple `useState` hooks for complex state.

---

## 6. **Folder Structure**

* Use **kebab-case** for folders and files except components:

```
components/
  ReservationCard/
    ReservationCard.tsx
    ReservationCard.test.tsx
    index.ts
contexts/
hooks/
providers/
types/
util/
```

---

## 7. **Accessibility**

* All `<img>` tags must have `alt`. If decorative, `alt=""` or `role="presentation"`.

```tsx
<img src="hello.jpg" alt="Me waving hello" />
<img src="hello.jpg" alt="" role="presentation" />
```

* Avoid redundant alt descriptions ("image", "photo", "picture").
* Use only valid ARIA roles.
* Do not use `accessKey`.

---

## 8. **Error Handling**

* Use **Error Boundaries** for render errors.
* Handle async errors with `try-catch`. Log errors to a service (e.g., Sentry).
* Example with `react-error-boundary`:

```tsx
<ErrorBoundary FallbackComponent={ErrorComponent} onError={logError}>
  <MyErrorProneComponent />
</ErrorBoundary>
```

---

## 9. **Performance & Best Practices**

* Implement **lazy loading / code splitting**.
* Sanitize HTML to prevent XSS attacks (`dompurify`).
* Always keep `key` prop unique across components.
* Avoid inline styles and deeply nested JSX.
* Follow proper import order:

  1. Built-in modules (React)
  2. External modules (third-party)
  3. Internal modules (components, utils, constants)

---

## 10. **Testing**

* Always write unit tests for critical functionality.
* Treat tests as **documentation**.
* Use `jest` and `react-testing-library` or equivalent.

---

## 11. **Linting & Formatting**

* Use **ESLint** + Prettier.
* Enforce:

  * PascalCase for components
  * camelCase for instances & hooks
  * JSX double quotes
  * Self-closing tags

---

## 12. **Additional Tips**

* Boolean props can be passed as shorthand (`<Foo hasPadding />`).
* Avoid curly braces for string props (`<Paragraph heading="Title" />`).
* Remove non-HTML attributes before spreading props.
* Use snippet extensions in VS Code for boilerplate efficiency.
* Follow solid React foundations: Hooks, Virtual DOM, CSR/SSR, Controlled Components, State Lifting, Context API/Redux.
