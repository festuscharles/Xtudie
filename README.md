# Xtudie
Xtudie is an educational web application, with the backend developed with Node.js, and MongoDB is for  the database. 

# Xtudie Backend Documentation

## Introduction

Xtudie is an educational web application designed to provide students with a platform to access various educational resources. This documentation aims to explain the backend architecture and implementation details of Xtudie. The backend is developed using Node.js, and MongoDB is used as the database.

## Architecture Overview

The backend architecture of Xtudie follows a client-server model. The server is responsible for handling client requests, processing data, and communicating with the MongoDB database. The server-side logic is implemented using Node.js, and it provides a RESTful API for the frontend to interact with.

## Technologies Used

- Node.js: A JavaScript runtime environment for executing server-side code.
- Express.js: A popular web application framework for Node.js, used to build the RESTful API.
- MongoDB: A NoSQL database used to store and retrieve data for Xtudie.
- Mongoose: An Object-Document Mapping (ODM) library for Node.js that provides a schema-based solution for interacting with MongoDB.
- JSON Web Tokens (JWT): Used for user authentication and authorization.
- bcrypt: A library used for password hashing and verification.

## Installation and Setup

1. Install Node.js and MongoDB on your server.
2. Clone the Xtudie backend repository from the Git repository.
3. Run `npm install` to install the required dependencies.
4. Create a `.env` file in the project root directory and configure the following environment variables:

```
PORT=3000
MONGODB_URI=mongodb://localhost:27017/xtudie
JWT_SECRET=your_jwt_secret_key
```

5. Start the server using `npm start`.

## API Endpoints

### Authentication

- `POST /api/auth/register`: Register a new user.
- `POST /api/auth/login`: Log in an existing user.

### Note Hub

- `GET /api/notes`: Get all notes.
- `GET /api/notes/:id`: Get a specific note by ID.
- `POST /api/notes`: Create a new note.
- `PUT /api/notes/:id`: Update an existing note by ID.
- `DELETE /api/notes/:id`: Delete a note by ID.

### Educational Blog

- `GET /api/blogs`: Get all blog posts.
- `GET /api/blogs/:id`: Get a specific blog post by ID.
- `POST /api/blogs`: Create a new blog post.
- `PUT /api/blogs/:id`: Update an existing blog post by ID.
- `DELETE /api/blogs/:id`: Delete a blog post by ID.

### Lecture Summary

- `GET /api/lectures`: Get all lecture summaries.
- `GET /api/lectures/:id`: Get a specific lecture summary by ID.
- `POST /api/lectures`: Create a new lecture summary.
- `PUT /api/lectures/:id`: Update an existing lecture summary by ID.
- `DELETE /api/lectures/:id`: Delete a lecture summary by ID.

## Authentication and Authorization

Xtudie uses JSON Web Tokens (JWT) for user authentication and authorization. Upon successful registration or login, a JWT is generated and sent to the client, which includes the user's information and a secret key for verification.

To access protected routes, the client must include the JWT in the `Authorization` header of the request. The server verifies the JWT and allows or denies access accordingly.

## Database Schema

### User Schema

```javascript
{
  username: { type: String, required: true, unique: true },
  email: { type: String, required: true, unique: true },
  password: { type: String, required: true }


}
```

### Note Schema

```javascript
{
  title: { type: String, required: true },
  content: { type: String, required: true },
  author: { type: mongoose.Schema.Types.ObjectId, ref: 'User', required: true }
}
```

### Blog Schema

```javascript
{
  title: { type: String, required: true },
  content: { type: String, required: true },
  author: { type: mongoose.Schema.Types.ObjectId, ref: 'User', required: true },
  createdAt: { type: Date, default: Date.now }
}
```

### Lecture Summary Schema

```javascript
{
  title: { type: String, required: true },
  summary: { type: String, required: true },
  author: { type: mongoose.Schema.Types.ObjectId, ref: 'User', required: true },
  createdAt: { type: Date, default: Date.now }
}
```

## Error Handling

The backend provides consistent error responses in JSON format. If an error occurs during processing, the server returns an appropriate status code and an error message in the response body.

Example error response:

```json
{
  "error": "Invalid credentials"
}
```

## Conclusion

This documentation provides an overview of the Xtudie backend architecture, API endpoints, authentication and authorization, database schema, and error handling. It serves as a guide for developers working on the Xtudie backend or integrating it with other systems.
