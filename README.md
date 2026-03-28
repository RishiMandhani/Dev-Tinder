# DevTinder Backend

## Overview
DevTinder is a backend application designed to help developers connect and collaborate, similar to Tinder but specifically for developers. Users can create profiles, explore other developers, send connection requests, and manage their matches.

This repository contains the backend of DevTinder, built with Node.js, Express, and MongoDB, following a microservices architecture for scalability.

---

## Tech Stack
- Backend Framework: [Node.js](https://nodejs.org/en) + [Express.js](https://expressjs.com/)
- Database: [MongoDB](https://www.mongodb.com/) + [Mongoose](https://mongoosejs.com/)
- Authentication: [JWT (JSON Web Tokens)](https://jwt.io/) + Cookies
- Encryption: [bcryptjs](https://www.npmjs.com/package/bcryptjs) for password hashing
- API Testing: Postman
- Environment Variables Management: dotenv
- Package Manager: npm

---

## Features Implemented

### 1. Authentication System
User Signup, Login, and Logout
JWT-based authentication with secure cookies
Password encryption using bcryptjs
Authentication middleware to protect routes

### 2. User Profile Management
View user profile
Edit profile details (restricted fields for security)
Update password with validation

### 3. Connection Request System
Send connection requests (`Interested` or `Ignored`)
Accept or reject received requests
Prevent duplicate requests using MongoDB validation
Prevent self-requests using Mongoose `.pre` middleware

### 4. Feed API & Pagination
Fetch suggested developers while excluding:
- Logged-in user
- Existing connections
- Ignored users
- Users with pending requests
Implemented pagination using `skip` and `limit`
Optimized query using MongoDB `$nin` and `$ne` operators

### 5. Database Design
User Schema:
- Sanitized input fields (`trim`, `lowercase`, validation)
- Unique constraints on email and username

ConnectionRequest Schema:
- `fromUserId`, `toUserId`, `status` with enum validation
- Indexed fields for optimized queries
- Prevents multiple requests between the same users

### 6. Advanced Query Optimization
Indexes and Compound Indexes:
- Used `index: true` for faster queries
- Implemented compound indexes to optimize search

### 7. Middleware Implementation
Authentication Middleware: Protects private routes
Error Handling Middleware: Centralized error response
Mongoose `.pre` Middleware: Prevents self-requests

### 8. Express Router Structure
Modular route organization for maintainability
APIs structured into separate routers (`auth`, `profile`, `connections`, `users`)

---
