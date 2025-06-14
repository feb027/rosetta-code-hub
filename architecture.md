# Rosetta Code Hub - Architecture Documentation

This document provides a comprehensive overview of the technical architecture, design decisions, and file organization for the Rosetta Code Hub project.

## 🏛️ Architectural Overview

The Rosetta Code Hub follows a **modular, component-based architecture** built on React with TypeScript. The system is designed for high performance, maintainability, and scalability while handling 1000+ interactive task visualizations.

### Core Architectural Principles

1. **Modularity First**: No file exceeds ~250 lines; single responsibility principle
2. **Performance-Driven**: Client-side rendering with optimized lazy loading
3. **Type Safety**: Full TypeScript coverage with strict mode enabled
4. **Component Composition**: Reusable, composable UI components
5. **Documentation-Centric**: Every major component and decision documented

---

## 📁 Project Structure

```
rosetta-hub/
├── public/                 # Static assets and data files
│   ├── tasks.json         # Master list of programming tasks
│   └── vite.svg           # Vite logo
├── src/                   # Source code
│   ├── components/        # Reusable React components
│   │   ├── layout/       # Layout components (Header, Footer, MainLayout)
│   │   └── ui/           # Base UI primitives (SearchInput, Button, etc.)
│   ├── pages/            # Top-level page components
│   ├── hooks/            # Custom React hooks
│   ├── lib/              # Utility functions and configurations
│   ├── types/            # TypeScript type definitions
│   ├── visualizations/   # Individual task implementations
│   ├── App.tsx           # Main application component
│   ├── main.tsx          # Application entry point
│   └── index.css         # Global styles and Tailwind imports
├── docs/                 # Project documentation
│   ├── srs.md           # Software Requirements Specification
│   └── implementation.md # Step-by-step implementation guide
├── README.md             # Project overview and setup
├── progress.md           # Development progress tracking
├── architecture.md       # This file - technical architecture
└── CONTRIBUTING.md       # Contribution guidelines
```

---

## 🎨 Design System Architecture

### Color System (Nord Palette)
```typescript
// Tailwind Theme Configuration
theme: {
  extend: {
    colors: {
      'primary-bg': '#2E3440',    // nord0 - Main background
      'secondary-bg': '#3B4252',  // nord1 - Cards, inputs
      'tertiary-bg': '#434C5E',   // nord2 - Borders, dividers
      'accent': '#88C0D0',        // nord8 - Links, focus, highlights
      'primary-text': '#ECEFF4',  // nord6 - Main text
      'secondary-text': '#D8DEE9', // nord4 - Muted text
    },
    fontFamily: {
      'sans': ['Inter', 'system-ui', 'sans-serif'],
      'mono': ['JetBrains Mono', 'Fira Code', 'monospace'],
    }
  }
}
```

### Typography Hierarchy
- **Headings**: Inter (clean, modern sans-serif)
- **Task Titles**: JetBrains Mono (monospace with ligatures)
- **Body Text**: Inter 
- **Code Snippets**: JetBrains Mono

---

## 🔧 Technical Stack Deep Dive

### Core Framework Layer
- **React 19**: Latest features, improved performance, concurrent rendering
- **TypeScript**: Full type safety, enhanced developer experience
- **Vite**: Lightning-fast HMR, optimized builds, modern ES modules

### Styling & Animation Layer
- **Tailwind CSS v4**: Utility-first styling, custom theme configuration
- **Framer Motion**: Declarative animations, gesture handling
- **clsx + tailwind-merge**: Conditional class handling, conflict resolution

### Data & State Layer
- **TanStack Query**: Server state management, caching, background updates
- **Zustand**: Minimal global state (theme toggles, user preferences)
- **React Router**: Client-side routing, URL parameter handling

### UI Component Layer
- **Radix UI**: Headless, accessible component primitives
- **Lucide React**: Consistent, lightweight icon system
- **Custom Components**: Application-specific UI components

---

## 📊 Data Flow Architecture

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   tasks.json    │────▶│  TanStack Query  │────▶│   React Hook    │
│  (Static Data)  │    │   (Caching)      │    │   (useTasks)    │
└─────────────────┘    └──────────────────┘    └─────────────────┘
                                                        │
                                                        ▼
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Task Cards    │◀───│   Task List      │◀───│   HomePage      │
│  (Individual)   │    │  (Collection)    │    │ (Search State)  │
└─────────────────┘    └──────────────────┘    └─────────────────┘
```

### Data Flow Principles
1. **Single Source of Truth**: `tasks.json` contains all task metadata
2. **Cached Responses**: TanStack Query handles caching and re-fetching
3. **Reactive Updates**: State changes trigger automatic UI updates
4. **Client-Side Filtering**: Search operates on cached data for performance

---

## 🎯 Component Architecture

### Component Hierarchy
```
App
├── MainLayout
│   ├── Header
│   │   ├── SearchInput
│   │   └── Navigation
│   ├── Outlet (Page Content)
│   │   ├── HomePage
│   │   │   └── TaskList
│   │   │       └── TaskItem[]
│   │   └── TaskPage
│   │       └── TaskVisualization
│   └── Footer
```

### Component Responsibilities

#### Layout Components (`src/components/layout/`)
- **MainLayout**: Overall page structure, consistent header/footer
- **Header**: Site branding, search functionality, navigation
- **Footer**: Links to GitHub, Rosetta Code, other resources

#### UI Components (`src/components/ui/`)
- **SearchInput**: Styled input with search icon, debounced input
- **TaskItem**: Individual task card with hover effects, navigation
- **LoadingSpinner**: Consistent loading states across the app

#### Page Components (`src/pages/`)
- **HomePage**: Main hub view, search state management
- **TaskPage**: Individual task visualization container

---

## 🚀 Performance Architecture

### Optimization Strategies
1. **Lazy Loading**: Components loaded on-demand
2. **Code Splitting**: Route-based chunks for faster initial load
3. **Virtualization**: (Future) Handle 1000+ items efficiently
4. **Caching**: TanStack Query prevents unnecessary re-fetches
5. **Bundle Optimization**: Vite's tree-shaking and minification

### Performance Targets
- **Initial Load**: < 2 seconds on 3G
- **Task Filtering**: < 100ms response time
- **Navigation**: < 500ms page transitions
- **Memory Usage**: < 50MB for 1000+ tasks

---

## 🔒 Type Safety Architecture

### TypeScript Configuration
```typescript
// Key tsconfig.json settings
{
  "compilerOptions": {
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "exactOptionalPropertyTypes": true
  }
}
```

### Type Definitions (`src/types/`)
```typescript
// Core data types
interface Task {
  id: string;          // URL-safe identifier
  title: string;       // Display name
  description?: string; // Optional description
  difficulty?: 'easy' | 'medium' | 'hard';
  tags?: string[];     // Categorization
}

interface TaskListProps {
  tasks: Task[];
  searchQuery: string;
  onTaskSelect: (task: Task) => void;
}
```

---

## 🧪 Testing Architecture

### Testing Strategy (Future Implementation)
- **Unit Tests**: Vitest for component logic
- **Integration Tests**: React Testing Library for user interactions
- **E2E Tests**: Playwright for full user journeys
- **Visual Regression**: Chromatic for UI consistency

---

## 📋 File Naming Conventions

```
Components:     PascalCase.tsx     (TaskItem.tsx)
Hooks:          camelCase.ts       (useTasks.ts)
Utilities:      camelCase.ts       (formatDate.ts)
Types:          camelCase.ts       (task.types.ts)
Pages:          PascalCase.tsx     (HomePage.tsx)
Directories:    kebab-case         (task-visualizations/)
```

---

## 🔄 Development Workflow

### Branch Strategy
```
main                    # Production-ready code
├── feature/phase-1     # Phase-based feature branches
├── feature/task-*      # Individual task implementations
└── hotfix/*           # Critical fixes
```

### Commit Convention
```
feat: add new feature
fix: bug fix
docs: documentation changes
style: formatting, styling
refactor: code restructuring
test: testing additions
chore: maintenance tasks
```

---

## 🚀 Deployment Architecture

### Build Process
1. **Type Checking**: TypeScript compilation
2. **Linting**: ESLint + Prettier formatting
3. **Bundling**: Vite production build
4. **Asset Optimization**: Image compression, font subsetting
5. **Static Hosting**: Vercel/Netlify deployment

### Environment Configuration
- **Development**: Hot reload, source maps, verbose logging
- **Production**: Minified bundles, error reporting, analytics

---

## 🔮 Future Architectural Considerations

### Scalability Plans
- **Virtualization**: React Window for 1000+ items
- **Service Workers**: Offline functionality
- **CDN Integration**: Asset delivery optimization
- **Micro-frontends**: Individual task isolation

### Extensibility Points
- **Plugin System**: Third-party task contributions
- **Theme System**: Multiple color schemes
- **API Integration**: Dynamic task loading
- **Internationalization**: Multi-language support
