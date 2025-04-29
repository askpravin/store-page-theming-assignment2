# Frontend Intern Assignment: Multiple Theme System

## Overview

Your task is to enhance the GoGetWell.ai web application by implementing a multiple theme system that will allow the platform to adapt its UI based on different medical specialties. This will improve user experience by providing contextually relevant interfaces for different types of medical treatments.

## Project Setup

Before starting, make sure you have the following installed:
* Node.js (version 14 or higher)
* npm (comes with Node.js)

To set up the project:
1. Clone this repository

```
git clone [repository-url]
cd [repository-name]
```

2. Install dependencies

```
npm install
```

3. Start the development server

```
npm run dev
```

The application should now be running on `http://localhost:5173` (or another port if 5173 is in use).

## Requirements

### 1. Create Two Specialty-Based Themes

Develop two complete themes for the following medical specialties:
- **Organ Transplant Theme**: A theme with a focus on trust, expertise, and precision
- **Cosmetic Surgery Theme**: A theme emphasizing aesthetics, transformation, and modern techniques

### 2. Theme Components

Each theme must include the following customizable elements:

- **Color Scheme**: Primary, secondary, accent, and background colors
- **Typography**: Font families, sizes, and weights for different text elements
- **UI Elements**: Buttons, cards, icons, and form elements
- **Hero Banners**: Specialty-specific hero images and messaging
- **Illustrations**: Relevant graphics that match each specialty
- **Marketing Copy**: Tailored testimonials and value propositions

### 3. Theme Implementation

Based on analysis of the existing codebase, you should:

1. Create a new directory structure at `src/views/home/themes/` for theme assets
2. Extend the existing theme configuration in `src/store/themeStore.ts`
3. Update `src/configs/theme.config.ts` to include new theme options
4. Create a theme selector component for the UI

## Technical Guidelines

### Directory Structure

```
src/
└── views/
    └── home/
        └── themes/
            ├── base/
            │   ├── colors.ts
            │   ├── typography.ts
            │   └── components.ts
            ├── organ-transplant/
            │   ├── colors.ts
            │   ├── typography.ts
            │   ├── components.ts
            │   └── assets/
            │       └── [theme-specific images]
            └── cosmetic-surgery/
                ├── colors.ts
                ├── typography.ts
                ├── components.ts
                └── assets/
                    └── [theme-specific images]
```

### Theme Store Enhancement

Modify the existing theme store by updating `src/store/themeStore.ts`. The current implementation uses Zustand. You'll need to extend it to support specialty themes:

```typescript
// Example extension for themeStore.ts
type ThemeState = Theme & {
  specialty: 'default' | 'organ-transplant' | 'cosmetic-surgery';
}

type ThemeAction = {
  // ... existing actions
  setSpecialty: (payload: ThemeState['specialty']) => void;
}

export const useThemeStore = create<ThemeState & ThemeAction>()(
  persist(
    (set) => ({
      // ... existing state
      specialty: 'default',
      setSpecialty: (payload) => set(() => ({ specialty: payload })),
    }),
    {
      name: 'theme',
    },
  ),
)
```

### CSS Implementation

Build on the existing Tailwind CSS configuration. The current approach uses CSS variables (in `app.css`) for dynamic theming:

1. Extend the CSS variable system for specialty-specific themes
2. Update the Tailwind configuration to support new theme variables
3. Create utility classes for theme-specific components

## UI Components to Modify

1. **Hero Section** (`src/views/Home/components/Home.tsx`)
   - Update imagery and messaging based on theme
   - Change color schemes and layouts

2. **Treatment Cards** (`src/views/Home/components/Treatment.tsx`)
   - Customize icons and styling for each theme
   - Highlight relevant specialties based on selected theme

3. **GetInTouch Section** (`src/views/Home/components/GetInTouch.tsx`)
   - Adjust styling and content based on theme

4. **Theme Selector Component** (Create new)
   - Build a UI element that allows users to switch themes
   - This should be visible in the header area

## Demonstration Requirements

Your implementation should demonstrate:

1. **Theme Switching**: Show seamless transitioning between themes
2. **Responsive Design**: All themes must work on mobile, tablet, and desktop
3. **Performance Optimization**: Themes should load efficiently without impact on performance
4. **Proper TypeScript Usage**: Strong typing for all theme-related variables and components
5. **Code Documentation**: Clear documentation of the theme system

## Code Quality Standards

Follow these frontend protocols that are evident in the codebase:

1. **TypeScript**: Use strong typing for all components and functions
2. **React Best Practices**: 
   - Use functional components with hooks
   - Implement proper component composition
   - Follow the pattern of using React.FC for component typing

3. **State Management**:
   - Use Zustand for global state as shown in existing stores
   - Follow patterns in `src/store/themeStore.ts`

4. **CSS Methodology**:
   - Use Tailwind CSS classes following existing patterns
   - Use CSS variables for theme values
   - Maintain responsive design patterns

5. **Code Organization**:
   - Follow the existing project structure
   - Use proper module exports and imports
   - Maintain separation of concerns

6. **Testing**:
   - Write tests for theme-switching functionality
   - Ensure visual consistency across themes

## Deliverables

1. Complete implementation of two themes (Organ Transplant and Cosmetic Surgery)
2. Theme selector component in the UI
3. Documentation of the theme system and how to add new themes
4. Pull request with your changes following the project's contribution guidelines

## Timeline

- Week 1: Research and design themes, plan implementation
- Week 2: Implement base theme structure and first theme
- Week 3: Implement second theme and theme selector
- Week 4: Testing, documentation, and finalization

## Resources

- Current theme implementation in `src/store/themeStore.ts`
- Existing styling in `src/assets/styles/app.css`
- Tailwind configuration in `tailwind.config.cjs`
- Component structure in `src/views/Home/components/`

Good luck with your assignment! This project will help you gain valuable experience with React, TypeScript, Tailwind CSS, and theme implementation in a real-world medical application.

Key Features:
- **Responsive Layout**: Optimized for all screen sizes and devices.
- **Dark/Light Mode**: Easily switch between light and dark themes.
- **Configurable Themes**: Personalize colors, layouts, and more to fit your needs.
- **Built with React + TypeScript**: Ensures robust type-checking and fast development.
- **Multi-Locale Support**: Easily add and manage multiple languages.
- **RTL Support**: Full Right-to-Left support for languages like Arabic or Hebrew.
- **Tailwind Component-Based Architecture**: Reusable components to streamline your development process.
- **API Ready**: Simple integration with any RESTful API.


### Guide
Please visit our [Online documentation](https://ecme-react.themenate.net/guide/documentation/introduction) for detailed guides, setup instructions, and customization options.

