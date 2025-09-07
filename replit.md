# Overview

This is a full-stack web application built with Express.js backend and React frontend, featuring a calculator application. The project uses TypeScript throughout and follows modern web development practices with a monorepo structure that shares code between client and server.

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **UI Library**: Shadcn/ui components built on Radix UI primitives
- **Styling**: Tailwind CSS with CSS variables for theming
- **Routing**: Wouter for lightweight client-side routing
- **State Management**: React Query (TanStack Query) for server state management
- **Form Handling**: React Hook Form with Zod validation resolvers

## Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ES modules
- **Development**: TSX for TypeScript execution in development
- **Build**: ESBuild for production bundling
- **Storage Interface**: Abstract storage pattern with in-memory implementation

## Data Layer
- **ORM**: Drizzle ORM with PostgreSQL dialect
- **Database**: PostgreSQL (configured via Neon serverless)
- **Schema**: Centralized in shared directory with Zod validation
- **Migrations**: Drizzle Kit for schema migrations

## Development Setup
- **Monorepo Structure**: Shared code between client/server in `/shared` directory
- **Path Aliases**: TypeScript path mapping for clean imports
- **Hot Reload**: Vite HMR for frontend, TSX for backend development
- **Environment**: Replit-optimized with development banners and error overlays

## Authentication & Session Management
- **Session Store**: PostgreSQL-backed sessions using connect-pg-simple
- **User Model**: Simple username/password authentication ready

## Key Design Decisions
- **Code Sharing**: Business logic and types shared between frontend/backend via `/shared` directory
- **Component Architecture**: Radix UI primitives wrapped in custom components for consistency
- **Storage Abstraction**: Interface-based storage allows swapping between in-memory and database implementations
- **Build Strategy**: Separate build processes for client (Vite) and server (ESBuild) with optimized outputs

# External Dependencies

## Core Framework Dependencies
- **Express.js**: Web application framework
- **React**: Frontend UI library
- **Vite**: Frontend build tool and development server
- **TypeScript**: Type system for JavaScript

## UI & Styling
- **Radix UI**: Headless component primitives
- **Tailwind CSS**: Utility-first CSS framework
- **Lucide React**: Icon library
- **Class Variance Authority**: Utility for creating component variants

## Database & ORM
- **Drizzle ORM**: TypeScript ORM for PostgreSQL
- **Neon Database**: Serverless PostgreSQL provider
- **Drizzle Kit**: Database migration tool

## State Management & Forms
- **TanStack React Query**: Server state management
- **React Hook Form**: Form handling library
- **Zod**: Schema validation library

## Development Tools
- **TSX**: TypeScript execution engine
- **ESBuild**: JavaScript bundler
- **PostCSS**: CSS processing tool
- **Replit Plugins**: Development environment integration

## Session & Authentication
- **Connect PG Simple**: PostgreSQL session store for Express
- **Express Session**: Session middleware (implied by pg session store)