# Product Audit AI - replit.md

## Overview

Product Audit AI is a comprehensive web application that helps product managers, founders, and analysts perform strategic product teardowns using AI-powered analysis. The application allows users to upload product screenshots or provide URLs to receive structured 8-step audit reports based on proven PM frameworks.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for development and production builds
- **Styling**: Tailwind CSS with shadcn/ui component library
- **State Management**: TanStack Query (React Query) for server state
- **Routing**: Wouter for client-side routing
- **Form Handling**: React Hook Form with Zod validation

### Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ES modules
- **File Upload**: Multer middleware for handling multipart/form-data
- **AI Integration**: OpenAI API with GPT-4 Vision for image analysis
- **Data Storage**: In-memory storage (MemStorage) with planned PostgreSQL migration

### Database Schema
- **ORM**: Drizzle ORM with PostgreSQL dialect
- **Main Entity**: `audits` table with fields:
  - `id`: Serial primary key
  - `input_type`: Type of input (upload, url, app_store)
  - `input_data`: File path, URL, or app store link
  - `additional_context`: Optional user-provided context
  - `audit_results`: JSON object containing 8-step audit analysis
  - `created_at`: Timestamp

## Key Components

### Data Models
- **Audit Result Structure**: 8-step analysis framework with each step containing:
  - Title and description
  - Detailed content analysis
  - Key insights array
  - Recommendations array
- **Summary**: Overall strengths, opportunities, risks, and final recommendation

### Frontend Components
- **FileUpload**: Drag-and-drop file upload with image validation
- **LoadingState**: Animated progress indicator for audit processing
- **AuditResults**: Expandable step-by-step audit display
- **AuditStep**: Individual audit step with collapsible content

### API Endpoints
- `POST /api/analyze-upload`: Process uploaded screenshots
- `POST /api/analyze-url`: Analyze products from URLs (planned)
- File upload handling with 10MB limit and image-only validation

## Data Flow

1. **Input Processing**: User uploads image or provides URL through React frontend
2. **File Handling**: Multer processes uploads, validates file types, and stores temporarily
3. **AI Analysis**: OpenAI GPT-4 Vision analyzes the product using structured prompts
4. **Data Storage**: Audit results stored in memory (transitioning to PostgreSQL)
5. **Results Display**: Frontend renders expandable audit steps with export options

## External Dependencies

### Core Dependencies
- **OpenAI API**: GPT-4 Vision for product analysis
- **Neon Database**: PostgreSQL hosting service
- **Radix UI**: Headless UI components for consistent design
- **Tailwind CSS**: Utility-first CSS framework

### Development Tools
- **ESBuild**: Fast JavaScript bundler for production
- **TSX**: TypeScript execution for development
- **Drizzle Kit**: Database migration and schema management

## Deployment Strategy

### Development Environment
- **Dev Server**: Vite development server with HMR
- **API Server**: Express server with file upload handling
- **Database**: Local PostgreSQL or Neon cloud database

### Production Build
- **Frontend**: Vite builds static assets to `dist/public`
- **Backend**: ESBuild bundles server code to `dist/index.js`
- **Static Serving**: Express serves built frontend assets
- **Environment Variables**: `DATABASE_URL` and `OPENAI_API_KEY` required

### Key Features
- **File Upload**: Drag-and-drop interface with image validation
- **AI Analysis**: 8-step product audit framework
- **Export Options**: PDF generation and planned Notion integration
- **Responsive Design**: Mobile-first approach with Tailwind CSS
- **Error Handling**: Toast notifications and proper error boundaries

The application is designed to be scalable and maintainable, with clear separation between frontend and backend concerns, and a well-defined API structure for future enhancements.