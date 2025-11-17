# project-instructions.md

## CourseHub - Angular LMS

### Chosen stack (project-wide)
- Frontend: Angular 18 (TypeScript, HTML, CSS/SCSS)
- Backend: Python (recommended: FastAPI for a modern async API)
- Database: MongoDB (NoSQL, document store)

Rationale: Angular 18 provides a robust frontend framework with strong TypeScript support. FastAPI pairs well with async MongoDB drivers (e.g., motor) and Pydantic for data validation. MongoDB fits the flexible document structure for courses and user progress.

### General Workflow
- Each developer works on a separate branch (`frontend` or `backend`).
- Pull latest `main` before starting work.
- Follow instructions step by step for each screen/component.
- Update this file if workflow or architecture changes.

### Project Structure
- **Modules:**
  - AuthModule (login, registration, guards)
  - CoursesModule (list, details, create/edit)
  - UsersModule (profile, enrollment, dashboard)
  - AdminModule (course & user management, analytics)
  - SharedModule (common components, directives, pipes)
  - CoreModule (singleton services)
- **Lazy-loading:** All feature modules should be lazy-loaded.
- **Routing:** Hierarchical with dynamic parameters.

### Branch Responsibilities
| Branch   | Responsibility                                                   |
| -------- | ---------------------------------------------------------------- |
| frontend | UI components, screens, styling, animations, data binding, forms |
| backend  | Python backend (FastAPI recommended): API, business logic, auth  |
| database | MongoDB: collections, indexes, seed data                         |

### Frontend Tasks (Angular 18)
- Create components screen by screen (`CourseList`, `CourseCard`, `CourseDetails`, `Dashboard`).
- Implement all types of data binding: interpolation, property, event, two-way.
- Directives: `*ngFor`, `*ngIf`, `ngClass`, `ngStyle`, custom directives.
- Forms:
  - Template-driven with validation and reset
  - Reactive with FormBuilder, custom & async validators, FormArray
- Animations: route transitions, list animations, buttons, highlight animations
- Communication: `@Input`, `@Output`, Content Projection, lifecycle hooks (`ngOnInit`, `ngOnChanges`, `ngAfterViewInit`, `ngOnDestroy`)

### Backend / Services Tasks (Python + FastAPI recommended)
- Implement API endpoints for courses, users, enrollments, progress.
- Use an async MongoDB driver (motor) or ODM (e.g., Beanie) with Pydantic models.
- Authentication: JWT-based auth (login/refresh), password hashing (bcrypt).
- Services: CoursesService, AuthService, UserService (as Python modules/classes).
- Integrate with Angular via clear REST endpoints and consistent JSON shapes.
- Error handling: return standard HTTP status codes and structured error bodies.

Recommended Python packages:
- fastapi
- uvicorn
- motor (async MongoDB driver) or beanie (async ODM)
- pydantic
- python-jose or pyjwt (JWT handling)
- passlib[bcrypt] (password hashing)

### Database Tasks (MongoDB)
- Collections: courses, users, enrollments, progress
- Use indexes for frequently queried fields (e.g., course.slug, users.email)
- Seed sample data via a script that inserts JSON documents.

Sample collection documents (examples)

- courses (collection name: `courses`)

```json
{
  "_id": "ObjectId(...)",
  "title": "Intro to Angular",
  "slug": "intro-to-angular",
  "description": "...",
  "instructorId": "ObjectId(...)",
  "tags": ["angular","frontend"],
  "createdAt": "2025-11-17T...Z",
  "lessons": [ { "title": "Lesson 1", "duration": 600 } ]
}
```

- users (collection name: `users`)

```json
{
  "_id": "ObjectId(...)",
  "email": "student@example.com",
  "name": "Student Name",
  "passwordHash": "...",
  "roles": ["student"],
  "createdAt": "2025-11-17T...Z"
}
```

- enrollments (collection name: `enrollments`)

```json
{
  "_id": "ObjectId(...)",
  "userId": "ObjectId(...)",
  "courseId": "ObjectId(...)",
  "enrolledAt": "2025-11-17T...Z",
  "status": "active"
}
```

- progress (collection name: `progress`)

```json
{
  "_id": "ObjectId(...)",
  "userId": "ObjectId(...)",
  "courseId": "ObjectId(...)",
  "lessonId": "...",
  "completed": true,
  "updatedAt": "2025-11-17T...Z"
}
```

### Guards & Routing
- AuthGuard for protected frontend routes
- CanDeactivate for unsaved forms
- Route Resolver to preload course data
- Dynamic routes for course details (`/courses/:id`)

### API - minimal recommended endpoints (example)
- POST /api/auth/login -> { access_token }
- POST /api/auth/register -> create user
- GET /api/courses -> list courses (filter, pagination)
- GET /api/courses/{id} -> course details
- POST /api/courses -> create course (admin/instructor)
- PUT /api/courses/{id} -> update course
- POST /api/courses/{id}/enroll -> enroll current user
- GET /api/users/{id}/progress -> user progress

### Testing
- Unit tests: backend services (pytest + HTTPX/testclient for FastAPI), frontend components (Jest/Karma/Angular TestBed)
- Integration tests: API endpoints
- E2E tests: full user flows: login → browse → enroll → logout (Cypress/Playwright)

### TODO (step-by-step setup instructions)
1. Frontend (Angular 18)
   - Install Node.js (LTS) and npm.
   - Create app: `ng new coursehub --routing --style=scss` (ensure Angular CLI matching v18).
   - Add modules and lazy-load feature modules as listed in this file.
   - Use Angular HttpClient to talk to the Python API.

2. Backend (Python + FastAPI)
   - Create a Python virtual environment.
   - Install dependencies (example):

```
pip install fastapi uvicorn motor pydantic python-jose passlib[bcrypt]
```

   - Implement Pydantic models and FastAPI routers for the endpoints above.
   - Connect to MongoDB (local or hosted) with motor.

3. Database (MongoDB)
   - Run MongoDB locally (or use Atlas).
   - Create a `seed` script (Python) to insert sample documents for `courses`, `users`, `enrollments`, `progress`.

4. Run locally (development)
   - Start MongoDB.
   - Run backend: `uvicorn app.main:app --reload --port 8000`.
   - Run frontend: `ng serve --open` (default port 4200) and configure proxy to /api -> http://localhost:8000 if desired.

5. CI / Deployment
   - Provide a GitHub Actions workflow that builds the frontend, runs backend tests, and deploys to chosen hosting (VPS, AWS/GCP, or container registry).

### Optional Enhancements
- Use Beanie (async ODM) to get Pydantic + MongoDB models and migrations conveniences.
- Add refresh tokens and role-based authorization.
- Add indexing and TTL where appropriate for logs/sessions.

### AI Workflow (Copilot / Claude)
- Copy instructions from this file
- Work screen by screen, approve AI suggestions
- Open a new session per screen to avoid token overflow

### Optional Enhancements
- NgRx for advanced state management
- Service workers for offline support
- CI/CD pipeline with GitHub Actions
