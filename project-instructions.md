# project-instructions.md

## CourseHub - Angular LMS

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
| backend  | Services, API integration, state management, HTTP requests       |
| database | Tables, relationships, seed data                                 |

### Frontend Tasks
- Create components screen by screen (`CourseList`, `CourseCard`, `CourseDetails`, `Dashboard`).
- Implement all types of data binding: interpolation, property, event, two-way.
- Directives: `*ngFor`, `*ngIf`, `ngClass`, `ngStyle`, custom directives.
- Forms:
  - Template-driven with validation and reset
  - Reactive with FormBuilder, custom & async validators, FormArray
- Animations: route transitions, list animations, buttons, highlight animations
- Communication: `@Input`, `@Output`, Content Projection, lifecycle hooks (`ngOnInit`, `ngOnChanges`, `ngAfterViewInit`, `ngOnDestroy`)

### Backend / Services Tasks
- CoursesService, AuthService, UserService
- CRUD operations via HttpClient
- RxJS: Observables, Subjects, BehaviorSubjects, operators (`map`, `switchMap`, `catchError`)
- HTTP Interceptors: auth headers and global error handling
- Loading spinner service

### Database Tasks
- Tables: Courses, Users, Enrollments, Progress
- Relationships & foreign keys
- Seed sample data

### Guards & Routing
- AuthGuard for protected routes
- CanDeactivate for unsaved forms
- Route Resolver to preload course data
- Dynamic routes for course details (`/courses/:id`)

### Testing
- Unit tests: services, pipes, validators
- Component tests: rendering, forms, service interaction
- E2E tests: full user flows: login → browse → enroll → logout

### AI Workflow (Copilot / Claude)
- Copy instructions from this file
- Work screen by screen, approve AI suggestions
- Open a new session per screen to avoid token overflow

### Optional Enhancements
- NgRx for advanced state management
- Service workers for offline support
- CI/CD pipeline with GitHub Actions
