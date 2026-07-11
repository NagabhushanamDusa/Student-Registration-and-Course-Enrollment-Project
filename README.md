# Student Registration and Course Enrollment Portal

A full-stack web application for registering students, viewing registered students, enrolling students into courses, and viewing enrollment records. The project was built as a fresher full-stack engineering assessment with a React frontend, Spring Boot + Apache Camel backend, and PostgreSQL database.

## Project Overview

The portal provides a simple academic workflow:

- View the home page
- Register a student
- View registered students
- Enroll a student into a course
- View course enrollments

The application follows a standard three-layer architecture:

```text
React Frontend -> Spring Boot + Apache Camel REST API -> PostgreSQL Database
```

## Technology Stack

### Frontend

- React.js
- React Router
- Axios
- Bootstrap
- Lucide React icons
- CSS

### Backend

- Java 17
- Spring Boot
- Apache Camel
- Spring JDBC
- Maven

### Database

- PostgreSQL

### Deployment

- Frontend: Vercel
- Backend: Render
- Database: Neon PostgreSQL
- Backend containerization: Docker

## Project Structure

```text
Student Project/
|-- frontend/
|   |-- public/
|   |-- src/
|   |   |-- components/
|   |   |-- pages/
|   |   |-- services/
|   |   |-- App.js
|   |   |-- index.js
|   |   `-- styles.css
|   `-- package.json
|-- backend/
|   |-- src/main/java/com/rava/studentportal/
|   |   |-- config/
|   |   |-- models/
|   |   |-- repositories/
|   |   |-- routes/
|   |   |-- services/
|   |   `-- Application.java
|   |-- src/main/resources/
|   |   |-- application.properties
|   |   |-- schema.sql
|   |   `-- data.sql
|   |-- Dockerfile
|   `-- pom.xml
|-- DEPLOYMENT.md
|-- package.json
`-- README.md
```

## Setup Instructions

### Prerequisites

Install these tools before running the project locally:

- Java 17
- Apache Maven
- Node.js and npm
- PostgreSQL
- Git
- Postman, optional for API testing

## Database Setup Steps

Create a PostgreSQL database:

```sql
CREATE DATABASE student_portal;
```

The backend automatically creates the required tables from:

```text
backend/src/main/resources/schema.sql
```

Tables:

- `students`
- `courses`
- `enrollments`

Sample course data is inserted from:

```text
backend/src/main/resources/data.sql
```

Default sample courses:

- Java Fundamentals
- React Basics
- Database Essentials

## Backend Configuration

The backend reads database credentials from environment variables.

For local PostgreSQL:

```powershell
$env:DB_USERNAME="postgres"
$env:DB_PASSWORD="your_postgresql_password"
```

For cloud deployment, use Spring Boot datasource variables:

```text
SPRING_DATASOURCE_URL=jdbc:postgresql://HOST/DATABASE?sslmode=require
SPRING_DATASOURCE_USERNAME=your_database_username
SPRING_DATASOURCE_PASSWORD=your_database_password
```

The backend runs locally on:

```text
http://localhost:8082
```

## How To Run Backend

From the project root:

```powershell
cd backend
$env:DB_USERNAME="postgres"
$env:DB_PASSWORD="your_postgresql_password"
mvn spring-boot:run
```

If the backend starts successfully, test:

```text
http://localhost:8082/api/courses
```

## How To Run Frontend

Install frontend dependencies:

```powershell
cd frontend
npm install
```

Start the React frontend:

```powershell
npm start
```

The frontend runs locally on:

```text
http://localhost:3000
```

The frontend uses the proxy in `frontend/package.json` for local API calls:

```json
"proxy": "http://localhost:8082"
```

## Run From Project Root

The root `package.json` includes helper scripts:

```powershell
npm run install:frontend
npm run dev
```

## API Endpoints

### Student APIs

Create student:

```http
POST /api/students
```

Request body:

```json
{
  "firstName": "John",
  "lastName": "Doe",
  "email": "john@example.com",
  "phoneNumber": "9999999999"
}
```

Get all students:

```http
GET /api/students
```

### Course APIs

Get all courses:

```http
GET /api/courses
```

### Enrollment APIs

Create enrollment:

```http
POST /api/enrollments
```

Request body:

```json
{
  "studentId": 1,
  "courseId": 2,
  "enrollmentDate": "2026-05-18"
}
```

Get all enrollments:

```http
GET /api/enrollments
```

## Validation Rules

Student registration:

- First name is required
- Last name is required
- Email must be valid and unique
- Phone number must be numeric

Course enrollment:

- Student must exist
- Course must exist
- Enrollment date cannot be a future date

## Deployment

Deployment steps are documented in:

```text
DEPLOYMENT.md
```

Production deployment uses:

```text
Vercel frontend -> Render backend -> Neon PostgreSQL
```

Frontend production API URL is configured with:

```text
REACT_APP_API_BASE_URL=https://your-render-backend-url
```

Backend CORS origins are configured with:

```text
https://your-vercel-url,http://localhost:3000
``

## Screenshots

Add screenshots of the completed pages here before final submission:

### Home Page
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b38e8813-93e8-42f3-b7c8-9b2a4a3e12d0" />

### Register Student Page
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6946a81a-44b0-4387-a463-591dc28bb86f" />

### Student List Page
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e860208a-1419-4e57-8e96-2f1c79019301" />

### Course Enrollment Page
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1d7cc372-dd97-4574-93bc-8ca13412cdee" />

### Enrollment List Page
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d4c5c52a-d199-443a-b70b-f0df54273b49" />

