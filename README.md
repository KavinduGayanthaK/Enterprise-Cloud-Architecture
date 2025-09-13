# Cloud Enabled Deployment In Action with AWS

This repository contains four projects:

- course-service (Spring Boot + MySQL)
- student-service (Spring Boot + MongoDB)
- media-service (Spring Boot + Local file storage, can be extended to S3/MinIO)
- frontend-app (React + TypeScript)

## Backend Services

### 1. course-service
- Entity: Course(id, name, duration)
- Endpoints:
  - GET /courses
  - GET /courses/{id}
  - POST /courses
  - DELETE /courses/{id}
- Default port: 8081
- Database Configuration
  - Currently, the course-service is configured only for AWS RDS MySQL.
    - application-aws.properties
      - MySQL Configurations (AWS RDS)
        - spring.datasource.host=database-1.c3q0umy2autw.eu-north-1.rds.amazonaws.com
        - spring.datasource.port=3306
        - spring.datasource.url=jdbc:mysql://${spring.datasource.host}:${spring.datasource.port}/eca_courses?createDatabaseIfNotExist=true
        - spring.datasource.username=root
        - spring.datasource.password=Kavindu1234*

### 2. student-service
- Document: Student(registrationNumber, fullName, address, contact, email)
- Endpoints:
  - GET /students
  - GET /students/{id}
  - POST /students
  - DELETE /students/{id}
- Default port: 8082
- Configure MongoDB settings

### 3. media-service
- Resource: files
- Endpoints:
  - POST /files (multipart/form-data: file)
  - GET /files (list)
  - GET /files/{id} (fetch)
  - DELETE /files/{id} (delete)
- Default port: 8083
- Uses local disk storage at `./data/media` by default (override with env var `MEDIA_STORAGE_DIR`).

## Frontend (frontend-app)
- React + TypeScript + MUI + Axios + Vite app with 3 sections: Courses, Students, Media
- Scripts:
  - npm run dev (Vite dev server)
  - npm run build (TypeScript build + Vite build)
  - npm run preview (Preview built app)

## Build

- Backend: run `mvn -q -e -DskipTests package` at repo root to build services.
- Frontend: run `npm install` then `npm run dev` inside `frontend-app`.

## Deployment Notes
- AWS
  - Use application-aws.properties with RDS MySQL

- GCP
  - Use application-gcp.properties with Cloud SQL MySQL
  - Can integrate with GCP Cloud Storage


## GCP Connect Video Link
- https://drive.google.com/file/d/1QgglFbIG1X7ZD6wHIN72bY2dxL-s6beQ/view?usp=sharing