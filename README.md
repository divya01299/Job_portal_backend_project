# Job Portal Backend

A RESTful backend for a job portal that connects job seekers with employers. The application provides authentication, job management, job search, applications, role-based access control, and analytics through a structured Node.js and Express.js API.

## Features

* **Authentication & Authorization**

  * User registration and login
  * JWT-based authentication
  * Password hashing using bcrypt
  * Role-based access for job seekers and employers

* **Job Management**

  * Employers can create, update, and delete jobs
  * Job seekers can browse and search available jobs
  * Job filtering, sorting, pagination, and partial text search

* **Application Management**

  * Job seekers can apply for jobs
  * Prevents duplicate applications for the same job
  * Application status management

* **Analytics**

  * Job and application analytics using MongoDB Aggregation Pipeline

* **Security**

  * Helmet security headers
  * Rate limiting
  * Input sanitization
  * Request validation
  * Centralized error handling

* **API Documentation**

  * Interactive API documentation using Swagger UI

## Tech Stack

* **Runtime:** Node.js
* **Framework:** Express.js
* **Database:** MongoDB
* **ODM:** Mongoose
* **Authentication:** JWT
* **Password Hashing:** bcrypt
* **Security:** Helmet, Rate Limiting, Input Sanitization

## Project Structure

```text
Job-Portal-Backend/
├── config/
│   └── db.js
├── controller/
│   ├── authController.js
│   ├── userController.js
│   ├── jobController.js
│   └── applicationController.js
├── middlewares/
│   ├── authMiddleware.js
│   ├── errorMiddleware.js
│   └── upload.js
├── models/
│   ├── userModel.js
│   ├── jobsModel.js
│   └── applicationModel.js
├── route/
│   ├── authRoutes.js
│   ├── userRoutes.js
│   ├── jobRoutes.js
│   └── applicationRoutes.js
├── uploads/
├── index.js
├── package.json
└── README.md
```

## Getting Started

### Prerequisites

Make sure you have the following installed:

* Node.js
* MongoDB

### Installation

1. Clone the repository:

```bash
git clone https://github.com/pranavst30/Backend-Job-Portal.git
```

2. Navigate to the project directory:

```bash
cd Backend-Job-Portal
```

3. Install dependencies:

```bash
npm install
```

4. Create a `.env` file in the root directory:

```env
PORT=8080
DEV_MODE=development
MONGO_URL=your_mongodb_connection_string
JWT_KEY=your_secret_key
```

5. Start the server:

```bash
npm run server
```

For production mode:

```bash
npm start
```

## API Access

Base URL:

```text
http://localhost:8080
```

Swagger API Documentation:

```text
http://localhost:8080/api-docs
```

Swagger UI allows you to explore and test the available API endpoints directly from the browser.

## Authentication

Protected routes require a JWT token in the `Authorization` header:

```text
Authorization: Bearer <your_jwt_token>
```

### Authentication Flow

1. Register a new user or log in.
2. Receive the JWT token from the response.
3. Pass the token in the `Authorization` header for protected requests.

## API Overview

### Authentication

```text
POST /api/v1/auth/register
POST /api/v1/auth/login
```

### Jobs

```text
POST   /api/v1/job/create
GET    /api/v1/job/get-all
PUT    /api/v1/job/update/:id
DELETE /api/v1/job/delete/:id
```

### Applications

```text
POST /api/v1/application/apply/:jobId
GET  /api/v1/application/get-applications
```

> Refer to the Swagger documentation for the complete list of endpoints, request formats, and responses.

## Error Handling

The API follows a consistent error response structure:

```json
{
  "success": false,
  "message": "Error description",
  "error": "Detailed error message"
}
```

Common HTTP status codes include:

* `200` - Success
* `201` - Created
* `400` - Bad Request
* `401` - Unauthorized
* `403` - Forbidden
* `404` - Not Found
* `500` - Internal Server Error

## Deployment

The project includes Vercel deployment configuration.

```bash
npm install -g vercel
vercel
```

Configure the required environment variables in the deployment platform before starting the application.

## License

This project is licensed under the ISC License.

