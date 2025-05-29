# Full-Stack Connect Four Game (React + Node.js + MongoDB)

This is a full-stack web application for the game **Connect Four**, featuring:
- User authentication (username and password)
- Game UI built with **React**
- Backend API built with **Node.js + Express**
- Data persistence using **MongoDB**

## Tech Stack

| Layer      | Technology                |
|------------|---------------------------|
| Frontend   | React, Tailwind CSS       |
| Backend    | Node.js, Express.js       |
| Database   | MongoDB, Mongoose         |
| Auth       | bcrypt (hashing), JWT     |
| Hosting    | Vercel (frontend), Render/MongoDB Atlas (backend+DB) |


## Features
- Register new users with hashed passwords
- Login with JWT-based authentication
- Connect Four game logic and UI
- Only authenticated users can play
- Game state stored per user session


## Project Structure

```
connect-four-app/
├── client/               # React frontend
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   └── App.jsx
├── server/               # Express backend
│   ├── models/
│   ├── routes/
│   ├── controllers/
│   └── server.js
└── README.md
```


## Setup Instructions

### 1. Backend Setup

```bash
cd server
npm install
# Create .env file with:
# MONGO_URI=<Your MongoDB connection string>
# JWT_SECRET=yourSecretKey
npm start
```

### 2. Frontend Setup

```bash
cd client
npm install
npm start
```


## Key Backend Code Snippets

### User Schema (`models/User.js`)

```js
const mongoose = require("mongoose");

const UserSchema = new mongoose.Schema({
  username: { type: String, required: true, unique: true },
  password: { type: String, required: true },
});

module.exports = mongoose.model("User", UserSchema);
```

### Auth Routes (`routes/auth.js`)

```js
const express = require("express");
const bcrypt = require("bcryptjs");
const jwt = require("jsonwebtoken");
const User = require("../models/User");

const router = express.Router();

router.post("/register", async (req, res) => {
  const { username, password } = req.body;
  const hashed = await bcrypt.hash(password, 10);
  const user = new User({ username, password: hashed });
  await user.save();
  res.status(201).send("User created");
});

router.post("/login", async (req, res) => {
  const { username, password } = req.body;
  const user = await User.findOne({ username });
  if (!user || !(await bcrypt.compare(password, user.password))) {
    return res.status(401).send("Invalid credentials");
  }
  const token = jwt.sign({ id: user._id }, process.env.JWT_SECRET);
  res.json({ token });
});

module.exports = router;
```


## TODOs

- [ ] Connect frontend login/register forms
- [ ] Implement game board logic in React
- [ ] Sync gameplay and score with backend
- [ ] Save history of games per user


## Summary

This full-stack app demonstrates how to combine React, Node.js, and MongoDB to create an interactive, user-authenticated web game. It emphasizes secure user management and scalable architecture.

