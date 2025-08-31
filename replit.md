# DLO Academy

## Overview

DLO Academy is a comprehensive learning management system designed to deliver accessible, mobile-first, AI-enhanced education to equip Africans with job-ready skills in energy transition, entrepreneurship, and digital economy. The platform serves young people, working adults, women in underserved communities, and employers looking to support or recruit talent.

The application features a full-stack architecture with React frontend, Express.js backend, PostgreSQL database, and comprehensive user management supporting learners, facilitators, and administrators. The platform includes course management, progress tracking, quiz systems, file uploads, and role-based dashboards.

## Featured Content
The platform's flagship course is "Just Energy Transition 101", a comprehensive 5-module program with full implementation including:

### Course Structure (8-10 hours total)
- **Module 1**: Introduction to JET fundamentals and African energy context
- **Module 2**: The Five Pillars of JET framework with interconnection analysis
- **Module 3**: South Africa's REIPPPP case study with real data and policy lessons
- **Module 4**: Energy value chains comparison with interactive video lesson
- **Module 5**: Career opportunities and personal action plan development

### Interactive Features
- **AI Tutor Naledi**: Context-aware learning support throughout all modules
- **Quiz System**: JSON-based assessments with immediate feedback and explanations
- **Scenario Assignments**: Real-world application exercises for each module
- **Video Integration**: Documentary content with pause points and reflection prompts
- **Action Planning**: Personalized career development and local involvement planning

### Technical Implementation
- Standalone LMS structure (`/lms/`, `/ai/`, `/data/`) served via static routes with authentication protection
- Light theme optimized learning interface matching platform design with mobile responsiveness
- Sectioned content delivery preventing information overload with interactive navigation
- Progress tracking and completion status management
- Integrated AI chat system for real-time learning support
- Interactive visual elements with energy and learning-focused imagery

## Recent Changes

### Deployment Fixes (January 31, 2025)
- Fixed premature process exit after database seeding completes
- Removed problematic infinite promise blocking main function execution
- Simplified process management to prevent deployment health check failures
- Created deployment build scripts to ensure static files are properly positioned
- Added post-build automation to copy static assets for production serving
- Resolved "Service Unavailable" deployment errors by ensuring server/public directory exists
- Fixed production static file serving by running: `npm run build && node scripts/post-build.js`
- Moved database seeding to background tasks to prevent blocking health checks
- Added ultra-fast health check endpoints (/health, /healthz, /ready, /ping) for deployment compatibility

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript using Vite as the build tool
- **Routing**: Wouter for client-side routing with role-based route protection
- **UI Framework**: Tailwind CSS with shadcn/ui component library following "new-york" style
- **State Management**: TanStack Query for server state management and caching
- **Form Handling**: React Hook Form with Zod validation schemas
- **Design System**: Custom color scheme with gold (#FFD700) primary color, Inter/Poppins typography

### Backend Architecture
- **Runtime**: Node.js with Express.js framework and TypeScript
- **API Design**: RESTful API with comprehensive CRUD operations for courses, users, enrollments
- **Database ORM**: Drizzle ORM with PostgreSQL as the database engine
- **Authentication**: Replit Auth integration with OpenID Connect and session management
- **File Upload**: Uppy integration with AWS S3 for file storage and management
- **Middleware**: Express session management, CORS handling, request logging

### Database Design
- **Primary Database**: PostgreSQL with Neon serverless driver
- **Schema Management**: Drizzle Kit for migrations and schema management
- **Key Entities**: Users (learners/facilitators/admins), Courses, Modules, Enrollments, Quiz Questions/Attempts, Reviews
- **Relationships**: Comprehensive foreign key relationships between courses, users, and progress tracking
- **Session Storage**: PostgreSQL-backed session store for authentication persistence

### Authentication & Authorization
- **Provider**: Replit Auth with OpenID Connect flow supporting multiple login options (Gmail, GitHub, etc.)
- **Session Management**: PostgreSQL-backed session storage with 7-day TTL
- **Role-Based Access**: Three-tier system (learner, facilitator, admin) with route-level protection
- **User Management**: Automatic user creation/updates via OAuth flow
- **Login Options**: Gmail and other OAuth providers available through Replit Auth interface

### File Storage & Management
- **Storage Provider**: Google Cloud Storage with Replit sidecar integration
- **Upload Interface**: Uppy dashboard with AWS S3 upload strategy
- **Access Control**: Custom ACL system with object-level permissions
- **File Organization**: Structured paths with public/private access controls

## External Dependencies

### Core Dependencies
- **@neondatabase/serverless**: PostgreSQL serverless database connectivity
- **drizzle-orm**: Type-safe database ORM and query builder
- **@tanstack/react-query**: Server state management and caching
- **@radix-ui/react-***: Headless UI components for accessible interface elements
- **@uppy/core, @uppy/aws-s3**: File upload handling with cloud storage integration

### Authentication & Session Management
- **openid-client**: OpenID Connect authentication flow
- **passport**: Authentication middleware integration
- **express-session**: Session management middleware
- **connect-pg-simple**: PostgreSQL session store adapter

### UI & Styling
- **tailwindcss**: Utility-first CSS framework
- **class-variance-authority**: Type-safe variant styling system
- **lucide-react**: Icon library for consistent visual elements
- **wouter**: Lightweight client-side routing

### Development & Build Tools
- **vite**: Modern build tool and development server
- **typescript**: Static type checking across frontend and backend
- **@replit/vite-plugin-runtime-error-modal**: Development error handling
- **tsx**: TypeScript execution for server development

### External Services
- **Google Cloud Storage**: Object storage for file management
- **Replit Auth**: Authentication service integration
- **Neon Database**: Serverless PostgreSQL hosting