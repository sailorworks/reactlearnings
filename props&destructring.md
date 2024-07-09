# Props and Destructring.

Let's start with a basic understanding of props and destructuring in React and gradually move towards more complex scenarios.

### Basic Example

#### Step 1: Simple Prop Passing

**App Component (App.jsx)**

```jsx
import React from "react";
import Greeting from "./Greeting";

function App() {
  return (
    <div>
      <Greeting name="Sahil" />
    </div>
  );
}

export default App;
```

**Greeting Component (Greeting.jsx)**

Without Destructuring:

```jsx
import React from "react";

function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

export default Greeting;
```

With Destructuring:

```jsx
import React from "react";

function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}

export default Greeting;
```

### Intermediate Example

#### Step 2: Multiple Props with Destructuring

**App Component (App.jsx)**

```jsx
import React from "react";
import UserInfo from "./UserInfo";

function App() {
  return (
    <div>
      <UserInfo name="Sahil" age={21} location="Mumbai" />
    </div>
  );
}

export default App;
```

**UserInfo Component (UserInfo.jsx)**

Without Destructuring:

```jsx
import React from "react";

function UserInfo(props) {
  return (
    <div>
      <h2>Name: {props.name}</h2>
      <p>Age: {props.age}</p>
      <p>Location: {props.location}</p>
    </div>
  );
}

export default UserInfo;
```

With Destructuring:

```jsx
import React from "react";

function UserInfo({ name, age, location }) {
  return (
    <div>
      <h2>Name: {name}</h2>
      <p>Age: {age}</p>
      <p>Location: {location}</p>
    </div>
  );
}

export default UserInfo;
```

### Advanced Example

#### Step 3: Passing Objects as Props and Destructuring Nested Objects

**App Component (App.jsx)**

```jsx
import React from "react";
import UserProfile from "./UserProfile";

const user = {
  name: "Sahil",
  age: 21,
  location: "Mumbai",
  contact: {
    email: "sahil@example.com",
    phone: "123-456-7890",
  },
};

function App() {
  return (
    <div>
      <UserProfile user={user} />
    </div>
  );
}

export default App;
```

**UserProfile Component (UserProfile.jsx)**

Without Destructuring:

```jsx
import React from "react";

function UserProfile(props) {
  return (
    <div>
      <h2>Name: {props.user.name}</h2>
      <p>Age: {props.user.age}</p>
      <p>Location: {props.user.location}</p>
      <p>Email: {props.user.contact.email}</p>
      <p>Phone: {props.user.contact.phone}</p>
    </div>
  );
}

export default UserProfile;
```

With Destructuring:

```jsx
import React from "react";

function UserProfile({ user }) {
  const {
    name,
    age,
    location,
    contact: { email, phone },
  } = user;

  return (
    <div>
      <h2>Name: {name}</h2>
      <p>Age: {age}</p>
      <p>Location: {location}</p>
      <p>Email: {email}</p>
      <p>Phone: {phone}</p>
    </div>
  );
}

export default UserProfile;
```

### Complex Example

#### Step 4: Prop Types and Default Props

To ensure the components receive the correct types of props and to provide default values for props, you can use `prop-types` and `defaultProps`.

**App Component (App.jsx)**

```jsx
import React from "react";
import UserProfile from "./UserProfile";

const user = {
  name: "Sahil",
  age: 21,
  location: "Mumbai",
  contact: {
    email: "sahil@example.com",
    phone: "123-456-7890",
  },
};

function App() {
  return (
    <div>
      <UserProfile user={user} />
    </div>
  );
}

export default App;
```

**UserProfile Component (UserProfile.jsx)**

```jsx
import React from "react";
import PropTypes from "prop-types";

function UserProfile({ user }) {
  const {
    name,
    age,
    location,
    contact: { email, phone },
  } = user;

  return (
    <div>
      <h2>Name: {name}</h2>
      <p>Age: {age}</p>
      <p>Location: {location}</p>
      <p>Email: {email}</p>
      <p>Phone: {phone}</p>
    </div>
  );
}

UserProfile.propTypes = {
  user: PropTypes.shape({
    name: PropTypes.string.isRequired,
    age: PropTypes.number.isRequired,
    location: PropTypes.string.isRequired,
    contact: PropTypes.shape({
      email: PropTypes.string.isRequired,
      phone: PropTypes.string.isRequired,
    }).isRequired,
  }).isRequired,
};

UserProfile.defaultProps = {
  user: {
    name: "Default Name",
    age: 0,
    location: "Default Location",
    contact: {
      email: "default@example.com",
      phone: "000-000-0000",
    },
  },
};

export default UserProfile;
```

### Summary

- **Basic Example:** Passing a single prop and destructuring it.
- **Intermediate Example:** Passing multiple props and destructuring them.
- **Advanced Example:** Passing an object as a prop and destructuring nested objects.
- **Complex Example:** Using `prop-types` for type checking and `defaultProps` for default values.

By gradually increasing the complexity of examples, you can better understand how props and destructuring work in React and how to use them effectively in real-world applications.
