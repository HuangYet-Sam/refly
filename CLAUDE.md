# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Refly.AI is an open-source AI-native workflow platform - essentially "N8N for non-technical users" and "Canva for workflows." It allows users to build, share, and monetize AI automation workflows through visual interfaces and simple prompts without coding.

## Key Development Commands

```bash
# Development
pnpm dev                    # Start all services in development mode
pnpm build                  # Build all packages
pnpm build:api             # Build API only
pnpm build:web             # Build web only

# Code Quality
pnpm lint                  # Lint with Biome
pnpm format                # Format code with Biome
pnpm check                 # Run all Biome checks
pnpm check:fix             # Fix Biome issues

# Testing
pnpm test                  # Run all tests
pnpm test:unit            # Unit tests only
pnpm test:integration     # Integration tests only

# Database
pnpm prisma:generate      # Generate Prisma client
pnpm sync-db-schema       # Sync database schema

# Environment Setup
pnpm copy-env            # Copy environment templates
pnpm copy-env:develop    # Copy development env
```

## Technology Stack

- **Monorepo**: pnpm workspace with Turborepo
- **Backend**: NestJS (Node.js), PostgreSQL with Prisma, Redis, Qdrant (vector DB)
- **Frontend**: React 18, TypeScript, Rsbuild, Redux Toolkit, Ant Design, Tailwind CSS
- **AI Integration**: Multiple providers (OpenAI, Anthropic, etc.)
- **Real-time**: WebSockets for collaboration

## High-Level Architecture

### Backend Structure (`apps/api`)
- **Framework**: NestJS with dependency injection
- **Database**: PostgreSQL via Prisma ORM
- **Real-time**: WebSockets for collaborative editing
- **AI Features**: RAG implementation, multi-LLM support, skill templates
- **Key Modules**:
  - `canvas/` - Canvas operations and management
  - `workflow/` - Workflow execution engine
  - `skill/` - AI skill management
  - `rag/` - Retrieval-augmented generation

### Frontend Structure (`apps/web`)
- **Canvas System**: Visual workflow builder with drag-and-drop
- **State Management**: Redux Toolkit + React Query
- **Component Architecture**: Reusable React components with TypeScript
- **Real-time Collaboration**: Y.js integration with WebSockets

### Shared Packages (`packages/`)
- `@refly/common-types` - Shared TypeScript types
- `@refly/ui-kit` - Design system components
- `@refly/stores` - State management
- `@refly/utils` - Utility functions
- `@refly/skill-template` - AI workflow templates

## Critical Files

- `apps/api/src/main.ts` - Application bootstrap
- `apps/api/prisma/schema.prisma` - Database schema
- `apps/web/src/App.tsx` - Frontend root component
- `turbo.json` - Build orchestration
- `biome.json` - Code style and linting rules

## Development Guidelines

### Code Style
- **Language**: English only for comments, variables, documentation
- **TypeScript**: Strict typing, no `any` types, explicit return types
- **React**: Use memoization, proper dependency arrays, avoid inline objects
- **Error Handling**: Comprehensive error boundaries with Sentry integration

### Architecture Patterns
- **Backend**: NestJS dependency injection, feature-based modules
- **Database**: Prisma schema with proper relationships
- **API**: RESTful design with proper HTTP status codes
- **Frontend**: Component-driven development with TypeScript

### Environment Setup
1. Requires PostgreSQL and Redis running
2. Extensive environment variable configuration for AI providers
3. Copy environment templates with `pnpm copy-env:develop`
4. Generate Prisma client after schema changes

## Key Features

- **Visual Canvas**: Drag-and-drop workflow building
- **AI Integration**: Multi-provider LLM support
- **RAG System**: Knowledge base integration
- **Real-time Collaboration**: WebSocket-based editing
- **Template System**: Reusable AI workflow templates
- **Extensibility**: Plugin architecture for custom tools