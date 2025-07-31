# MedTime - Medication Reminder Application

## Overview

MedTime is a full-stack medication reminder application built with React, TypeScript, Express, and PostgreSQL. The application helps users track their medications and receive timely reminders to take them. It features a modern UI built with shadcn/ui components and Tailwind CSS, user authentication through Replit Auth, and a comprehensive medication management system.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **Routing**: Wouter for lightweight client-side routing
- **State Management**: TanStack Query (React Query) for server state management
- **UI Framework**: shadcn/ui components built on Radix UI primitives
- **Styling**: Tailwind CSS with CSS variables for theming
- **Form Handling**: React Hook Form with Zod validation

### Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ES modules
- **Database ORM**: Drizzle ORM with PostgreSQL dialect
- **Authentication**: Replit Auth with OpenID Connect
- **Session Management**: Express sessions with PostgreSQL store
- **API Pattern**: RESTful API with JSON responses

### Database Design
- **Primary Database**: PostgreSQL (configured for Neon serverless)
- **Schema Management**: Drizzle Kit for migrations and schema management
- **Key Tables**:
  - `users`: User profiles and authentication data
  - `medicines`: Medication information and scheduling
  - `medicine_reminders`: Individual reminder instances
  - `sessions`: Session storage for authentication

## Key Components

### Authentication System
- **Provider**: Replit Auth using OpenID Connect
- **Session Storage**: PostgreSQL-backed sessions with connect-pg-simple
- **Authorization**: Middleware-based route protection
- **User Management**: Automatic user creation/updates on login

### Medication Management
- **CRUD Operations**: Full create, read, update, delete for medications
- **Scheduling**: Flexible timing system with multiple daily doses
- **Validation**: Zod schemas for type-safe data validation
- **User Isolation**: All data scoped to authenticated users

### Reminder System
- **Generation**: Automated reminder creation based on medication schedules
- **Notifications**: Browser notification API integration
- **Status Tracking**: Mark reminders as taken/missed
- **Time-based Queries**: Today's reminders and upcoming notifications

### UI Components
- **Design System**: Consistent component library with shadcn/ui
- **Responsive Design**: Mobile-first approach with Tailwind CSS
- **Accessibility**: Built on Radix UI for keyboard navigation and screen readers
- **Theming**: CSS custom properties for light/dark mode support

## Data Flow

1. **Authentication Flow**:
   - User clicks login → Redirected to Replit OAuth
   - Successful auth → User data stored/updated in database
   - Session created → User can access protected routes

2. **Medication Management Flow**:
   - User creates medication → Validated and stored in database
   - Reminders auto-generated → Individual reminder records created
   - User views schedule → Data fetched and displayed by date/time

3. **Notification Flow**:
   - Background service checks for due reminders
   - Browser notifications sent for upcoming doses
   - User marks as taken → Reminder status updated

## External Dependencies

### Core Framework Dependencies
- **React Ecosystem**: React, React DOM, React Hook Form
- **Build Tools**: Vite, TypeScript, ESBuild for production builds
- **Database**: Drizzle ORM, @neondatabase/serverless, PostgreSQL driver
- **Authentication**: Passport.js, OpenID Client, Express Session

### UI Dependencies
- **Component Library**: Extensive Radix UI primitives collection
- **Styling**: Tailwind CSS, Class Variance Authority, CLSX
- **Icons**: Lucide React for consistent iconography
- **Utilities**: Date-fns for date manipulation, Zod for validation

### Development Dependencies
- **Type Safety**: TypeScript definitions for all major libraries
- **Development Tools**: Replit-specific plugins for enhanced development experience

## Deployment Strategy

### Development Environment
- **Runtime**: Node.js with tsx for TypeScript execution
- **Hot Reload**: Vite development server with HMR
- **Database**: Environment variable-based connection to PostgreSQL
- **Session Secret**: Environment-based session configuration

### Production Build
- **Frontend**: Vite builds static assets to `dist/public`
- **Backend**: ESBuild bundles server code to `dist/index.js`
- **Database**: Drizzle migrations applied via `db:push` command
- **Environment**: Production-ready Express server with static file serving

### Configuration Requirements
- `DATABASE_URL`: PostgreSQL connection string
- `SESSION_SECRET`: Secure session encryption key
- `REPL_ID`: Replit environment identifier for OAuth
- `ISSUER_URL`: OAuth provider URL (defaults to Replit)

The application follows a monorepo structure with clear separation between client, server, and shared code, making it maintainable and scalable for a medication reminder system.