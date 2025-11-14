# Flash Game Library

## Overview

A retro-styled web application for browsing and playing classic Flash games using Ruffle emulator. The application features a nostalgic design inspired by early 2000s Flash gaming portals (Newgrounds, Miniclip, Kongregate) while maintaining modern web standards and UX patterns.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework**: React with TypeScript, built using Vite as the build tool and development server.

**Routing**: Wouter for lightweight client-side routing with two main routes:
- `/` - Game library view displaying all available games in a grid
- `/play/:filename` - Game player view for running individual Flash games

**UI Component System**: shadcn/ui components (New York style) providing a comprehensive set of pre-built, accessible React components built on Radix UI primitives. Components are styled using Tailwind CSS with custom design tokens.

**State Management**: TanStack Query (React Query) for server state management, handling API requests and caching game data.

**Styling Approach**: 
- Tailwind CSS for utility-first styling
- Custom CSS variables for theming (light mode with retro aesthetic)
- Typography system using "Press Start 2P" pixel font for headings/game titles and system font stack for body text
- Responsive grid layouts with mobile-first breakpoints
- Hover and active elevation effects for interactive elements

### Backend Architecture

**Server Framework**: Express.js running on Node.js with TypeScript.

**API Design**: RESTful endpoints serving JSON responses:
- `GET /api/games` - Returns list of available Flash games with metadata
- Static file serving for `.swf` game files from `/games` directory

**Storage Strategy**: File-system based storage using `MemStorage` class that scans the local `games` directory for `.swf` files. Game metadata (filename, display name, file size, path) is dynamically generated from filesystem inspection rather than stored in a database.

**Rationale**: Filesystem-based approach chosen for simplicity and direct access to game files. This eliminates database dependencies for the core functionality while maintaining flexibility to add database support later if needed (schema is already defined using Drizzle ORM).

### Data Storage

**Current Implementation**: No active database - games are served directly from the filesystem.

**Prepared Database Schema**: Drizzle ORM schema defined with PostgreSQL dialect for potential future use:
- `games` table with fields: id, filename, displayName, path, size
- Schema uses Neon Database serverless driver (`@neondatabase/serverless`)
- Migration configuration ready in `drizzle.config.ts`

**Session Management**: Connect-pg-simple available for PostgreSQL-backed sessions if authentication is added.

### Flash Game Emulation

**Emulator**: Ruffle (loaded via CDN script) - a Flash Player emulator written in Rust compiled to WebAssembly.

**Integration Pattern**: 
- Ruffle player instance created dynamically when loading a game
- Game SWF files loaded asynchronously via URL
- Player controls include fullscreen toggle, reload functionality, and navigation back to library

### External Dependencies

**Core Runtime**:
- Ruffle Flash emulator (loaded from unpkg.com CDN)
- React 18+ for UI rendering
- Express.js for HTTP server

**UI Component Libraries**:
- Radix UI primitives (accordion, dialog, dropdown, tooltip, etc.)
- Embla Carousel for potential carousel features
- Lucide React for icon system

**Build & Development Tools**:
- Vite for fast development and optimized production builds
- TypeScript for type safety
- Tailwind CSS + PostCSS for styling
- esbuild for server-side bundling

**Database (Configured but Not Active)**:
- Drizzle ORM for type-safe database queries
- PostgreSQL via Neon Database serverless driver
- drizzle-kit for schema migrations

**Validation & Forms**:
- Zod for schema validation
- drizzle-zod for database schema to Zod conversion
- React Hook Form with Hookform Resolvers for form handling

**Utilities**:
- date-fns for date formatting
- clsx + tailwind-merge for conditional class merging
- class-variance-authority for component variant management

**Development Tools (Replit-specific)**:
- @replit/vite-plugin-runtime-error-modal for error overlay
- @replit/vite-plugin-cartographer for code mapping
- @replit/vite-plugin-dev-banner for development indicator