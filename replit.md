# Overview

Messe-Moment is a B2B SaaS platform that transforms physical promotional items into measurable, interactive marketing campaigns for trade show exhibitors. The platform allows marketing managers to create QR code-enabled campaigns with modular content (headers, text, quizzes, lead forms, prizes) through a visual drag-and-drop builder. Users can track engagement metrics, collect leads, and measure campaign performance in real-time.

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Frontend Architecture
- **React SPA**: Built with TypeScript using Vite as the build tool for fast development and optimized production builds
- **UI Framework**: Tailwind CSS with shadcn/ui component library for consistent, accessible design system
- **State Management**: TanStack Query for server state management and caching, React Context for authentication
- **Routing**: Wouter for lightweight client-side routing with protected route components
- **Form Handling**: React Hook Form with Zod validation for type-safe form management

## Backend Architecture
- **Node.js + Express**: RESTful API server with TypeScript for type safety
- **Authentication**: Passport.js with local strategy using bcrypt for password hashing and express-session for session management
- **Session Storage**: PostgreSQL-backed session store using connect-pg-simple
- **API Design**: RESTful endpoints with consistent error handling and request logging middleware

## Data Storage
- **Primary Database**: PostgreSQL with Drizzle ORM for type-safe database operations
- **Database Provider**: Neon serverless PostgreSQL for scalable cloud database hosting
- **Schema Design**: 
  - Users table with company information and authentication data
  - Campaigns table with publication status and unique URL slugs
  - Campaign modules table with JSONB content storage for flexible module data
  - Leads table for captured user information
  - Analytics table for tracking campaign interactions and performance metrics

## Campaign Builder System
- **Modular Architecture**: Drag-and-drop interface with predefined module types (header, text, quiz, lead_form, prize)
- **Content Storage**: JSONB fields allow flexible content structure for different module types
- **Live Preview**: Real-time smartphone simulation showing campaign appearance
- **QR Code Generation**: Server-side QR code creation for campaign access
- **Public URLs**: Unique slug-based URLs for published campaigns

## External Dependencies
- **Neon Database**: Serverless PostgreSQL hosting with connection pooling
- **QR Code Generation**: qrcode library for creating campaign QR codes
- **File Upload**: react-dropzone for drag-and-drop file uploads
- **Date Handling**: date-fns for consistent date formatting and manipulation
- **Validation**: Zod schemas for runtime type checking and API validation
- **UI Components**: Comprehensive set of Radix UI primitives wrapped in custom components

## Security & Performance
- **Authentication**: Session-based auth with secure password hashing using scrypt
- **CORS**: Configured for cross-origin requests in development
- **Environment Variables**: Database URLs and session secrets managed through environment configuration
- **Type Safety**: End-to-end TypeScript with shared schema definitions between client and server