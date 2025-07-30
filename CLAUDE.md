# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

### Essential Commands
- `npm install` - Install dependencies
- `npm start` - Run the Electron app locally  
- `npm run dev:engine` - Run with local engine at http://localhost:8080/v1
- `npm run staging:engine` - Run with staging engine
- `npm run staging:gateway` - Run with staging gateway

### Build & Package
- `npm run package` - Package the Electron app
- `npm run make` - Create distributable packages
- `npm run publish` - Publish the app

### Code Quality
- `npm run ts` - Run TypeScript checks (both main and workers)
- `npm run ts:main` - TypeScript check for main process
- `npm run ts:workers` - TypeScript check for workers
- `npm run lint` - Run oxlint with auto-fix
- `npm run lint:fix` - Run oxlint with aggressive fixes
- `npm run prettier` - Format code with Prettier
- `npm run presubmit` - Run prettier check and lint

### Testing
- `npm test` - Run Vitest tests
- `npm run test:watch` - Run Vitest in watch mode
- `npm run test:ui` - Run Vitest with UI
- `npm run e2e` - Run Playwright end-to-end tests
- `npm run pre:e2e` - Build for E2E tests

### Database
- `npm run db:generate` - Generate Drizzle schema
- `npm run db:push` - Push schema changes to database
- `npm run db:studio` - Open Drizzle Studio

## Architecture Overview

Dyad is an Electron-based AI app builder with these key architectural components:

### Core Structure
- **Main Process** (`src/main.ts`): Electron main process, handles system-level operations
- **Renderer Process** (`src/renderer.tsx`): React frontend using TanStack Router
- **Preload Script** (`src/preload.ts`): Secure bridge between main and renderer processes

### IPC Communication Pattern
The app follows a structured IPC pattern for secure communication between processes:

- **IPC Client** (`src/ipc/ipc_client.ts`): Renderer-side interface for calling main process functions
- **IPC Host** (`src/ipc/ipc_host.ts`): Main process IPC handler registration
- **IPC Handlers** (`src/ipc/handlers/`): Specific handlers for different functionality areas
- **IPC Types** (`src/ipc/ipc_types.ts`): Type definitions for IPC communication

### Key Principles from Cursor Rules
- Use TanStack Router (NOT Next.js or React Router)
- Follow the IPC + React Query pattern for data fetching and mutations
- Error handling: Main process handlers MUST `throw new Error("message")` on failures
- Use `withLock(appId, async () => {})` for operations that modify shared resources
- TanStack Query handles error propagation with `showErrorToast: true` meta option

### Data Layer
- **Database**: SQLite with Drizzle ORM (`src/db/schema.ts`)
- **State Management**: Jotai atoms (`src/atoms/`) + TanStack Query for server state
- **Local Storage**: Electron's userData directory for app data and user settings

### Key Directories
- `src/components/` - React components, including chat UI and preview panels
- `src/hooks/` - Custom React hooks, many integrating with TanStack Query
- `src/pages/` - Top-level page components
- `src/routes/` - TanStack Router route definitions
- `src/supabase_admin/` - Supabase integration utilities
- `scaffold/` - Template directory for new apps
- `e2e-tests/` - Playwright end-to-end tests with extensive fixtures
- `workers/` - TypeScript compilation workers

### Important Features
- **Local AI Development**: Runs entirely locally with user's own API keys
- **Multi-Provider Support**: Anthropic, OpenAI, Ollama, LM Studio, and custom providers
- **Git Integration**: Built-in version control with GitHub sync
- **Real-time Chat**: Streaming AI responses with approval/rejection workflow
- **Code Preview**: Integrated preview panel with live reload
- **Project Management**: Create, import, and manage multiple apps
- **Template System**: Scaffold new projects from templates

### Testing Strategy
- Unit tests with Vitest (`src/__tests__/`)
- Comprehensive E2E tests with Playwright covering all major workflows
- Test utilities and helpers in `e2e-tests/helpers/`
- Extensive fixture data for E2E tests in `e2e-tests/fixtures/`

### Build Configuration
- Electron Forge for packaging and distribution
- Vite for fast development and building
- Multiple TypeScript configurations for different parts of the app
- Cross-platform builds (macOS, Windows, Linux)