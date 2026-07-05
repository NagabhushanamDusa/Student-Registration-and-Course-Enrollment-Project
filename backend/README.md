# Student Portal Backend

Spring Boot and Apache Camel backend for the Student Registration and Course Enrollment Portal.

## Technology Stack

- Java 17
- Spring Boot
- Apache Camel
- Maven
- PostgreSQL

## Database

Create the PostgreSQL database:

```sql
CREATE DATABASE student_portal;
```

The backend uses this connection:

```properties
spring.datasource.url=${SPRING_DATASOURCE_URL:jdbc:postgresql://localhost:5432/student_portal}
spring.datasource.username=${SPRING_DATASOURCE_USERNAME:${DB_USERNAME:postgres}}
spring.datasource.password=${SPRING_DATASOURCE_PASSWORD:${DB_PASSWORD:postgres}}
```

Do not commit your real database password. Set it when running the project.

## Run Backend

From the `backend` folder:

```powershell
$env:DB_USERNAME="postgres"
$env:DB_PASSWORD="your_postgresql_password"
mvn spring-boot:run
```

The backend runs on:

```text
http://localhost:8082
```

## APIs

- `POST /api/students`
- `GET /api/students`
- `GET /api/courses`
- `POST /api/enrollments`
- `GET /api/enrollments`
