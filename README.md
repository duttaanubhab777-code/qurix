# Qurix

Qurix — Smart Question Bank & Assessment Platform

A scalable question bank, practice, and examination platform for students.

Qurix is a full-stack educational assessment platform designed for Class 11–12 students and competitive examination aspirants. It provides a structured question bank, customizable practice tests, examination simulation, automated evaluation, detailed solutions, and performance analytics.

The platform is designed to support multiple education boards and competitive examinations through a configurable examination engine rather than hardcoded exam rules.

---

1. Project Overview

Qurix aims to make question practice, mock tests, and academic assessment more organized, accessible, and effective.

Students can select their education board, examination, subject, chapter, difficulty level, and language to generate practice tests from a verified question bank.

Administrators manage the question bank by uploading question images, PDFs, answers, marking schemes, and detailed solutions.

The platform does not independently invent questions or official answer keys. It uses administrator-provided and verified educational content.

Core Objectives

- Build a structured and searchable question bank.
- Support multiple education boards and competitive examinations.
- Generate customized tests from verified questions.
- Support image-based and LaTeX-based mathematical content.
- Provide automated evaluation and detailed solutions.
- Track student performance and learning progress.
- Maintain a scalable and maintainable backend architecture.

---

2. Target Users

Students

- Class 11 and Class 12 Science students.
- JEE Main aspirants.
- JEE Advanced aspirants.
- WBJEE aspirants.
- NEET UG aspirants.

Administrators

- Manage questions and solutions.
- Upload question images and PDFs in bulk.
- Organize questions by subject, chapter, board, and examination.
- Configure examination patterns.
- Review and approve uploaded questions.
- Manage users and platform content.

---

3. Supported Academic Categories

Education Boards

- WBCHSE
- CBSE
- Other Indian State Boards (future expansion)

Competitive Examinations

- JEE Main
- JEE Advanced
- WBJEE
- NEET UG

Subjects

- Physics
- Chemistry
- Mathematics
- Biology

Supported Content Types

- Text-based questions
- Mathematical equations using LaTeX
- Question images
- Diagrams and graphs
- Chemistry structures
- Scanned question papers
- Image-based solutions
- Step-by-step written solutions

---

4. Technology Stack

Layer| Technology
Frontend| React.js
Build Tool| Vite
Styling| Tailwind CSS
Backend| Node.js
Backend Framework| Express.js
Database| MongoDB
ODM| Mongoose
Image Storage| Cloudinary
Mathematical Rendering| KaTeX
Authentication| JWT
Password Hashing| bcrypt
Validation| Zod
File Upload| Multer / Signed Cloudinary Upload
Image Processing| Sharp
PDF Processing| pdfjs-dist
Background Jobs| BullMQ
Job Queue| Redis
API Documentation| Swagger / OpenAPI
Testing| Vitest / Jest + Supertest
Logging| Pino
Security| Helmet, CORS, Rate Limiting

---

5. System Architecture

Qurix follows a Modular Monolith Architecture.

The backend is divided into independent modules with clear responsibilities. This keeps the codebase maintainable while allowing individual modules to evolve as the platform grows.

                    QURIX PLATFORM
                           |
              +------------+------------+
              |                         |
         React Frontend             Admin Panel
              |                         |
              +------------+------------+
                           |
                       REST API
                           |
                  Express Application
                           |
        +------------------+------------------+
        |                  |                  |
   Auth Module       Question Module      Test Module
        |                  |                  |
   User Module       Bulk Upload Module   Result Module
        |                  |                  |
        +------------------+------------------+
                           |
                    Service Layer
                           |
              +------------+------------+
              |                         |
          MongoDB                   Cloudinary
              |
        Redis / BullMQ
              |
        Background Workers

Architecture Principles

- Separation of concerns.
- Reusable services.
- Centralized error handling.
- Request validation.
- Secure authentication and authorization.
- Consistent API responses.
- Environment-based configuration.
- Background processing for heavy tasks.
- Database indexing and optimized queries.
- Testable and modular code.

---

6. Production-Grade Backend Folder Structure

The backend should follow a clean, modular "src" structure.

server/
│
├── src/
│   │
│   ├── config/
│   │   ├── env.js
│   │   ├── database.js
│   │   ├── cloudinary.js
│   │   ├── redis.js
│   │   ├── cors.js
│   │   ├── swagger.js
│   │   └── logger.js
│   │
│   ├── constants/
│   │   ├── app.constants.js
│   │   ├── api.constants.js
│   │   ├── roles.constants.js
│   │   ├── question.constants.js
│   │   ├── exam.constants.js
│   │   ├── status.constants.js
│   │   └── error.constants.js
│   │
│   ├── database/
│   │   ├── indexes/
│   │   │   ├── user.index.js
│   │   │   ├── question.index.js
│   │   │   └── test.index.js
│   │   │
│   │   ├── seeds/
│   │   │   ├── admin.seed.js
│   │   │   ├── subjects.seed.js
│   │   │   └── exam-blueprints.seed.js
│   │   │
│   │   └── migrations/
│   │
│   ├── modules/
│   │   │
│   │   ├── auth/
│   │   │   ├── auth.controller.js
│   │   │   ├── auth.service.js
│   │   │   ├── auth.routes.js
│   │   │   ├── auth.validation.js
│   │   │   └── auth.model.js
│   │   │
│   │   ├── users/
│   │   │   ├── user.controller.js
│   │   │   ├── user.service.js
│   │   │   ├── user.routes.js
│   │   │   ├── user.validation.js
│   │   │   └── user.model.js
│   │   │
│   │   ├── questions/
│   │   │   ├── question.controller.js
│   │   │   ├── question.service.js
│   │   │   ├── question.routes.js
│   │   │   ├── question.validation.js
│   │   │   ├── question.model.js
│   │   │   └── question.repository.js
│   │   │
│   │   ├── subjects/
│   │   │   ├── subject.controller.js
│   │   │   ├── subject.service.js
│   │   │   ├── subject.routes.js
│   │   │   └── subject.model.js
│   │   │
│   │   ├── chapters/
│   │   │   ├── chapter.controller.js
│   │   │   ├── chapter.service.js
│   │   │   ├── chapter.routes.js
│   │   │   └── chapter.model.js
│   │   │
│   │   ├── exams/
│   │   │   ├── exam.controller.js
│   │   │   ├── exam.service.js
│   │   │   ├── exam.routes.js
│   │   │   ├── exam.validation.js
│   │   │   └── exam.model.js
│   │   │
│   │   ├── exam-blueprints/
│   │   │   ├── blueprint.controller.js
│   │   │   ├── blueprint.service.js
│   │   │   ├── blueprint.routes.js
│   │   │   ├── blueprint.validation.js
│   │   │   └── blueprint.model.js
│   │   │
│   │   ├── tests/
│   │   │   ├── test.controller.js
│   │   │   ├── test.service.js
│   │   │   ├── test.routes.js
│   │   │   ├── test.validation.js
│   │   │   ├── test.model.js
│   │   │   └── test.repository.js
│   │   │
│   │   ├── results/
│   │   │   ├── result.controller.js
│   │   │   ├── result.service.js
│   │   │   ├── result.routes.js
│   │   │   ├── result.model.js
│   │   │   └── result.repository.js
│   │   │
│   │   ├── analytics/
│   │   │   ├── analytics.controller.js
│   │   │   ├── analytics.service.js
│   │   │   └── analytics.routes.js
│   │   │
│   │   ├── bulk-upload/
│   │   │   ├── upload.controller.js
│   │   │   ├── upload.service.js
│   │   │   ├── upload.routes.js
│   │   │   ├── upload.validation.js
│   │   │   ├── upload.model.js
│   │   │   ├── image.processor.js
│   │   │   ├── pdf.processor.js
│   │   │   ├── ocr.service.js
│   │   │   ├── question.extractor.js
│   │   │   ├── question.grouping.js
│   │   │   └── upload.repository.js
│   │   │
│   │   └── admin/
│   │       ├── admin.controller.js
│   │       ├── admin.service.js
│   │       └── admin.routes.js
│   │
│   ├── middleware/
│   │   ├── auth.middleware.js
│   │   ├── role.middleware.js
│   │   ├── error.middleware.js
│   │   ├── not-found.middleware.js
│   │   ├── validate.middleware.js
│   │   ├── rate-limit.middleware.js
│   │   ├── upload.middleware.js
│   │   ├── request-id.middleware.js
│   │   └── security.middleware.js
│   │
│   ├── services/
│   │   ├── cloudinary.service.js
│   │   ├── email.service.js
│   │   ├── token.service.js
│   │   ├── cache.service.js
│   │   └── notification.service.js
│   │
│   ├── jobs/
│   │   ├── queues/
│   │   │   └── upload.queue.js
│   │   ├── workers/
│   │   │   └── upload.worker.js
│   │   └── job.events.js
│   │
│   ├── utils/
│   │   ├── ApiError.js
│   │   ├── ApiResponse.js
│   │   ├── asyncHandler.js
│   │   ├── generateToken.js
│   │   ├── pagination.js
│   │   ├── sanitize.js
│   │   ├── normalize-answer.js
│   │   ├── calculate-score.js
│   │   ├── random-selection.js
│   │   ├── logger.js
│   │   └── file-validator.js
│   │
│   ├── validators/
│   │   ├── common.validator.js
│   │   └── object-id.validator.js
│   │
│   ├── routes/
│   │   └── index.js
│   │
│   ├── app.js
│   └── server.js
│
├── tests/
│   ├── unit/
│   ├── integration/
│   ├── e2e/
│   └── fixtures/
│
├── scripts/
│   ├── seed.js
│   ├── create-admin.js
│   └── build-indexes.js
│
├── logs/
├── uploads/
├── .env.example
├── .gitignore
├── package.json
└── README.md

Important: This is the target architecture. You do not need to create every file on day one. Build modules gradually as features become necessary. Avoid empty files and unnecessary abstractions.

---

7. Backend Folder Responsibilities

config/

Contains application configuration and external service connections.

Examples:

- "database.js" — MongoDB connection.
- "cloudinary.js" — Cloudinary configuration.
- "redis.js" — Redis connection.
- "env.js" — Environment variable validation.
- "swagger.js" — API documentation configuration.

constants/

Contains fixed application values.

Examples:

- User roles.
- Question types.
- Supported subjects.
- Examination identifiers.
- Question statuses.
- API route prefixes.

Avoid scattering the same hardcoded values across controllers and services.

database/

Contains database-related setup.

- Index definitions.
- Seed data.
- Migration scripts.
- Initial examination configurations.

modules/

Each major business feature has its own module.

A module typically contains:

File| Responsibility
controller| Handles HTTP requests and responses
service| Contains business logic
routes| Defines API endpoints
validation| Validates request data
model| Defines MongoDB schema
repository| Handles reusable database queries

The repository layer is useful when queries become complex. It does not need to be added to every small module.

middleware/

Runs between the incoming request and controller.

Examples:

- Authentication.
- Role-based access control.
- Request validation.
- Rate limiting.
- Error handling.
- Upload restrictions.

services/

Contains reusable integrations and infrastructure services shared across modules.

For example, Cloudinary upload logic should not be duplicated inside every controller.

jobs/

Handles time-consuming asynchronous tasks.

Examples:

- Bulk image processing.
- PDF processing.
- OCR.
- Question extraction.
- Upload batch status updates.

utils/

Contains small reusable helper functions.

Examples:

- Score calculation.
- Answer normalization.
- Pagination.
- Random question selection.
- API error formatting.

A utility should not become a place for unrelated business logic.

---

8. Frontend Folder Structure

client/
│
├── public/
│   ├── favicon.svg
│   └── logo.svg
│
├── src/
│   │
│   ├── assets/
│   │   ├── images/
│   │   ├── icons/
│   │   └── fonts/
│   │
│   ├── components/
│   │   ├── common/
│   │   ├── layout/
│   │   ├── forms/
│   │   ├── questions/
│   │   ├── tests/
│   │   └── ui/
│   │
│   ├── pages/
│   │   ├── Home/
│   │   ├── Login/
│   │   ├── Register/
│   │   ├── Dashboard/
│   │   ├── QuestionBank/
│   │   ├── Practice/
│   │   ├── Test/
│   │   ├── Results/
│   │   ├── Analytics/
│   │   └── Admin/
│   │
│   ├── features/
│   │   ├── auth/
│   │   ├── questions/
│   │   ├── tests/
│   │   ├── results/
│   │   ├── analytics/
│   │   └── bulk-upload/
│   │
│   ├── hooks/
│   ├── context/
│   ├── services/
│   │   ├── api.js
│   │   ├── auth.api.js
│   │   ├── question.api.js
│   │   ├── test.api.js
│   │   └── result.api.js
│   │
│   ├── routes/
│   │   ├── AppRoutes.jsx
│   │   ├── ProtectedRoute.jsx
│   │   └── AdminRoute.jsx
│   │
│   ├── utils/
│   ├── constants/
│   ├── styles/
│   ├── App.jsx
│   └── main.jsx
│
├── .env.example
├── index.html
├── package.json
└── vite.config.js

Frontend Responsibilities

- "components/" — Reusable UI components.
- "pages/" — Full application pages.
- "features/" — Feature-specific UI and logic.
- "hooks/" — Reusable React hooks.
- "context/" — Global application state where appropriate.
- "services/" — API communication.
- "routes/" — Application routing and route protection.
- "utils/" — Frontend helper functions.

---

9. Main Application Modules

9.1 Authentication Module

Features:

- User registration.
- Login and logout.
- Password hashing.
- Access token management.
- Refresh token rotation.
- Protected routes.
- Role-based permissions.

Roles:

- "student"
- "admin"
- "super_admin"

Only authorized administrators can create, edit, approve, or delete questions.

9.2 Question Bank Module

This is the central module of Qurix.

Every question should have structured metadata.

Example question structure:

{
  "class": 12,
  "subject": "Mathematics",
  "chapter": "Calculus",
  "boards": ["WBCHSE"],
  "exams": ["JEE_MAIN", "WBJEE"],
  "questionType": "SINGLE_CORRECT",
  "difficulty": "HARD",
  "language": "EN",
  "marks": 4,
  "negativeMarks": 1,
  "content": {
    "text": "Find the value of the given expression.",
    "latex": "\\int_0^1 x^2 dx",
    "images": []
  },
  "options": [],
  "correctAnswer": {
    "type": "OPTION",
    "value": "A"
  },
  "solution": {
    "text": "Detailed explanation...",
    "latex": "",
    "images": []
  },
  "status": "APPROVED"
}

This is an illustrative data structure. Production schemas should use stricter validation, references, versioning, and appropriate answer formats for each question type.

Supported Question Types

- "SINGLE_CORRECT"
- "MULTIPLE_CORRECT"
- "NUMERICAL"
- "INTEGER"
- "TRUE_FALSE"
- "SUBJECTIVE" (future feature)

Question Status

- "DRAFT"
- "PROCESSING"
- "PENDING_REVIEW"
- "APPROVED"
- "REJECTED"
- "ARCHIVED"

Only approved questions should be available to students.

---

10. Bulk Question Upload System

Qurix should provide a powerful admin-side bulk upload system.

Administrators should be able to upload multiple images or PDFs in one batch.

Upload Workflow

Admin selects category
          |
          v
Selects board / examination
          |
          v
Selects subject and chapter
          |
          v
Selects language
          |
          v
Uploads multiple images or PDF
          |
          v
Files stored in Cloudinary
          |
          v
Background processing
          |
          v
OCR / content extraction
          |
          v
Question grouping and mapping
          |
          v
Admin review
          |
          v
Answer and solution verification
          |
          v
Approve questions
          |
          v
Publish to Question Bank

Bulk Upload Requirements

- Multiple image uploads.
- Multiple PDF uploads.
- Common metadata for an entire batch.
- Image ordering.
- Question grouping across multiple images.
- Manual question boundary correction.
- Answer key mapping.
- Solution image mapping.
- OCR extraction where applicable.
- Processing status tracking.
- Admin review before publication.

Important: OCR is not guaranteed to correctly understand mathematical equations, diagrams, or handwritten material. The system must allow manual correction before questions become available to students.

The admin supplies the official question content, correct answers, marks, instructions, and solutions. Qurix manages storage, organization, processing, test generation, and evaluation.

---

11. Examination Blueprint Engine

Different examinations have different question formats and marking rules.

Therefore, Qurix must not hardcode one examination pattern into the test-generation logic.

Instead, it should use configurable examination blueprints.

Example:

{
  "exam": "JEE_MAIN",
  "subject": "MATHEMATICS",
  "mode": "CUSTOM_PRACTICE",
  "version": 1,
  "duration": 180,
  "questionCount": 30,
  "difficultyDistribution": {
    "EASY": 5,
    "MEDIUM": 15,
    "HARD": 10
  },
  "questionTypes": [
    "SINGLE_CORRECT",
    "NUMERICAL"
  ],
  "markingScheme": {
    "correct": 4,
    "incorrect": -1,
    "unattempted": 0
  },
  "status": "ACTIVE"
}

This is an example of a custom practice blueprint, not a claim about the official JEE Main pattern.

Blueprint Responsibilities

- Question count.
- Subject selection.
- Chapter weightage.
- Difficulty distribution.
- Question type distribution.
- Marks per question.
- Negative marking.
- Duration.
- Language.
- Blueprint version.

Official examination patterns should be separately verified and configured. Custom practice tests must be clearly identified as custom.

---

12. Test Generation Engine

The test engine selects questions from the approved question bank according to the student's chosen configuration.

Student Test Configuration

A student can select:

- Examination.
- Subject.
- One or multiple chapters.
- Number of questions.
- Difficulty.
- Language.
- Practice or mock test mode.

Test Generation Workflow

Student selects test configuration
              |
              v
Validate test configuration
              |
              v
Load applicable blueprint
              |
              v
Find eligible approved questions
              |
              v
Apply chapter and difficulty filters
              |
              v
Select questions without duplicates
              |
              v
Validate question availability
              |
              v
Create test session
              |
              v
Save question snapshots
              |
              v
Start examination

Important Engine Rules

- Do not select unapproved questions.
- Do not repeat a question in the same test.
- Respect the requested subject and chapter.
- Respect the selected language.
- Respect the blueprint's question distribution.
- Check question availability before creating a test.
- Report shortages instead of silently generating incomplete tests.
- Store a snapshot of selected questions and marking rules.
- Use controlled random selection rather than relying only on unrestricted random numbers.

---

13. Test Session & Evaluation

Each test session should be stored independently.

A session should contain:

- Student ID.
- Examination ID.
- Selected question IDs.
- Question snapshots.
- Blueprint version.
- Start time.
- Submission time.
- Duration.
- Student answers.
- Evaluation status.
- Final score.

Evaluation System

The evaluation service should support:

- Single-correct MCQ evaluation.
- Multiple-correct evaluation using a configured marking policy.
- Numerical answer normalization.
- Integer answer evaluation.
- Negative marking.
- Unattempted question handling.

For numerical answers, configurable tolerance may be needed.

Security requirement: Correct answers and detailed solutions must never be returned in the student question API before submission. Evaluation must happen on the server.

After submission, the result API can return the permitted answer key, explanations, and performance information.

---


14. Results & Analytics Module

Students should receive meaningful performance feedback after completing a test.

Result Information

- Total marks.
- Marks obtained.
- Correct answers.
- Incorrect answers.
- Unattempted questions.
- Accuracy percentage.
- Time taken.
- Subject-wise performance.
- Chapter-wise performance.
- Difficulty-wise performance.

Future Analytics Features

- Performance history.
- Chapter strength analysis.
- Weak-topic identification.
- Time management analysis.
- Previous test comparison.
- Personal progress dashboard.

Analytics should be based on actual submitted test data, not estimated performance.

---

15. API Structure

All backend APIs should use a consistent version prefix:

"/api/v1"

Authentication

Method| Endpoint| Description
POST| "/auth/register"| Register user
POST| "/auth/login"| Login
POST| "/auth/logout"| Logout
POST| "/auth/refresh"| Refresh token
GET| "/auth/me"| Get current user

Questions

Method| Endpoint| Description
GET| "/questions"| List questions with filters
GET| "/questions/:id"| Get permitted question details
POST| "/questions"| Create question
PATCH| "/questions/:id"| Update question
DELETE| "/questions/:id"| Archive question

Question creation and modification endpoints must be admin-protected.

Bulk Upload

Method| Endpoint| Description
POST| "/uploads/batches"| Create upload batch
POST| "/uploads/batches/:id/files"| Upload batch files
GET| "/uploads/batches/:id"| Get batch details
GET| "/uploads/batches/:id/status"| Get processing status
PATCH| "/uploads/batches/:id/questions/:questionId"| Correct extracted question
POST| "/uploads/batches/:id/approve"| Approve batch questions

Tests

Method| Endpoint| Description
POST| "/tests/generate"| Generate test
GET| "/tests/:id"| Get test session
POST| "/tests/:id/answers"| Save answers
POST| "/tests/:id/submit"| Submit test
GET| "/tests/:id/result"| Get result

Analytics

Method| Endpoint| Description
GET| "/analytics/overview"| Student overview
GET| "/analytics/subjects"| Subject-wise analysis
GET| "/analytics/chapters"| Chapter-wise analysis
GET| "/analytics/history"| Test history

These endpoints describe the intended API contract. Request schemas, response DTOs, pagination, authorization, and error codes should be documented in OpenAPI.

---

16. Database Collections

Recommended MongoDB collections:

Collection| Purpose
users| User accounts
questions| Verified question bank
subjects| Subject information
chapters| Chapter information
exams| Examination metadata
examblueprints| Configurable examination rules
uploadbatches| Bulk upload information
testsessions| Active and completed test sessions
results| Evaluation results
refreshTokens| Refresh token records
auditlogs| Important administrative actions

Database Design Rules

- Use MongoDB references where appropriate.
- Add indexes to frequently filtered fields.
- Avoid storing large image binaries in MongoDB.
- Store Cloudinary public IDs and URLs.
- Keep sensitive authentication data protected.
- Use schema validation.
- Use timestamps.
- Maintain question versions where historical test accuracy matters.

---

17. Security Architecture

Security must be considered from the beginning.

Authentication

- Hash passwords using bcrypt.
- Use short-lived access tokens.
- Rotate refresh tokens.
- Store refresh tokens securely.
- Protect private routes.

Authorization

- Implement role-based access control.
- Restrict administrative endpoints.
- Prevent students from editing questions.
- Prevent unauthorized access to other users' results.

API Security

- Helmet security headers.
- CORS allowlist.
- Rate limiting.
- Request validation.
- Input sanitization.
- Centralized error handling.
- Secure cookie configuration where cookies are used.

File Upload Security

- Validate actual file type and MIME type.
- Limit file sizes and batch sizes.
- Restrict supported file formats.
- Validate uploaded content.
- Keep Cloudinary secrets on the server.
- Use signed uploads or controlled server-side uploads.
- Prevent unauthorized file replacement.
- Never trust the original filename.

Data Security

- Never expose passwords or token secrets.
- Never send correct answers before test submission.
- Keep secrets inside environment variables.
- Avoid logging sensitive user information.
- Maintain audit logs for important admin operations.

---

18. Environment Variables

Create ".env.example" in the backend:

NODE_ENV=development
PORT=5000

CLIENT_URL=http://localhost:5173

MONGODB_URI=

JWT_ACCESS_SECRET=
JWT_REFRESH_SECRET=

JWT_ACCESS_EXPIRES_IN=15m
JWT_REFRESH_EXPIRES_IN=7d

CLOUDINARY_CLOUD_NAME=
CLOUDINARY_API_KEY=
CLOUDINARY_API_SECRET=

REDIS_URL=

LOG_LEVEL=info

Frontend ".env.example":

VITE_API_BASE_URL=http://localhost:5000/api/v1

Never commit actual ".env" files to GitHub.

---

19. API Response Format

Use a consistent response format.

Success Response

{
  "success": true,
  "message": "Test generated successfully",
  "data": {
    "testId": "example-test-id"
  }
}

Error Response

{
  "success": false,
  "message": "Invalid test configuration",
  "errors": []
}

Use appropriate HTTP status codes:

- "200" — Successful request.
- "201" — Resource created.
- "400" — Invalid request.
- "401" — Unauthorized.
- "403" — Forbidden.
- "404" — Resource not found.
- "409" — Conflict.
- "422" — Validation failure.
- "429" — Rate limit exceeded.
- "500" — Internal server error.

---

20. Development Setup

Prerequisites

Install:

- Node.js (LTS).
- npm.
- MongoDB.
- Redis (needed when background jobs are enabled).
- Git.

Clone Repository

git clone YOUR_REPOSITORY_URL
cd qurix

Install Backend Dependencies

cd server
npm install

Install Frontend Dependencies

cd ../client
npm install

Configure Environment

Create ".env" files using the ".env.example" templates.

Configure MongoDB and Cloudinary credentials.

Start Backend

cd server
npm run dev

Start Frontend

cd client
npm run dev

---

21. Recommended Backend Scripts

Example "server/package.json" scripts:

{
  "scripts": {
    "dev": "nodemon src/server.js",
    "start": "node src/server.js",
    "test": "vitest run",
    "test:watch": "vitest",
    "lint": "eslint .",
    "format": "prettier --write .",
    "seed": "node scripts/seed.js",
    "build:indexes": "node scripts/build-indexes.js"
  }
}

Install and configure the corresponding development dependencies before using these scripts.

---

22. Testing Strategy

Testing is essential for a reliable assessment platform.

Unit Tests

Test individual functions:

- Score calculation.
- Answer normalization.
- Question filtering.
- Random question selection.
- Blueprint validation.
- Numerical tolerance.

Integration Tests

Test complete backend workflows:

- User registration and login.
- Admin question creation.
- Question approval.
- Bulk upload processing.
- Test generation.
- Test submission.
- Result calculation.

End-to-End Tests

Test complete user journeys:

1. Student registers.
2. Student logs in.
3. Student selects an examination.
4. Student generates a practice test.
5. Student answers questions.
6. Student submits the test.
7. Student views the result and solutions.

Also test authorization boundaries and attempts to access another user's data.

---

23. Deployment Architecture

A practical deployment arrangement:

Component| Responsibility
Frontend hosting| React application
Backend hosting| Express API
MongoDB hosting| Application database
Cloudinary| Image and document storage
Redis hosting| Background job queue
Monitoring| Logs and application health

For production:

- Use HTTPS.
- Configure production environment variables.
- Restrict CORS to trusted origins.
- Enable database backups.
- Monitor API errors.
- Monitor background job failures.
- Configure health-check endpoints.
- Use persistent storage for required job infrastructure.
- Set up CI/CD after the basic deployment is stable.

Free-tier hosting may have sleep limits, bandwidth restrictions, database limits, or Redis restrictions. Always verify the current provider limits before selecting a deployment plan.

---

24. Development Roadmap

Phase 1 — Foundation

- Initialize React + Vite.
- Initialize Express backend.
- Connect MongoDB.
- Set up the production folder structure.
- Configure environment variables.
- Implement global error handling.
- Set up authentication.

Phase 2 — Academic Structure

- Create subjects.
- Create chapters.
- Create board metadata.
- Create examination metadata.
- Create question schemas.
- Implement admin question management.

Phase 3 — Question Bank

- Add text-based questions.
- Add LaTeX support.
- Add image-based questions.
- Add detailed solutions.
- Implement filtering and search.
- Implement question approval.

Phase 4 — Bulk Upload

- Multiple image uploads.
- PDF uploads.
- Cloudinary integration.
- Batch management.
- Background processing.
- OCR integration.
- Question grouping.
- Admin review and correction.

Phase 5 — Test Engine

- Examination blueprints.
- Custom test configuration.
- Question selection engine.
- Test session management.
- Timer and autosave.
- Answer submission.
- Evaluation engine.

Phase 6 — Results & Analytics

- Result generation.
- Detailed solutions.
- Subject-wise analytics.
- Chapter-wise analytics.
- Test history.
- Student dashboard.

Phase 7 — Production Readiness

- Unit and integration tests.
- API documentation.
- Security review.
- Database indexes.
- Performance optimization.
- Error monitoring.
- Backup strategy.
- Production deployment.

---

25. Important Engineering Decisions

1. Verified content first: Students should receive questions and solutions that have been reviewed and approved by administrators.

2. Configurable examination rules: Avoid hardcoding marking schemes, durations, or question distributions.

3. Server-side evaluation: Never trust frontend score calculations.

4. Question snapshots: Store the question and marking-rule versions used in a test session so that later edits do not change historical results.

5. Secure answer delivery: Do not expose correct answers or solutions before submission.

6. Background processing: Large file batches and OCR tasks should run through background workers rather than blocking normal API requests.

7. Admin review: OCR-extracted content must be reviewable and correctable before publication.

8. Scalable architecture: Start with a modular monolith. Introduce microservices only if actual scale and operational requirements justify it.

9. Clear test labels: Distinguish official-pattern mock tests from custom practice tests.

10. Maintainable code: Keep controllers thin, business logic in services, database operations organized, and shared infrastructure reusable.

---

26. Future Features

Potential future expansions:

- Bookmark questions.
- Custom question collections.
- Previous-year question bank.
- Timed chapter-wise practice.
- Full-length mock examinations.
- Leaderboards and rankings.
- Personal performance dashboard.
- Question reporting.
- Admin audit dashboard.
- Multi-language question support.
- Offline-friendly practice mode.
- Advanced search and filtering.
- Institution and classroom support.

---

27. Project Philosophy

Qurix is built around three core principles:

Accuracy — Educational content must be structured, verified, and reliable.

Flexibility — Different boards and examinations must be supported through configurable rules.

Scalability — The application should remain maintainable as its question bank, users, and features grow.

The goal is not simply to create another quiz application. The goal is to build a reliable academic assessment system that helps students practice effectively, understand their performance, and prepare with confidence.

---

Qurix — Practice Smarter. Understand Better. Progress Further.
