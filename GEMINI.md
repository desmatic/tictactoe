### 1. Technical Stack & Environment Requirements

*   **Framework:** Next.js (Latest Stable Version).
*   **Router:** **Next.js App Router** (using the `app/` directory structure).
*   **Language:** **JavaScript (Vanilla JS)**.
    *   **Constraint:** TypeScript must not be used.
*   **Module System: ES Modules (ESM) — CRITICAL**
    *   The project **must exclusively** use ES Modules (ESM) syntax (`import ... from '...'` and `export default ...`).
    *   **ABSOLUTELY NO CommonJS (CJS) Syntax.** Avoid `require()`, `module.exports =`, or `exports.handler =`.
*   **Styling:** Tailwind CSS (configured via PostCSS).
*   **Hosting:** Optimized for deployment on Vercel.
*   **Database/Authentication:** Not required for this initial boilerplate.

### 2. Code Principles Enforcement

*   **ESM Usage:** Verify that no file uses CommonJS syntax.
*   **Client Boundary:** Correctly use the `'use client'` directive only where necessary (i.e., components using hooks/state).
*   **Composition:** Ensure components are composed efficiently.

### 3. Tailwind CSS Configuration

*   **Use single tailwind directive:** Use @import "tailwindcss" in global.css file.
*   **DO NOT USE INDIVIDUAL TAILWIND DIRECTIVES:** Do not use any of the individual @tailwind directives "base", "components", or "utilities".
*   **Configure PostCSS to use Tailwind:** Use "@tailwindcss/postcss" in postcss.config.mjs file.

### 4. Embrace JavaScript's Array Operators

To further enhance code cleanliness and promote safe functional programming practices, leverage JavaScript's rich set of array operators as much as possible. Methods like `.map()`, `.filter()`, `.reduce()`, `.slice()`, `.sort()`, and others are incredibly powerful for transforming and manipulating data collections in an immutable and declarative way.

*   **Promote Immutability:** Most array operators return new arrays, leaving the original array untouched. This functional approach helps prevent unintended side effects and makes your code more predictable.
*   **Improve Readability:** Chaining array operators often lead to more concise and expressive code than traditional for loops or imperative logic. The intent of the operation is clear at a glance.
*   **Facilitate Functional Programming:** These operators are cornerstones of functional programming, encouraging the creation of pure functions that take inputs and produce outputs without causing side effects. This paradigm is highly beneficial for writing robust and testable code that pairs well with React.


### 6. Follow React best practices
*   **Use functional components with Hooks:** Do not generate class components or use old lifecycle methods. Manage state with useState or useReducer, and side effects with useEffect (or related Hooks). Always prefer functions and Hooks for any new component logic.

*   **Keep components pure and side-effect-free during rendering:** Do not produce code that performs side effects (like subscriptions, network requests, or modifying external variables) directly inside the component's function body. Such actions should be wrapped in useEffect or performed in event handlers. Ensure your render logic is a pure function of props and state.

*   **Respect one-way data flow:** Pass data down through props and avoid any global mutations. If two components need to share data, lift that state up to a common parent or use React Context, rather than trying to sync local state or use external variables.

*   **Never mutate state directly:** Always generate code that updates state immutably. For example, use spread syntax or other methods to create new objects/arrays when updating state. Do not use assignments like state.someValue = ... or array mutations like array.push() on state variables. Use the state setter (setState from useState, etc.) to update state.

*   **Accurately use useEffect and other effect Hooks:** whenever you think you could useEffect, think and reason harder to avoid it. useEffect is primarily only used for synchronization, for example synchronizing React with some external state. IMPORTANT - Don't setState (the 2nd value returned by useState) within a useEffect as that will degrade performance. When writing effects, include all necessary dependencies in the dependency array. Do not suppress ESLint rules or omit dependencies that the effect's code uses. Structure the effect callbacks to handle changing values properly (e.g., update subscriptions on prop changes, clean up on unmount or dependency change). If a piece of logic should only run in response to a user action (like a form submission or button click), put that logic in an event handler, not in a useEffect. Where possible, useEffects should return a cleanup function.

*   **Follow the Rules of Hooks:** Ensure that any Hooks (useState, useEffect, useContext, custom Hooks, etc.) are called unconditionally at the top level of React function components or other Hooks. Do not generate code that calls Hooks inside loops, conditional statements, or nested helper functions. Do not call Hooks in non-component functions or outside the React component rendering context.

*   **Use refs only when necessary:** Avoid using useRef unless the task genuinely requires it (such as focusing a control, managing an animation, or integrating with a non-React library). Do not use refs to store application state that should be reactive. If you do use refs, never write to or read from ref.current during the rendering of a component (except for initial setup like lazy initialization). Any ref usage should not affect the rendered output directly.

*   **Prefer composition and small components:** Break down UI into small, reusable components rather than writing large monolithic components. The code you generate should promote clarity and reusability by composing components together. Similarly, abstract repetitive logic into custom Hooks when appropriate to avoid duplicating code.

*   **Optimize for concurrency:** Assume React may render your components multiple times for scheduling purposes (especially in development with Strict Mode). Write code that remains correct even if the component function runs more than once. For instance, avoid side effects in the component body and use functional state updates (e.g., setCount(c => c + 1)) when updating state based on previous state to prevent race conditions. Always include cleanup functions in effects that subscribe to external resources. Don't write useEffects for "do this when this changes" side-effects. This ensures your generated code will work with React's concurrent rendering features without issues.

*   **Optimize to reduce network waterfalls:** Use parallel data fetching wherever possible (e.g., start multiple requests at once rather than one after another). Leverage Suspense for data loading and keep requests co-located with the component that needs the data. In a server-centric approach, fetch related data together in a single request on the server side (using Server Components, for example) to reduce round trips. Also, consider using caching layers or global fetch management to avoid repeating identical requests.

*   **Rely on React Compiler:** useMemo, useCallback, and React.memo can be omitted if React Compiler is enabled. Avoid premature optimization with manual memoization. Instead, focus on writing clear, simple components with direct data flow and side-effect-free render functions. Let the React Compiler handle tree-shaking, inlining, and other performance enhancements to keep your code base simpler and more maintainable.

*   **Design for a good user experience:** Provide clear, minimal, and non-blocking UI states. When data is loading, show lightweight placeholders (e.g., skeleton screens) rather than intrusive spinners everywhere. Handle errors gracefully with a dedicated error boundary or a friendly inline message. Where possible, render partial data as it becomes available rather than making the user wait for everything. Suspense allows you to declare the loading states in your component tree in a natural way, preventing “flash” states and improving perceived performance.

*   **Server Components:** Shift data-heavy logic to the server whenever possible. Break up the more static parts of the app into server components. Break up data fetching into server components. Only client components (denoted by the 'use client' top level directive) need interactivity. By rendering parts of your UI on the server, you reduce the client-side JavaScript needed and avoid sending unnecessary data over the wire. Use Server Components to prefetch and pre-render data, allowing faster initial loads and smaller bundle sizes. This also helps manage or eliminate certain waterfalls by resolving data on the server before streaming the HTML (and partial React tree) to the client.
