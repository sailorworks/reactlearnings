### React Routing with `react-router-dom`

Routing in React is handled using the `react-router-dom` library. This library allows you to create single-page applications (SPAs) with navigation between different components, all without needing to reload the page.

### Basic Setup

1. **Install `react-router-dom`**

   ```bash
   npm install react-router-dom
   ```

2. **Setup the Router in Your Project**

   Create a basic routing setup using `BrowserRouter` from `react-router-dom`.

### Example 1: Basic Routing

#### Step 1: Create the App Component

**App.jsx**

```jsx
import React from "react";
import { BrowserRouter as Router, Route, Routes, Link } from "react-router-dom";
import Home from "./Home";
import About from "./About";
import Contact from "./Contact";

function App() {
  return (
    <Router>
      <nav>
        <ul>
          <li>
            <Link to="/">Home</Link>
          </li>
          <li>
            <Link to="/about">About</Link>
          </li>
          <li>
            <Link to="/contact">Contact</Link>
          </li>
        </ul>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/contact" element={<Contact />} />
      </Routes>
    </Router>
  );
}

export default App;
```

#### Step 2: Create the Component Files

**Home.jsx**

```jsx
import React from "react";

function Home() {
  return <h1>Home Page</h1>;
}

export default Home;
```

**About.jsx**

```jsx
import React from "react";

function About() {
  return <h1>About Page</h1>;
}

export default About;
```

**Contact.jsx**

```jsx
import React from "react";

function Contact() {
  return <h1>Contact Page</h1>;
}

export default Contact;
```

In this setup:

- `BrowserRouter` wraps the entire application.
- `Routes` contains all the `Route` components, defining the path and corresponding component.
- `Link` components are used for navigation.
