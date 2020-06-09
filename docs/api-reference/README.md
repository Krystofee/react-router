<a name="top"></a>

# React Router API Reference

This is the comprehensive API reference for React Router.

The components, hooks, and utilities in this reference fall into a few major categories, grouped by purpose:

```ts
```

- Setup
  - `<BrowserRouter>`, `<HashRouter>`, and `<NativeRouter>`
  - `<MemoryRouter>`
  - `<StaticRouter>` (for server rendering)
- Routing
  - `<Routes>` and `<Route>`
  - `useRoutes`
- Navigation
  - `<Link>`
  - `useNavigate`
  - `<Navigate>`

<a name="overview"></a>

## Overview

React Router adds "routing" capabilities to React. But what is routing, anyway?

There are 2 main ideas behind what a "route" is in React Router:

**First, a route determines what will be rendered at a given location.** When the location changes, a route will try to *match* the current location. If it matches, it renders its `element`. Otherwise, it doesn't render anything.

**Secondly, routes are arranged in a nested hierarchy**, which reflects the way the user interface is designed. You can logically break down most user interfaces into boxes nested inside other boxes. For example, on many websites the main header and navigation are always visible, while the "content" area changes depending on which "page" is selected. In React Router, we could model this scenario with 2 **nested** routes: one route for the inner content which would be nested inside another route for the main nav.

React Router provides several primitives that let you declare the routes available in your app and how they are nested. This combination gives you complete control over exactly what is rendered to the page when the location changes, as well as a flexible and efficient mechanism for doing layouts.

<a name="setup"></a>

## Setup

React Router runs anywhere React does, including in web browsers, on the server using node, and even on React Native. To do this, React Router comes with several different "router" components, each for a different environment. You should be able to re-use the same route config in any environment.

**Web browsers**: In web browsers, you should wra

<a name="routing"></a>

## Routing



<a name="routes"></a>

## `<Routes>` and `<Route>`

A `<Routes>` element is a container for a set of nested [`<Route>` elements](#route). It is the declarative equivalent to [the `useRoutes` hook](#useroutes).