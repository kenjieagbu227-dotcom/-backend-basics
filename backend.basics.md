
🧩 2️⃣ BACKEND DEVELOPMENT BASICS

---

🧠 What is a Server & API?

🔹 Server

A server is a computer or system that stores, processes, and delivers data to clients (like browsers or apps).
Every time you open a website, your browser (client) sends a request to the server, and the server replies with a response (HTML, data, images, etc).

Example:

Client: “Give me the list of users.”

Server: “Here’s your data (JSON).”


🔹 API (Application Programming Interface)

An API allows two applications to communicate.
It defines how software components should interact.

Example of API Request & Response (JSON):

// Request → GET /users
[
  { "id": 1, "name": "Alice" },
  { "id": 2, "name": "Bob" }
]


---

⚙️ Node.js + Express Introduction

🔸 Node.js

Node.js is a JavaScript runtime that lets you run JS code outside the browser — used to build backend servers.

🔸 Express.js

Express is a lightweight framework for Node.js to handle HTTP requests easily.


---

🧱 Example: Simple Express Server

Create a file named server.js:

// Import Express
const express = require('express');
const app = express();
const PORT = 3000;

// Sample route
app.get('/', (req, res) => {
  res.send('Hello, World! Backend is running!');
});

// Start server
app.listen(PORT, () => {
  console.log(`Server running on http://localhost:${PORT}`);
});

How to run:

1. Install Node.js (from https://nodejs.org)


2. Run commands:

npm init -y
npm install express
node server.js



You’ll see:

> Server running on http://localhost:3000




---

🔁 REST API vs GraphQL

Feature	REST API	GraphQL

Data Fetching	Multiple endpoints (/users, /posts)	Single endpoint with flexible queries
Format	JSON	JSON
Pros	Simple, widely used	Efficient, customizable data
Example	GET /users	{ users { id, name } }



---

✍️ CRUD Tutorial with JSON Data

CRUD = Create, Read, Update, Delete

const express = require('express');
const app = express();
app.use(express.json());

let users = [
  { id: 1, name: 'Alice' },
  { id: 2, name: 'Bob' }
];

// Read
app.get('/users', (req, res) => {
  res.json(users);
});

// Create
app.post('/users', (req, res) => {
  const newUser = req.body;
  users.push(newUser);
  res.json({ message: 'User added', data: newUser });
});

// Update
app.put('/users/:id', (req, res) => {
  const id = parseInt(req.params.id);
  const updated = req.body;
  users = users.map(u => (u.id === id ? updated : u));
  res.json({ message: 'User updated' });
});

// Delete
app.delete('/users/:id', (req, res) => {
  const id = parseInt(req.params.id);
  users = users.filter(u => u.id !== id);
  res.json({ message: 'User deleted' });
});

app.listen(3000, () => console.log('API running on http://localhost:3000'));


---

🔒 Basic Authentication (Intro)

You can secure routes using simple tokens or passwords.

Example:

app.post('/login', (req, res) => {
  const { username, password } = req.body;
  if (username === 'admin' && password === '1234') {
    res.json({ message: 'Login successful', token: 'fake-jwt-token' });
  } else {
    res.status(401).json({ message: 'Invalid credentials' });
  }
});


---

🧠 Summary

✅ You learned:

What servers and APIs are

How to set up Node.js + Express

The difference between REST & GraphQL

CRUD operations with JSON data

Basic authentication setup



---

