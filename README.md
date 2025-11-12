# project-instructions.md

## CourseHub - Angular LMS

### General Workflow

- Each developer creates a separate branch: `frontend` and `backend`.
- Use GitHub for version control, pull latest `main` before starting tasks.
- Follow instructions step-by-step for each screen/component.
- Update this file if there are changes in workflow or architecture.

### Project Structure

- **Modules**:
  - AuthModule (login, registration, guards)
  - CoursesModule (list, details, create/edit)
  - UsersModule (profile, enrollment, dashboard)
  - AdminModule (course & user management, analytics)
  - SharedModule (common components, directives, pipes)
  - CoreModule (singleton services)
- **Lazy-loading**: Each feature module should be lazy-loaded.
- **Routing**: Hierarchical routes with dynamic parameters.

### Branch Responsibilities

| Branch   | Responsibility                                                   |
| -------- | ---------------------------------------------------------------- |
| frontend | UI components, screens, styling, animations, data binding, forms |
| backend  | Services, API integration, state management, HTTP requests       |
| database | Tables, relationships, seed data                                 |

### Frontend Tasks

- Create components screen by screen (`CourseList`, `CourseCard`, `CourseDetails`, `Dashboard`).
- Implement all data binding types: interpolation, property, event, two-way.
- Add directives: `*ngFor`, `*ngIf`, `ngClass`, `ngStyle`, custom directives.
- Forms:
  - Template-driven forms with validation and reset.
  - Reactive forms with FormBuilder, custom & async validators, FormArray.
- Animations: route transitions, list animations, buttons, highlight animations.
- Communication: `@Input`, `@Output`, Content Projection, lifecycle hooks (`ngOnInit`, `ngOnChanges`, `ngAfterViewInit`, `ngOnDestroy`).

### Backend / Services Tasks

- CoursesService, AuthService, UserService.
- CRUD operations via HttpClient.
- RxJS: Observables, Subjects, BehaviorSubjects, operators (map, switchMap, catchError).
- HTTP Interceptors for auth headers and global error handling.
- Loading spinner service.

### Database Tasks

- Tables: Courses, Users, Enrollments, Progress.
- Relationships & foreign keys.
- Seed sample data.

### Guards & Routing

- AuthGuard for protected routes.
- CanDeactivate for unsaved forms.
- Route Resolver to preload course data.
- Dynamic routes for course details (`/courses/:id`).

### Testing

- Unit tests: services, pipes, validators.
- Component tests: rendering, forms, service interaction.
- E2E tests: user flow login → browse → enroll → logout.

### AI Workflow (Copilot / Claude)

- Copy instructions from this file.
- Work screen by screen, approve AI suggestions.
- Open new session per screen to avoid token overflow.

### Optional Enhancements

- NgRx for advanced state management.
- Service workers for offline support.
- CI/CD pipeline with GitHub Actions.


# README.md

## CourseHub - Advanced Angular LMS

### Project Overview

CourseHub is an advanced Angular 18+ learning management system that includes:

- Admin panel and user management.
- Lazy-loaded modules, dynamic routing, guards, resolvers.
- Advanced forms (template-driven & reactive).
- RxJS state management, HTTP API communication.
- Animations, custom pipes, directives, and performance optimizations.

### Features

- **Authentication:** JWT login/logout, role-based access, password reset.
- **Course Management:** Browse, search, details, create/edit courses, enrollment cart.
- **Admin Panel:** Manage users, courses, analytics dashboard.
- **User Dashboard:** View enrolled courses, progress tracking, profile management.

### Project Structure

- **Modules:** AuthModule, CoursesModule, UsersModule, AdminModule, SharedModule, CoreModule.
- **Services:** CoursesService, AuthService, UserService.
- **Components:** CourseList, CourseCard, CourseDetails, Dashboard, Forms.
- **Database:** Courses, Users, Enrollments, Progress.

### Installation

```bash
git clone <repo-url>
cd CourseHub
npm install
ng serve
