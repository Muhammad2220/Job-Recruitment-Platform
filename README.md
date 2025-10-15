# Job-Recruitment-Platform
A modern full-stack job recruitment platform for managing software developer applications. The platform allows applicants to submit applications, upload CVs, and track their application status. Recruiters and admins can manage job postings, review applications, and communicate with candidates. The project is Docker-ready, fully secure, and built with a modular structure for scalability.

Table of Contents

Project Overview

Features

Technology Stack

Folder Structure

Getting Started

Prerequisites

Front-End Setup

Back-End Setup

Docker Setup

Database Schema

API Endpoints

Email Integration

Security

Testing

Project Roadmap

Contributing

License

Project Overview

This project is designed to streamline the recruitment process:

Applicants can submit job applications, upload CVs, and track status.

Recruiters/Admins can manage job postings, review applications, and communicate with candidates.

Fully Dockerized for easy development and deployment.

Secure, modular, and scalable architecture.

Features

Applicant Features:

Submit applications with dynamic fields.

Upload CV and cover letter (PDF only, max 5 MB).

Receive email confirmation with a unique token.

Track application status via token.

Recruiter/Admin Features:

Role-based authentication (Admin, Recruiter, Applicant).

Create and manage job postings.

Review, filter, and shortlist applications.

Dashboard with analytics.

Automated email notifications for status updates.

Technology Stack
Layer	Technology
Front-End	React.js + Tailwind CSS + Axios
Back-End	Node.js + Express.js
Database	PostgreSQL
Authentication	JWT (JSON Web Tokens)
Email Service	SendGrid / SMTP
File Storage	Local storage or AWS S3 (optional)
Containerization	Docker + Docker Compose
Testing	Jest, Supertest (Back-End), React Testing Library (Front-End)
Version Control	Git & GitHub
Folder Structure
job-recruitment-platform/
│
├── backend/
│   ├── src/
│   │   ├── controllers/       # Request handlers
│   │   ├── models/            # Database models (Users, Jobs, Applications)
│   │   ├── routes/            # API routes
│   │   ├── middlewares/       # Authentication, validation, error handling
│   │   ├── utils/             # Helpers (email sending, file upload)
│   │   ├── config/            # DB config, env variables
│   │   └── server.js          # Entry point
│   ├── tests/                 # Unit & integration tests
│   ├── package.json
│   └── Dockerfile
│
├── frontend/
│   ├── public/                # Static assets
│   ├── src/
│   │   ├── components/        # Reusable UI components
│   │   ├── pages/             # Pages (Home, Jobs, ApplicationForm, Dashboard)
│   │   ├── services/          # API calls
│   │   ├── context/           # State management (React Context / Redux)
│   │   ├── App.jsx
│   │   └── index.jsx
│   ├── package.json
│   └── Dockerfile
│
├── database/
│   └── init.sql               # Database schema & seed data
│
├── docker-compose.yml
├── .env.example               # Example environment variables
└── README.md

Getting Started
Prerequisites

Node.js v18+

npm or yarn

PostgreSQL 14+

Docker & Docker Compose

Front-End Setup

Navigate to the frontend folder:

cd frontend


Install dependencies:

npm install


Start development server:

npm run dev


Open in browser: http://localhost:3000

Back-End Setup

Navigate to backend folder:

cd backend


Install dependencies:

npm install


Create .env file (example .env.example provided) with:

PORT=5000
DB_HOST=postgres
DB_USER=youruser
DB_PASSWORD=yourpassword
DB_NAME=job_recruitment
JWT_SECRET=your_jwt_secret
SENDGRID_API_KEY=your_sendgrid_key


Run server:

npm run dev


API will run on http://localhost:5000

Docker Setup

Build and start all services:

docker-compose up --build


Services included in docker-compose.yml:

frontend → React app

backend → Node.js API

db → PostgreSQL database

Stop services:

docker-compose down

Database Schema

Users Table

id (PK)

name

email

password_hash

role (Admin/Recruiter/Applicant)

created_at

Jobs Table

id (PK)

title

description

posted_by (FK → Users)

created_at

Applications Table

id (PK)

user_id (FK → Users)

job_id (FK → Jobs)

cv_url

cover_letter_url

status (Pending/Shortlisted/Hired/Rejected)

token (unique application token)

created_at

API Endpoints

Applicants:

POST /api/applications → Submit a new application

GET /api/applications/:token → Retrieve application status

Recruiters/Admins:

POST /api/jobs → Create new job posting

GET /api/jobs → List all jobs

PATCH /api/applications/:id/status → Update application status

Authentication:

POST /api/auth/register → Register new user

POST /api/auth/login → Login and receive JWT

Email Integration

SendGrid or SMTP integration for:

Application submission confirmation

Application status updates

Security

Input validation & sanitization

JWT authentication

Secure file uploads (PDF only, max 5MB)

HTTPS recommended in production

Passwords hashed (bcrypt)

Testing

Back-End: Jest + Supertest

Front-End: Jest + React Testing Library

Run tests:

npm test           # Frontend
npm run test:backend   # Backend

Project Roadmap

Applicant dashboard (edit submissions, view status)

Recruiter/Admin dashboard with analytics & filters

Multi-file uploads (certificates, portfolios)

OAuth login (LinkedIn, GitHub)

Docker Compose for full-stack orchestration

Contributing

Fork repository

Create branch: git checkout -b feature/your-feature

Commit: git commit -m "Add feature"

Push: git push origin feature/your-feature

Open Pull Request

License

MIT License
