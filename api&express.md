## Example program:

Here we are handling hardcoded json format api using expressjs.

Here we can learn about http methods and how to use them with rules specified by restful api.

### getting all users

```Javascript
// Import the express module
const express = require("express");
const users = require("./MOCK_DATA.json");

// Create an instance of an Express application
const app = express();

// Define a route for the root URL
app.get("/users", (req, res) => {
    return res.json(users);
});

// Start the server on port 3000
const port = 3000;
app.listen(port, () => {
    console.log(`Server is running on http://localhost:${port}`);
});
```

- I've created a file MOCK_DATA.json and inside it there is json data.

### Dynamic id accessing

```Javascript
// Import the express module
const express = require("express");
const users = require("./MOCK_DATA.json");

// Create an instance of an Express application
const app = express();

// Define a route for the root URL
app.get("/users", (req, res) => {
    return res.json(users);
});
app.get("/users/:id", (req, res) => {
    const id = Number(req.params.id);
    const user = users.find((user) => user.id === id);
    return res.json(user)
});

// Start the server on port 3000
const port = 3000;
app.listen(port, () => {
    console.log(`Server is running on http://localhost:${port}`);
});
```

- The :id is a variable that can be dynamically be set on the browser.
- Here the req.params.id brings the id parameter from the browser to the const id and then checks for that particular id in the api and returns it.

### with post and efficient coding:

```Javascript
// Import the express module
const express = require("express");
const users = require("./MOCK_DATA.json");

// Create an instance of an Express application
const app = express();


// Define a route for the root URL
app.route("/users/:id")
    .get((req, res) => {
        const id = Number(req.params.id);
        const user = users.find((user) => user.id === id);
        return res.json(user);
    })
    .patch((req, res) => {
        return res.json({ status: "Pending" });
    })
    .delete((req, res) => {
        return res.json({ status: "Pending" });
    });

app.post("/api/users", (req, res) => {
    return res.json({ status: "Pending" });
})
// Start the server on port 3000
const port = 3000;
app.listen(port, () => {
    console.log(`Server is running on http://localhost:${port}`);
});
```

### using postman to post data into json file

```Javascript
// Import the express module
const express = require("express");
const fs = require("fs")
const users = require("./MOCK_DATA.json");

// Create an instance of an Express application
const app = express();

//middleware-plugin
app.use(express.urlencoded({ extended: false }))

app.get("/users", (req, res) => {
    return res.json(users);
})
// Define a route for the root URL
app.route("/users/:id")
    .get((req, res) => {
        const id = Number(req.params.id);
        const user = users.find((user) => user.id === id);
        return res.json(user);
    })
    .patch((req, res) => {
        return res.json({ status: "Pending" });
    })
    .delete((req, res) => {
        return res.json({ status: "Pending" });
    });

app.post("/users", (req, res) => {
    const body = req.body
    users.push({ ...body, id: users.length + 1 })
    fs.writeFile("./MOCK_DATA.json", JSON.stringify(users), (err, data) => {
        return res.json({ status: "success", id: users.length + 1 });
    })
})
// Start the server on port 3000
const port = 3000;
app.listen(port, () => {
    console.log(`Server is running on http://localhost:${port}`);
});
```
