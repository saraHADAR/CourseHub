# CourseHub - Advanced Angular LMS

## Project Overview
CourseHub is an advanced Angular 18+ learning management system designed for interactive learning. It provides:

- Admin panel and user management.
- Lazy-loaded modules, dynamic routing, guards, and resolvers.
- Advanced forms (template-driven & reactive).
- RxJS for state management and HTTP API communication.
- Animations, custom pipes, and performance optimizations.

## Key Features
- **Authentication:** JWT login/logout, role-based access, password reset.
- **Course Management:** Browse, search, course details, create/edit courses, enrollment system.
- **Admin Panel:** User & course management, analytics dashboard.
- **User Dashboard:** View enrolled courses, track progress, manage profile.

## Project Structure
- **Modules:** AuthModule, CoursesModule, UsersModule, AdminModule, SharedModule, CoreModule
- **Services:** CoursesService, AuthService, UserService
- **Components:** CourseList, CourseCard, CourseDetails, Dashboard, Forms
- **Database:** Courses, Users, Enrollments, Progress

## Installation
```bash
git clone <repo-url>
cd CourseHub
npm install
ng serve
