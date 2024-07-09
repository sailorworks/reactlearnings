# Functional components

Functional components in React are the most basic form of React components. They are JavaScript functions that return React elements (JSX) and are used to define components in a React application. When using Vite as your build tool, it helps create a fast and optimized development environment for React applications.

understand functional components in Vite React:

### Step 1: Understanding Functional Components

A functional component in React is simply a JavaScript function that returns JSX (JavaScript XML).

#### Example 1: Basic Functional Component

Create a file named `HelloWorld.jsx` in the `src` directory:

```jsx
import React from "react";

const HelloWorld = () => {
  return (
    <div>
      <h1>Hello, World!</h1>
    </div>
  );
};

export default HelloWorld;
```

Here, `HelloWorld` is a functional component that returns a `div` containing an `h1` element.

#### Example 2: Functional Component with Props

Props (short for properties) are used to pass data from one component to another.

Create a file named `Greeting.jsx` in the `src` directory:

```jsx
import React from "react";

const Greeting = ({ name }) => {
  return (
    <div>
      <h1>Hello, {name}!</h1>
    </div>
  );
};

export default Greeting;
```

In this example, `Greeting` is a functional component that accepts a `name` prop and displays it.

### Step 3: Using Functional Components in App

To use these components, you need to import and include them in your main `App.jsx` file:

```jsx
import React from "react";
import HelloWorld from "./HelloWorld";
import Greeting from "./Greeting";

const App = () => {
  return (
    <div>
      <HelloWorld />
      <Greeting name="Sahil" />
    </div>
  );
};

export default App;
```

This `App` component imports the `HelloWorld`, `Greeting`, and `Counter` components and includes them in the rendered output.

### Summary

- **Functional Components**: Basic building blocks in React, defined as JavaScript functions that return JSX.
- **Props**: Passed to components to provide dynamic data.
