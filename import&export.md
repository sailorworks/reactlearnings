# Import and Export

### Example 1: Default Export and Import

#### ComponentA.js

```javascript
import React from "react";

export default function ComponentA() {
  return <h1>This is ComponentA</h1>;
}
```

#### App.js

```javascript
import React from "react";
import ComponentA from "./ComponentA";

function App() {
  return (
    <div>
      <ComponentA />
    </div>
  );
}

export default App;
```

### Example 2: Named Export and Import

#### ComponentB.js

```javascript
import React from "react";

export function ComponentB() {
  return <h1>This is ComponentB</h1>;
}
```

#### App.js

```javascript
import React from "react";
import { ComponentB } from "./ComponentB";

function App() {
  return (
    <div>
      <ComponentB />
    </div>
  );
}

export default App;
```

### Example 3: Multiple Named Exports and Import

#### Utils.js

```javascript
export function add(a, b) {
  return a + b;
}

export function subtract(a, b) {
  return a - b;
}
```

#### App.js

```javascript
import React from "react";
import { add, subtract } from "./Utils";

function App() {
  return (
    <div>
      <h1>Add: {add(5, 3)}</h1>
      <h1>Subtract: {subtract(5, 3)}</h1>
    </div>
  );
}

export default App;
```

### Example 4: Importing All Named Exports as an Object

#### Utils.js

```javascript
export function add(a, b) {
  return a + b;
}

export function subtract(a, b) {
  return a - b;
}
```

#### App.js

```javascript
import React from "react";
import * as Utils from "./Utils";

function App() {
  return (
    <div>
      <h1>Add: {Utils.add(5, 3)}</h1>
      <h1>Subtract: {Utils.subtract(5, 3)}</h1>
    </div>
  );
}

export default App;
```

### Example 5: Combining Default and Named Exports

#### ComponentC.js

```javascript
import React from "react";

export default function ComponentC() {
  return <h1>This is the default export, ComponentC</h1>;
}

export function Helper() {
  return <p>This is a named export, Helper</p>;
}
```

#### App.js

```javascript
import React from "react";
import ComponentC, { Helper } from "./ComponentC";

function App() {
  return (
    <div>
      <ComponentC />
      <Helper />
    </div>
  );
}

export default App;
```

Certainly! Using the `import { X as Y }` syntax allows you to import a named export and give it a different name locally. This can be useful to avoid naming conflicts or to make the imported name more descriptive in the context of your file. Here are some examples:

### Example 1: Renaming a Single Named Export

#### Utils.js

```javascript
export function add(a, b) {
  return a + b;
}

export function subtract(a, b) {
  return a - b;
}
```

#### App.js

```javascript
import React from "react";
import { add as sum, subtract as difference } from "./Utils";

function App() {
  return (
    <div>
      <h1>Sum: {sum(5, 3)}</h1>
      <h1>Difference: {difference(5, 3)}</h1>
    </div>
  );
}

export default App;
```

Anyname:

when you export a module using `export default`, you can import it with any name in React (or JavaScript in general). This is because the default export is considered the "main" export of the module, and the importing module can choose any name for it.

### ModuleA.js

```javascript
// Exporting a default function
export default function ModuleA() {
  console.log("This is ModuleA");
}
```

### App.js

```javascript
// Importing the default export from ModuleA.js
import AnyName from "./ModuleA";

AnyName(); // This will log "This is ModuleA"
```

In the above example, `ModuleA` was exported as a default export. When importing it in `App.js`, we used `AnyName` as the import name, and it works perfectly fine.

This flexibility is unique to default exports. Named exports, on the other hand, must be imported with their exact exported names.
These examples should give you a good understanding of different ways to use `import` and `export` in React.

This document looks long but it is easy and filled with cool examples.
