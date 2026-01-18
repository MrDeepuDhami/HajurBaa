# Hajur Baa - AI Chatbot Application

## Overview

Hajur Baa is a next-generation AI chatbot application designed to provide an emotional, respectful, and calm digital presence. The name "Hajur Baa" means grandfather in Nepali, and the AI embodies the wisdom, patience, and warmth of a beloved elder figure. The application features a thoughtful onboarding experience, conversation management, and streaming AI responses with a distinctive personality that speaks primarily in Nepali.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter (lightweight React router)
- **State Management**: TanStack React Query for server state
- **Styling**: Tailwind CSS with shadcn/ui component library
- **Build Tool**: Vite with hot module replacement
- **Theme**: Custom light/dark mode with CSS variables, featuring calm blue tones

### Backend Architecture
- **Runtime**: Node.js with Express 5
- **Language**: TypeScript with ESM modules
- **API Style**: RESTful endpoints with streaming support for AI responses
- **AI Integration**: OpenAI API via Replit AI Integrations (environment variables `AI_INTEGRATIONS_OPENAI_API_KEY` and `AI_INTEGRATIONS_OPENAI_BASE_URL`)

### Data Storage
- **Storage**: In-memory storage (MemStorage) for conversations and messages
- **Schema Location**: `shared/schema.ts` with Zod validation schemas
- **Note**: Data persists only during the server session; use PostgreSQL for permanent storage if needed

### Key Design Patterns
- **Monorepo Structure**: Client code in `client/`, server in `server/`, shared types in `shared/`
- **Path Aliases**: `@/*` for client source, `@shared/*` for shared modules
- **Storage Abstraction**: Interface-based storage pattern (`IStorage`) allowing in-memory or database backends
- **Streaming Responses**: Server-Sent Events (SSE) for real-time AI message streaming
- **Component Library**: shadcn/ui components with Radix UI primitives

### Application Pages
- `/` - Main home page with 3-second delayed UI, hamburger menu (About/Contacts), and action buttons (Chat with Hajur Baa, New Chat, Chat History)
- `/chat/:id` - Individual conversation view with streaming messages, hamburger menu drawer for navigation and chat history management
- `/about` - Information about Hajur Baa
- `/contact` - Creator contact information

### User Sessions
- Each visitor is identified by a unique cookie (`hajurbaa_user`)
- Users only see their own chat history
- Sessions persist for 1 year

## External Dependencies

### AI Services
- **OpenAI API**: Primary AI backend accessed through Replit AI Integrations
- **Model**: Uses OpenAI-compatible endpoints for chat completions with streaming

### Database
- **PostgreSQL**: Primary database via `DATABASE_URL` environment variable
- **Session Storage**: connect-pg-simple for Express sessions

### Audio Processing (Available Integration)
- **FFmpeg**: Required for WebM to WAV audio conversion
- **Speech-to-Text/Text-to-Speech**: OpenAI Whisper and TTS capabilities available in `server/replit_integrations/audio/`

### Frontend Libraries
- **Radix UI**: Accessible component primitives
- **date-fns**: Date formatting utilities
- **Zod**: Runtime type validation with drizzle-zod integration
- **react-icons**: Icon library for social media icons

### Build & Development
- **esbuild**: Server-side bundling for production
- **tsx**: TypeScript execution for development
- **PostCSS/Autoprefixer**: CSS processing pipeline