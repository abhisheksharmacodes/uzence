# Uzence UI Components

A modern React TypeScript component library built with Tailwind CSS and documented with Storybook.

## 🚀 Features

- **Built with TypeScript**: Safer code and better editor help.
- **Styled with Tailwind**: Quick, consistent styles using utility classes.
- **Storybook docs**: See and play with components in the browser.
- **Accessible by default**: Uses proper labels and ARIA where needed.
- **Responsive**: Works on mobile and desktop.
- **Organized folders**: Easy to read and maintain.

## 🧭 How I built this (simple explanation)

- **TypeScript everywhere**: I used generics (like `DataTable<T>`) so the table knows what kind of rows you pass.
- **Accessibility**: Labels and ARIA are part of the components. You can sort with keyboard keys too.
- **Tailwind setup**: Tailwind is added with Vite’s official plugin in `vite.config.ts`. Storybook pulls styles from `src/index.css` via `.storybook/preview.ts`.
- **Docs with Storybook**: Stories live in `src/stories/`. You can see props, try controls, and check a11y.
- **Tests**: I used Vitest and Testing Library. Storybook is connected to Vitest so stories can help with tests.
- **Fast dev**: Vite + React SWC makes it quick. I try to keep props simple and avoid extra re-renders.
- **Theming**: Some components (like `InputField`) have a `theme` prop (`light`/`dark`) so you can switch styles without global dark mode.
- **Folder structure**: Code, tests, and stories sit near each other to keep things tidy.

## 🧰 Prerequisites

- Node.js 18+ and npm 9+
- Git

## ⚙️ Setup

1) Install dependencies

```bash
npm install
```

2) Useful npm scripts

```json
{
  "dev": "vite",
  "build": "tsc -b && vite build",
  "preview": "vite preview",
  "lint": "eslint .",
  "storybook": "storybook dev -p 6006",
  "build-storybook": "storybook build",
  "test": "vitest run"
}
```

3) Start the demo app (Vite)

```bash
npm run dev
```

4) Open Storybook (component docs)

```bash
npm run storybook
# If 6006 is busy:
npm run storybook -- -p 6007 --no-open
```

5) Run tests (Vitest)

```bash
npm run test
```

## 📦 Components

### InputField
An input box you can customize (size, style, type). It supports helper text, errors, clear button, password toggle, and basic light/dark look via a `theme` prop.

```tsx
import InputField from '@/components/InputField';

function Example() {
  const [email, setEmail] = useState('');
  return (
    <InputField
      label="Email"
      value={email}
      onChange={(e) => setEmail(e.currentTarget.value)}
      placeholder="you@example.com"
      variant="outlined" // 'outlined' | 'filled' | 'ghost'
      size="md"          // 'sm' | 'md' | 'lg'
      type="text"        // 'text' | 'password' | 'email' | 'number'
      theme="light"      // 'light' | 'dark'
      helperText="We’ll never share your email."
      invalid={false}
      errorMessage={undefined}
    />
  );
}
```

Key props (the common ones):

- `variant`: 'filled' | 'outlined' | 'ghost'
- `size`: 'sm' | 'md' | 'lg'
- `type`: 'text' | 'password' | 'email' | 'number'
- `showClearButton`: boolean (default true)
- `invalid`, `errorMessage`, `helperText`
- `theme`: 'light' | 'dark' (default 'light')
- `id`, `ariaLabel` for accessibility

### DataTable
A simple yet type-safe table with sorting, row selection, loading/empty states, and custom cell rendering.

```tsx
import DataTable, { type Column } from '@/components/DataTable';

type Row = { id: number; name: string; age: number };

const columns: Column<Row>[] = [
  { key: 'id', header: 'ID', sortable: true },
  { key: 'name', header: 'Name', sortable: true },
  { key: 'age', header: 'Age' },
];

const data: Row[] = [
  { id: 1, name: 'Alice', age: 30 },
  { id: 2, name: 'Bob', age: 25 },
];

export default function TableExample() {
  return (
    <DataTable<Row>
      data={data}
      columns={columns}
      selectable
      onRowSelect={(rows) => console.log(rows)}
      loading={false}
    />
  );
}
```

## 🎨 Theming

- `InputField` has a `theme` prop: `"light" | "dark"`.
- For dark examples in Storybook, add a dark background so text has good contrast.

## ♿ Accessibility

- Inputs use proper labels and link them with `htmlFor` and `id`.
- Error and helper text connect with ARIA (like `aria-invalid`, `aria-describedby`).
- Table headers show sort order with `aria-sort` and you can use Enter/Space to sort.
- Row checkboxes have clear labels; select-all shows the in-between (indeterminate) state.

## 🗂️ Project structure

```
src/
  components/
    DataTable/
      DataTable.tsx
      index.ts
    InputField.tsx
    __tests__/
      InputField.test.tsx
      DataTable.test.tsx
  stories/
    InputField.stories.tsx
    DataTable.stories.tsx
  docs/
    DataTable.docs.mdx
    (optional docs)
.storybook/
  main.ts
  preview.ts
  vitest.setup.ts
```

## 🤝 Contributing

1) Make a new branch for your change
2) Add/update stories and tests for what you built
3) Run lint and tests to make sure it’s all good
4) Open a PR

## 📄 License

MIT
