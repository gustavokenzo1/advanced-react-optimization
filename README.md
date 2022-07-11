# Advanced React Optimization

Mini project to practice good practices to make React apps faster, not focusing on CSS. Built using Next.js and a Fake API.

### How React Re-Rendering Works

1. Create a new version of the component.
2. Compare the new version to the old version.
3. If there are differences, update what's needed.

### How React Optimization Works

Most Hooks shouldn't be used prematurely, as it can be slower for small components. Always test on React Dev Tools Profiler:

- memo: used in ProductItem.tsx to avoid re-rendering the component when the props are the same, which makes it much faster on large amounts of components.

- useMemo: used at first to calculate totalPrice, then changed it to when the API is called. Used to avoid re-rendering a component caused by a return value of a function with heavy calculations and/or when the return value of the function is passed to a child component.

- useCallback: similar to useMemo, but used to memoize a function instead of a value. Suppose we have a function on a parent component. Every time the parent component is rendered, the function is re-created. If this function is passed to a child component, it will also re-render, because React uses Referential Equality.

- lazy/dynamic: When bundling, all the code will be minified into one file. This isn't always good, because we can have an import that is only used by an user's action. If the user never uses what's imported, than we would have an unecessarily large file. React.lazy makes the imports dynamic, so they are only imported when they are used. For SSR, Next.js uses dynamic from 'next/dynamic'.

- Virtualization: If we have a large component, with say 1000 items, we can use virtualization to render only a part of those items, like 20 items at a time, with an offset of 5 items, so when the user scrolls, we can keep rendering the previous/next items.

# How to Run

Frontend:

```bash
npm install
```

```bash
npm run dev
```

Fake API:

```bash
npm run server
```
