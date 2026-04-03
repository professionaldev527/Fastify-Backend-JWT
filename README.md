# Fastify Thumbnail Manager API

A blazing fast RESTful API built with **Fastify** and **MongoDB**. This backend service provides secure user authentication and allows users to upload, manage, and delete image thumbnails.

## Features

- **User Authentication**: Secure registration and login using `bcryptjs`.
- **Stateless Sessions**: Route protection via JSON Web Tokens (JWT).
- **Account Recovery**: Generate and verify password reset tokens.
- **File Uploads**: Efficient multipart file streaming to the local filesystem using `@fastify/multipart`.
- **CRUD Operations**: Complete management of thumbnail metadata tied to specific users.
- **Automated Cleanup**: Synchronized deletion of local files when database records are removed.

## Tech Stack

- **Framework**: Fastify
- **Database**: MongoDB (via Mongoose)
- **Authentication**: `@fastify/jwt`

## Getting Started

### Prerequisites

- Node.js installed
- A MongoDB Atlas account or local MongoDB instance

### Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/professionaldev527/Fastify-Backend-JWT
    cd /Fastify-Backend-JWT
    ```

2. Install dependencies:

    ```bash
    npm install
    ```

3. Create a `.env` file in the root directory and add the following variables:

    ```env
    PORT=4000
    MONGODB_URI=mongodb+srv://<username>:<password>@cluster0.mongodb.net/31-fastify
    JWT_SECRET=your_super_secret_key
    ```

4. Start the development server:
    ```bash
    npm run dev
    ```
    The server should now be running at `http://localhost:4000`.

## API Endpoints

### Auth Routes (`/api/auth`)

- `POST /register` - Register a new user
- `POST /login` - Authenticate a user and receive a JWT
- `POST /forgot-password` - Generate a reset token
- `POST /reset-password/:token` - Reset user password
- `POST /logout` - Logout a user (Requires JWT)

### Thumbnail Routes (`/api/thumbnail`) - _Requires JWT_

- `POST /` - Upload a new thumbnail (multipart/form-data)
- `GET /` - Get all thumbnails for the authenticated user
- `GET /:id` - Get a specific thumbnail by ID
- `PUT /:id` - Update thumbnail details
- `DELETE /:id` - Delete a thumbnail and its associated image file
- `DELETE /` - Delete all thumbnails for the authenticated user
