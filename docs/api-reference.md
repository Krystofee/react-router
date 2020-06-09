<a name="top"></a>

# React Router API Reference

React Router is a collection of [React components](https://reactjs.org/docs/components-and-props.html) and [hooks](#https://reactjs.org/docs/hooks-intro.html) that make it easy to build multi-page applications with [React](https://reactjs.org). If you [installed](./installation) React Router as a global (using a `<script>` tag), you can find the library on the `window.ReactRouterDOM` object. If you installed it from npm, you can simply `import` the pieces you need.

<a name="overview"></a>

## Overview

The various components, hooks, and methods in the React Router API fall into a few major categories, grouped by purpose.

<a name="setup"></a>

### Setup

To get React Router working in your app, you need to render a `<Router>` element at or near the root of your element tree. We provide several different routers, depending on where you're running your app.

- [`<BrowserRouter>`](#browserrouter) or [`<HashRouter>`](#hashrouter) should be used when running in a web browser. Which one you pick depends on the style of URL you prefer or need.
- [`<StaticRouter>`](#staticrouter) should be used when server-rendering a website
- [`<NativeRouter>`](#nativerouter) should be used in [React Native](https://reactnative.dev/) apps
- [`<MemoryRouter>`](#memoryrouter) is useful in testing scenarios and as a reference implementation for the other routers

These routers provide the context that React Router needs to operate in a particular environment. Each one renders [a `<Router>`](#router) internally, which you may also do if you need more fine-grained control for some reason. But it is highly likely that one of the built-in routers is what you need.

<a name="routing"></a>

### Routing

The process of "routing" is simply deciding which React elements will be rendered on a given page of your app, and how they will be nested. React Router provides two interfaces for declaring your routes.

- [`<Routes>` and `<Route>`](#routes-and-route) if you're using JSX
- [`useRoutes`](#useroutes) if you'd prefer a JavaScript object-based config

<a name="navigation"></a>

### Navigation

React Router's navigation interfaces let you change the currently rendered page by modifying the current location. There are two main interfaces for navigating between pages in your app, depending on what you need.

- [`<Link>` and `<NavLink>`](#link-and-navlink) render an accessible `<a>` element, or a `TouchableHighlight` on React Native. This lets the user initiate navigation by clicking or tapping an element on the page.
- [`useNavigate` and `<Navigate>`](#usenavigate-and-navigate) let you programmatically navigate, usually in response to some change in state

<a name="confirming-navigation"></a>

### Confirming Navigation

Sometimes you need to confirm navigation before it actually happens. For example, if the user has entered some data into a form on the current page, you may want to prompt them to save the data before they navigate to a different page.

- [`usePrompt` and `<Prompt>`](#useprompt-and-prompt) trigger a platform-native confirmation prompt when the user tries to navigate away from the current page
- [`useBlocker`](#useblocker) is a low-level interface that lets you keep the user on the same page and execute a function that will be called when they try to navigate away

<a name="search-parameters"></a>

### Search Parameters

Access to the URL [search parameters](https://developer.mozilla.org/en-US/docs/Web/API/URL/searchParams) is provided via [the `useSearchParams` hook](#usesearchparams).

----------

<a name="component-reference"></a>

## Component Reference

This is an alphabetical list of all the components that are part of React Router.

> [!Note:]
>
> You should only ever `import` from one React Router package. If you're making
> a web app, you should import everything from `react-router-dom`. Otherwise, if
> you're making a React Native app, import from `react-router-native`.

<a name="browserrouter"></a>

### `<BrowserRouter>`

`<BrowserRouter>` is the recommended interface for running React Router in a web browser. A `<BrowserRouter>` stores the current location in the browser's address bar using clean URLs and navigates using the browser's built-in history stack.

```tsx
import React from 'react';
import ReactDOM from 'react-dom';
import { BrowserRouter } from 'react-router-dom';

ReactDOM.render(
  <BrowserRouter>
    {/* The rest of your app goes here */}
  </BrowserRouter>,
  root
);
```

<a name="hashrouter"></a>

### `<HashRouter>`

`<HashRouter>` is for use in web browsers when the URL should not (or cannot) be sent to the server for some reason. This may happen in some shared hosting scenarios where you do not have full control over the server. In these situations, `<HashRouter>` makes it possible to store the current location in the `hash` portion of the current URL, so it is never sent to the server.

```tsx
import React from 'react';
import ReactDOM from 'react-dom';
import { HashRouter } from 'react-router-dom';

ReactDOM.render(
  <HashRouter>
    {/* The rest of your app goes here */}
  </HashRouter>,
  root
);
```

<a name="nativerouter"></a>

### `<NativeRouter>`

`<NativeRouter>` is the recommended interface for running React Router in a [React Native](https://reactnative.dev) app.

```tsx
import React from 'react';
import { NativeRouter } from 'react-router-native';

function App() {
  return (
    <NativeRouter>
      {/* The rest of your app goes here */}
    </NativeRouter>
  );
}
```

###########################

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
