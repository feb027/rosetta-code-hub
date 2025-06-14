# Rosetta Code Hub

A high-performance, interactive web portal showcasing over 1,000 programming tasks from the Rosetta Code chrestomathy. Built with modern web technologies and designed with a sleek, dark "code vibe" aesthetic.

## 🚀 Project Vision

The Rosetta Code Hub serves as a central, lightning-fast portal for accessing interactive web-based visualizations of programming tasks. This project combines performance, visual appeal, and comprehensive documentation to create a portfolio piece that demonstrates both technical skill and design sensibility.

## ✨ Key Features

- **⚡ High Performance**: Handles 1000+ tasks without performance degradation
- **🔍 Real-time Search**: Instant client-side filtering and search
- **🎨 Modern Design**: Dark theme with Nord color palette and "code vibe" aesthetic
- **📱 Fully Responsive**: Seamless experience across all device sizes
- **🎭 Smooth Animations**: Framer Motion powered micro-interactions
- **📊 Interactive Visualizations**: Each task rendered as an engaging web component

## 🛠️ Technology Stack

- **Frontend**: React 19 + TypeScript
- **Build Tool**: Vite (with Bun runtime)
- **Styling**: Tailwind CSS v4 with Nord theme
- **Animation**: Framer Motion
- **Routing**: React Router
- **Data Fetching**: TanStack Query
- **State Management**: Zustand (when needed)
- **UI Components**: Radix UI + Lucide Icons

## 🏗️ Architecture

This project follows a modular, feature-based architecture with strict separation of concerns. Each file maintains a single responsibility with a ~250 line limit to ensure maintainability.

```
src/
├── components/          # Reusable UI components
│   ├── layout/         # Layout components (Header, Footer, etc.)
│   └── ui/             # Base UI primitives
├── pages/              # Route-level components
├── hooks/              # Custom React hooks
├── lib/                # Utility functions and configurations
├── types/              # TypeScript type definitions
└── visualizations/     # Individual task implementations
```

## 🚦 Getting Started

```bash
# Install dependencies
bun install

# Start development server
bun dev

# Build for production
bun run build

# Preview production build
bun run preview
```

## 📖 Documentation

- **[SRS Document](../docs/srs.md)**: Complete software requirements specification
- **[Implementation Plan](../docs/implementation.md)**: Step-by-step development guide
- **[Architecture Guide](./architecture.md)**: Technical architecture details
- **[Progress Tracking](./progress.md)**: Development progress and milestones

## 🎨 Design System

The UI follows a carefully crafted design system based on the Nord color palette:

- **Primary Background**: `#2E3440` (nord0)
- **Secondary Background**: `#3B4252` (nord1) 
- **Accent Color**: `#88C0D0` (nord8) - Deep light blue
- **Primary Text**: `#ECEFF4` (nord6)
- **Typography**: Inter (UI) + JetBrains Mono (code/titles)

## 🤝 Contributing

This is primarily a portfolio project, but contributions and feedback are welcome! Please see [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

**Built with ❤️ and lots of ☕ by [Aqua]**
