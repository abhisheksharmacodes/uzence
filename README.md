# Uzence UI Components

A modern React TypeScript component library built with Tailwind CSS and documented with Storybook.

## 🚀 Features

- **Modern React Components**: Built with TypeScript for type safety
- **Tailwind CSS Styling**: Utility-first CSS framework for consistent design
- **Storybook Documentation**: Interactive component documentation
- **Accessibility First**: WCAG compliant components with proper ARIA attributes
- **Responsive Design**: Mobile-first approach with responsive breakpoints
- **Scalable Architecture**: Well-organized folder structure for maintainability

## 📦 Components

### InputField
A versatile input component with multiple variants, sizes, and states.

**Features:**
- Multiple variants: `filled`, `outlined`, `ghost`
- Three sizes: `sm`, `md`, `lg`
- Input types: `text`, `password`, `email`, `number`
- States: `disabled`, `invalid`, `loading`
- Built-in clear button and password toggle
- Helper text and error messaging

### DataTable
A feature-rich data table component with sorting, selection, and loading states.

**Features:**
- Generic TypeScript interface for type safety
- Column sorting with visual indicators
- Row selection (single/multiple) with select-all
- Loading and empty states
- Responsive design with horizontal scrolling
- Full accessibility support
- Custom cell rendering
```

You can also install [eslint-plugin-react-x](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-x) and [eslint-plugin-react-dom](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-dom) for React-specific lint rules:

```js
// eslint.config.js
import reactX from 'eslint-plugin-react-x'
import reactDom from 'eslint-plugin-react-dom'

export default tseslint.config([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      // Other configs...
      // Enable lint rules for React
      reactX.configs['recommended-typescript'],
      // Enable lint rules for React DOM
      reactDom.configs.recommended,
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
])
```
