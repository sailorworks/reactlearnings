# Hooks in react

## useState

- useState is a hook that allows us to manage state in functional components.

Syntax:

```
const [state, setState] = useState(initialState);
```

here it takes values as array. `state` as a value and `setState` as a function.

Example:

```jsx
import React, { useState } from "react";

function Counter() {
  // Declare a state variable named count, initialized to 0
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}

export default Counter;
```

- here `onClick` is an event handler property that is only available in react .
- inside it is the special funtion provided by useState, setCount is responsible for updating state variable count.

#### Intermidiate level example:

```Javascript
import React, { useState } from 'react';

function Toggle() {
  // Declare a state variable named isOn, initialized to false
  const [isOn, setIsOn] = useState(false);

  return (
    <div>
      <p>The button is {isOn ? 'On' : 'Off'}</p>
      <button onClick={() => setIsOn(!isOn)}>
        {isOn ? 'Turn Off' : 'Turn On'}
      </button>
    </div>
  );
}

export default Toggle;
```

Here it can be confusing just because there are two statements that change in opposite manner. If you identify you'll understand it quickly.

##### Managing multiple state variables:

Example:

```jsx
import React, { useState } from "react";

function ContactForm() {
  const [name, setName] = useState("");
  const [email, setEmail] = useState("");

  const handleSubmit = (event) => {
    event.preventDefault(); // Prevent default form submission

    console.log("Form submitted:", { name, email });
  };

  return (
    <form onSubmit={handleSubmit}>
      <div>
        <label htmlFor="name">Name:</label>
        <input
          type="text"
          id="name"
          value={name}
          onChange={(e) => setName(e.target.value)}
        />
      </div>
      <div>
        <label htmlFor="email">Email:</label>
        <input
          type="email"
          id="email"
          value={email}
          onChange={(e) => setEmail(e.target.value)}
        />
      </div>
      <button type="submit">Submit</button>
    </form>
  );
}

export default ContactForm;
```

`e.target.value` is a key part of handling form inputs in React. Let's break it down:

- **`e` (or `event`)**: This represents the event object that's automatically passed to your event handler function (like `onChange` in this case). The event object contains information about what triggered the event.

- **`target`**: Within the event object, `e.target` refers specifically to the HTML element that triggered the event. In the context of your form, `e.target` would be the `<input>` element itself when you're typing in it.

- **`value`**: This property of the `target` element holds the current value entered by the user in the input field.

**Putting it all together:**

`e.target.value` allows you to access the current text content of your input field whenever the user types something or changes its value.

**Example:**

Let's imagine someone types "hello" into the "Name" field of your form:

1. The `onChange` event is triggered on the input field.
2. The event handler function (`(e) => setName(e.target.value)`) is called.
3. `e.target` points to the `<input id="name">` element.
4. `e.target.value` would be "hello" (the current text in the input).
5. `setName(e.target.value)` updates the `name` state variable to "hello".

**In essence:** `e.target.value` acts as the bridge between what the user enters in the input field and your React component's state, allowing you to keep your state synchronized with the form input.

- for more go through videos by piyush garg videos or web dev simplified hooks
