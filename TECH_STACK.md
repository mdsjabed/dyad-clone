# Dyad Clone - Complete Tech Stack Guide

This document outlines all the technologies, skills, tools, and libraries needed to build a clone of the Dyad AI app builder.

## 🎯 Core Technologies & Skills Required

### **Desktop Application Framework**
- **Electron** - Cross-platform desktop app framework using web technologies
  - Main process (Node.js backend)
  - Renderer process (Web frontend)
  - Preload scripts for secure IPC communication
  - Electron Forge for packaging and distribution

### **Frontend Technologies**

#### **Core Frontend Stack**
- **React 19** - UI library with latest features
- **TypeScript** - Type-safe JavaScript development
- **TanStack Router** - Type-safe routing (NOT React Router or Next.js)
- **Vite** - Fast build tool and development server

#### **State Management**
- **Jotai** - Atomic state management for local state
- **TanStack Query (React Query)** - Server state management, caching, and synchronization
- **Zustand** (optional) - Simple state management alternative

#### **Styling & UI Components**
- **Tailwind CSS 4** - Utility-first CSS framework
- **Radix UI** - Unstyled, accessible UI components:
  - Accordion, Alert Dialog, Checkbox, Dialog, Dropdown Menu
  - Label, Popover, Scroll Area, Select, Separator, Switch
  - Toggle, Tooltip, and many more
- **Framer Motion** - Animation library for smooth transitions
- **Class Variance Authority (CVA)** - Component variants management
- **Tailwind Merge** - Merge Tailwind classes efficiently
- **Geist Font** - Modern typography

#### **Code Editor & Syntax Highlighting**
- **Monaco Editor** - VS Code editor in the browser
- **@monaco-editor/react** - React wrapper for Monaco
- **Shiki** - Syntax highlighter
- **React Shiki** - React integration for Shiki

### **Backend/Main Process Technologies**

#### **Database & ORM**
- **SQLite** - Local database storage
- **Better SQLite3** - Synchronous SQLite driver for Node.js
- **Drizzle ORM** - Type-safe SQL ORM
- **Drizzle Kit** - Database migrations and schema management

#### **File System & Git Operations**
- **Node.js fs module** - File system operations
- **Isomorphic Git** - Pure JavaScript Git implementation
- **Glob** - File pattern matching
- **Tree Kill** - Process management

### **AI Integration**

#### **AI SDK & Providers**
- **Vercel AI SDK** - Universal AI interface
- **AI SDK Providers**:
  - @ai-sdk/anthropic (Claude)
  - @ai-sdk/openai (GPT models)
  - @ai-sdk/google (Gemini)
  - @ai-sdk/openai-compatible (Custom providers)
  - @openrouter/ai-sdk-provider (OpenRouter)
  - ollama-ai-provider (Local Ollama)

#### **LLM Provider Integration**
- **OpenAI API** - GPT models
- **Anthropic API** - Claude models  
- **Ollama** - Local model serving
- **LM Studio** - Local model management
- **Custom provider support**

### **Third-Party Integrations**

#### **Cloud Services**
- **Supabase** - Backend-as-a-Service
  - @dyad-sh/supabase-management-js (Custom management SDK)
  - Database, Auth, and API management
- **Vercel** - Deployment platform
  - @vercel/sdk for API integration
- **GitHub** - Version control and repository management
  - GitHub API integration
  - OAuth authentication

#### **Analytics & Monitoring**
- **PostHog** - Product analytics and feature flags
- **Electron Log** - Logging for Electron apps

### **Development Tools & Testing**

#### **Code Quality & Linting**
- **Oxlint** - Fast JavaScript/TypeScript linter
- **Biome** - Fast formatter and linter (alternative to ESLint/Prettier)
- **Prettier** - Code formatting
- **Husky** - Git hooks
- **Lint Staged** - Run linters on staged files

#### **Testing Framework**
- **Vitest** - Fast unit testing framework
- **@vitest/ui** - Visual test runner
- **Happy DOM** - Lightweight DOM for testing
- **@testing-library/react** - React testing utilities
- **Playwright** - End-to-end testing framework
- **Electron Playwright Helpers** - E2E testing for Electron

#### **Build Tools & Configuration**
- **TypeScript** - Multiple tsconfig files for different parts
- **ESBuild Register** - Fast TypeScript execution
- **Cross-env** - Cross-platform environment variables
- **Rollup Common.js Plugin** - Module bundling

### **Utilities & Helpers**

#### **Date & Text Processing**
- **Date-fns** - Modern date utility library
- **UUID** - Unique identifier generation
- **React Markdown** - Markdown rendering
- **Remark GFM** - GitHub Flavored Markdown support

#### **System Integration**
- **Fix Path** - Fix PATH environment on macOS
- **Shell Env** - Get shell environment variables
- **Kill Port** - Kill processes on specific ports
- **Dotenv** - Environment variable loading

#### **UI Enhancement**
- **Sonner** - Toast notifications
- **React Resizable Panels** - Resizable layout panels
- **Lucide React** - Beautiful icon library

## 🛠️ Development Environment Setup

### **Required Tools**
1. **Node.js 20+** - JavaScript runtime
2. **npm** - Package manager
3. **Git** - Version control
4. **VS Code** (recommended) - Code editor with extensions:
   - TypeScript support
   - Tailwind CSS IntelliSense
   - Prettier
   - Electron debugging support

### **System Dependencies**
- **Python** - For native module compilation
- **Build tools** - Visual Studio Build Tools (Windows) or Xcode (macOS)
- **SQLite** - Database engine

## 📚 Key Learning Areas

### **Essential Skills**
1. **Electron Development**
   - IPC communication patterns
   - Main vs Renderer process architecture
   - Security best practices
   - Native OS integration

2. **React Advanced Patterns**
   - Custom hooks
   - Context providers
   - Error boundaries
   - Performance optimization

3. **TypeScript Proficiency**
   - Advanced types and generics
   - Module declarations
   - Type-safe API design

4. **State Management Architecture**
   - Jotai atomic patterns
   - TanStack Query for server state
   - Local vs server state separation

5. **AI Integration Patterns**
   - Streaming responses
   - Token management
   - Error handling
   - Multiple provider abstractions

### **Database & Backend Skills**
1. **SQL & SQLite**
   - Schema design
   - Migrations
   - Query optimization

2. **Drizzle ORM**
   - Schema definition
   - Type-safe queries
   - Relations and joins

3. **File System Operations**
   - Git operations programmatically
   - File watching and monitoring
   - Path handling across platforms

### **Testing Strategies**
1. **Unit Testing**
   - Component testing with Testing Library
   - Hook testing patterns
   - Mocking strategies

2. **E2E Testing**
   - Playwright for Electron apps
   - Page object patterns
   - Cross-platform testing

## 🏗️ Architecture Patterns

### **IPC Communication Pattern**
- Type-safe IPC using TypeScript interfaces
- Error propagation from main to renderer
- Async operations with proper error handling

### **Component Architecture**
- Compound components with Radix UI
- Controlled vs uncontrolled component patterns
- Custom hook patterns for data fetching

### **File Structure Patterns**
```
src/
├── atoms/          # Jotai state atoms
├── components/     # React components
├── hooks/          # Custom React hooks
├── ipc/            # IPC handlers and types
├── db/             # Database schema and queries
├── pages/          # Route components
└── utils/          # Utility functions
```

## 🚀 Deployment & Distribution

### **Build Pipeline**
- Electron Forge for cross-platform builds
- GitHub Actions for CI/CD
- Automated testing and quality checks

### **Distribution**
- macOS: .dmg and Mac App Store
- Windows: .exe installer and Microsoft Store
- Linux: .deb and .rpm packages

### **Auto-Updates**
- Electron's built-in updater
- Staged rollouts
- Version management

## 📖 Recommended Learning Path

1. **Start with Electron basics** - Understand main/renderer processes
2. **Learn React with TypeScript** - Master component patterns
3. **Study TanStack Router** - Different from traditional React Router
4. **Practice with Jotai & TanStack Query** - Modern state management
5. **Integrate AI SDKs** - Start with simple chat implementations
6. **Master Tailwind + Radix UI** - Build beautiful interfaces
7. **Learn testing patterns** - Both unit and E2E testing
8. **Study IPC patterns** - Secure communication between processes
9. **Practice with SQLite + Drizzle** - Local database operations
10. **Build deployment pipeline** - Package and distribute apps

This tech stack represents a modern, type-safe, and scalable approach to building desktop AI applications with web technologies.