# Course Enrollment Platform - Skill Shikhun

## Overview

This is a full-stack web application for an online course platform called "Skill Shikhun" (meaning "Learn Skills" in Bengali). The platform allows users to browse courses, view course details, and enroll in courses through a multi-step enrollment process with phone verification.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter (lightweight React router)
- **State Management**: TanStack Query (React Query) for server state
- **Styling**: Tailwind CSS with custom design system
- **UI Components**: Radix UI primitives with shadcn/ui component library
- **Build Tool**: Vite for fast development and optimized builds

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Runtime**: Node.js with ES modules
- **Database ORM**: Drizzle ORM with PostgreSQL
- **Database Provider**: Neon Database (serverless PostgreSQL)
- **Session Management**: PostgreSQL-based sessions with connect-pg-simple
- **Development**: Hot module replacement with Vite integration

### Monorepo Structure
The application uses a monorepo structure with clear separation:
- `client/` - React frontend application
- `server/` - Express.js backend API
- `shared/` - Shared TypeScript schemas and types
- Root configuration files for tools and deployment

## Key Components

### Database Schema
- **Users**: Basic user authentication (username/password)
- **Courses**: Course information including title, description, price, duration, images
- **Enrollments**: Student enrollment records with contact information
- **Testimonials**: Student reviews and feedback

### Frontend Features
- **Course Catalog**: Interactive course grid with filtering and display
- **Course Details**: Individual course pages with enrollment capability
- **Enrollment Modal**: Multi-step enrollment process with phone verification
- **Responsive Design**: Mobile-first responsive layout
- **Bengali Language Support**: Full Bengali language interface

### API Endpoints
- `POST /api/enrollments` - Process course enrollments with validation
- `GET /api/courses` - Retrieve course catalog data
- Input validation using Zod schemas from shared types

## Data Flow

1. **Course Display**: Static course data served from backend API
2. **Enrollment Process**: 
   - User clicks on course → opens enrollment modal
   - Multi-step form collection (phone, OTP verification, personal details)
   - Form validation using shared Zod schemas
   - Enrollment submission to backend API
3. **Database Operations**: Drizzle ORM handles PostgreSQL operations with type safety

## External Dependencies

### Database & Infrastructure
- **Neon Database**: Serverless PostgreSQL hosting
- **Drizzle Kit**: Database migration and schema management

### UI & Styling
- **Tailwind CSS**: Utility-first CSS framework
- **Radix UI**: Headless UI components for accessibility
- **Lucide React**: Icon library for consistent iconography
- **Google Fonts**: Poppins and Noto Sans Bengali fonts

### Development Tools
- **TypeScript**: Type safety across the full stack
- **Vite**: Fast build tool with HMR
- **ESBuild**: JavaScript bundling for production
- **PostCSS**: CSS processing with Tailwind

## Deployment Strategy

### Build Process
- Frontend built with Vite to `dist/public/`
- Backend bundled with ESBuild to `dist/index.js`
- Shared schemas compiled for both environments

### Environment Configuration
- Database connection via `DATABASE_URL` environment variable
- Development vs production environment detection
- Replit-specific optimizations and debugging tools

### Development Workflow
- `npm run dev` - Start development server with HMR
- `npm run build` - Production build
- `npm run start` - Production server
- `npm run db:push` - Apply database schema changes

The architecture emphasizes type safety, developer experience, and scalability while maintaining a clean separation between frontend and backend concerns. The shared schema approach ensures consistency between client and server validation.

## Vercel Deployment Configuration

### Added Files for Vercel Support
- **vercel.json**: Main deployment configuration with serverless function setup
- **api/index.js**: Serverless function entry point wrapping Express app
- **.vercelignore**: Optimization file to exclude unnecessary files from deployment
- **build-vercel.js**: Automated build script with verification and error handling
- **deploy-guide.md**: Complete step-by-step deployment guide in Bengali

### Deployment Features
- **Serverless API**: Express backend converted to Vercel serverless functions
- **Static Frontend**: React app served as static files from CDN
- **Automatic HTTPS**: SSL certificates and custom domain support
- **Environment Variables**: Production configuration support
- **Error Handling**: Comprehensive build verification and troubleshooting

### Build Process for Vercel
1. Frontend built with Vite to `dist/public/`
2. Backend bundled with ESBuild for serverless deployment
3. API wrapper created for Vercel Functions
4. Static assets optimized for CDN delivery

The project is now fully Vercel-compatible with automated deployment pipeline.