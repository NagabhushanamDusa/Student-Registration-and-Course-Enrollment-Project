# Deployment Guide

This project deploys across three free-friendly services:

- Frontend: Vercel
- Backend: Render
- Database: Neon PostgreSQL

## Final URL Flow

```text
Vercel frontend -> Render backend -> Neon PostgreSQL
```

## 1. Create Accounts

Create free accounts:

- GitHub: https://github.com
- Neon: https://neon.tech
- Render: https://render.com
- Vercel: https://vercel.com

Use GitHub login where available.

## 2. Push Project To GitHub

Push the full project repository to GitHub before deploying.

## 3. Create Neon Database

1. Open https://console.neon.tech
2. Click `New Project`.
3. Enter project name: `student-portal`.
4. Choose a region near you.
5. Click `Create Project`.
6. Open `Dashboard` -> `Connection string`.
7. Copy the JDBC-style values needed for Spring Boot:

```text
SPRING_DATASOURCE_URL=jdbc:postgresql://YOUR_NEON_HOST/YOUR_DATABASE?sslmode=require
SPRING_DATASOURCE_USERNAME=YOUR_NEON_USERNAME
SPRING_DATASOURCE_PASSWORD=YOUR_NEON_PASSWORD
```

## 4. Deploy Backend On Render

1. Open https://dashboard.render.com
2. Click `New` -> `Web Service`.
3. Connect your GitHub repository.
4. Select the project repository.
5. Set:

```text
Name: student-portal-backend
Root Directory: backend
Runtime: Java
Language: Docker
```

6. Add environment variables:

```text
SPRING_DATASOURCE_URL=jdbc:postgresql://YOUR_NEON_HOST/YOUR_DATABASE?sslmode=require
SPRING_DATASOURCE_USERNAME=YOUR_NEON_USERNAME
SPRING_DATASOURCE_PASSWORD=YOUR_NEON_PASSWORD
APP_CORS_ALLOWED_ORIGINS=http://localhost:3000
```

7. Click `Create Web Service`.
8. After deployment, copy the backend URL:

```text
https://student-portal-backend.onrender.com
```

## 5. Deploy Frontend On Vercel

1. Open https://vercel.com/dashboard
2. Click `Add New` -> `Project`.
3. Import your GitHub repository.
4. Set:

```text
Framework Preset: Create React App
Root Directory: frontend
Build Command: npm run build
Output Directory: build
Install Command: npm install
```

5. Add environment variable:

```text
REACT_APP_API_BASE_URL=https://YOUR_RENDER_BACKEND_URL
```

6. Click `Deploy`.
7. After deployment, copy the frontend URL:

```text
https://your-project-name.vercel.app
```

## 6. Update Render CORS

After Vercel gives the frontend URL:

1. Go to Render backend service.
2. Open `Environment`.
3. Update:

```text
APP_CORS_ALLOWED_ORIGINS=https://your-project-name.vercel.app,http://localhost:3000
```

4. Click `Save Changes`.
5. Render redeploys the backend.

## 7. Test

Open the Vercel frontend URL and test:

- Register student
- View students
- Load courses
- Submit enrollment
- View enrollments
