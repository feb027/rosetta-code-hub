# Contributing to Rosetta Code Hub

Thank you for your interest in contributing to the Rosetta Code Hub! This is primarily a portfolio project, but contributions, feedback, and suggestions are welcome.

## 🎯 Project Goals

This project serves as a high-performance, interactive web portal for Rosetta Code programming tasks. The primary objectives are:

- **Performance**: Handle 1000+ tasks without degradation
- **Visual Appeal**: Modern, dark "code vibe" aesthetic with Nord colors
- **Code Quality**: Maintainable, well-documented, modular codebase
- **Developer Experience**: Fast development workflow with excellent tooling

## 🏗️ Development Setup

### Prerequisites
- **Bun**: Latest version for package management and runtime
- **Node.js**: v18+ (for compatibility)
- **Git**: For version control

### Getting Started
```bash
# Clone the repository
git clone https://github.com/[username]/rosetta-code-hub.git
cd rosetta-code-hub

# Install dependencies
bun install

# Start development server
bun dev

# Build for production
bun run build
```

## 📋 Code Standards

### File Organization
- **Modular Design**: Keep files under ~250 lines
- **Single Responsibility**: Each file should have one clear purpose
- **Feature-Based Structure**: Group related functionality together

### TypeScript Guidelines
- **Type Safety**: All code must be fully typed
- **Interface First**: Define interfaces before implementation
- **No `any` Types**: Use proper typing or `unknown` with type guards

### Component Standards
```typescript
// Preferred component structure
interface ComponentProps {
  // Props definition
}

export const Component: React.FC<ComponentProps> = ({ ...props }) => {
  // Component implementation
};
```

### Styling Guidelines
- **Tailwind First**: Use utility classes for styling
- **Consistent Spacing**: Follow Tailwind's 4px scale
- **Nord Theme**: Stick to the defined color palette
- **Responsive Design**: Mobile-first approach

## 🎨 Design System

### Colors (Nord Palette)
- **Primary Background**: `#2E3440` (nord0)
- **Secondary Background**: `#3B4252` (nord1)
- **Accent Color**: `#88C0D0` (nord8)
- **Primary Text**: `#ECEFF4` (nord6)
- **Secondary Text**: `#D8DEE9` (nord4)

### Typography
- **UI Font**: Inter
- **Code Font**: JetBrains Mono
- **Hierarchy**: Consistent heading scales

## 🚀 Contribution Types

### 1. Bug Reports
- **Use GitHub Issues**: Clear title and description
- **Reproduction Steps**: Include minimal reproduction case
- **Environment Details**: Browser, OS, screen size
- **Expected vs Actual**: Clear explanation of the issue

### 2. Feature Requests
- **Alignment Check**: Ensure it fits the project goals
- **Use Cases**: Explain the problem it solves
- **Implementation Ideas**: Suggest technical approach

### 3. Code Contributions

#### Task Visualizations
The most valuable contributions are new task implementations:

```
src/visualizations/[task-name]/
├── index.tsx           # Main task component
├── README.md          # Implementation documentation
├── types.ts           # Task-specific types
└── utils.ts           # Task-specific utilities
```

**Task Implementation Guidelines:**
- **Interactive**: Make it engaging, not just a solution display
- **Documented**: Explain the algorithm and approach
- **Performant**: Optimize for smooth animations and interactions
- **Accessible**: Consider keyboard navigation and screen readers

#### Hub Improvements
- **Performance Optimizations**: Profiling and improvements
- **UI/UX Enhancements**: Better interactions and animations
- **Developer Experience**: Tooling and workflow improvements

## 🔄 Pull Request Process

### Before Submitting
1. **Branch Naming**: Use descriptive names (`feat/task-100-doors`, `fix/search-performance`)
2. **Code Quality**: Ensure TypeScript compiles without errors
3. **Testing**: Verify changes work across different screen sizes
4. **Documentation**: Update relevant docs if needed

### PR Requirements
- **Clear Title**: Descriptive and concise
- **Detailed Description**: What changes were made and why
- **Screenshots**: For UI changes, include before/after images
- **Testing Notes**: How to test the changes

### Review Process
1. **Automated Checks**: TypeScript compilation, linting
2. **Code Review**: Maintainer will review for quality and alignment
3. **Testing**: Manual testing of functionality
4. **Merge**: Once approved, changes will be merged

## 📖 Documentation

### Required Documentation
- **README Updates**: For significant feature additions
- **Component Documentation**: JSDoc comments for complex logic
- **Architecture Notes**: Update `architecture.md` for structural changes
- **Progress Tracking**: Update `progress.md` for completed tasks

### Documentation Style
- **Clear and Concise**: Easy to understand for future developers
- **Code Examples**: Include usage examples where helpful
- **Rationale**: Explain why decisions were made

## 🐛 Issue Templates

### Bug Report Template
```markdown
**Describe the bug**
A clear description of what the bug is.

**To Reproduce**
Steps to reproduce the behavior:
1. Go to '...'
2. Click on '....'
3. See error

**Expected behavior**
What you expected to happen.

**Screenshots**
If applicable, add screenshots.

**Environment:**
- Browser: [e.g. Chrome, Firefox]
- OS: [e.g. Windows, macOS, Linux]
- Screen size: [e.g. 1920x1080, mobile]
```

### Feature Request Template
```markdown
**Feature Description**
Clear description of the feature you'd like to see.

**Problem it Solves**
What problem does this feature address?

**Proposed Solution**
How would you like it to work?

**Alternatives Considered**
Any alternative solutions you've considered?

**Additional Context**
Any other context or screenshots about the feature request.
```

## 🎉 Recognition

Contributors will be recognized in:
- **README.md**: Contributors section
- **Individual Task READMEs**: Author credit for task implementations
- **GitHub**: Proper commit attribution and PR recognition

## 📞 Questions?

- **GitHub Issues**: For bugs and feature requests
- **GitHub Discussions**: For general questions and ideas
- **Email**: [febnawanrochman2@gmail.com]

---

**Thank you for contributing to making the Rosetta Code Hub even better! 🚀**
