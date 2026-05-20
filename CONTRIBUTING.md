# Contributing to `@kreozalabs/ui`

When adding or modifying components in this package, please adhere to the following architectural boundaries.

## 📐 What belongs here?

- **Framework-specific components:** Only React (`.tsx`, `.ts`) components.
- **Generic Building Blocks:** Reusable UI components like `<Button>`, `<Table>`, `<Card>`, `<Input>`, etc.
- **Composed UI:** Slightly more complex generic UI elements (e.g., a standard `<Pagination>` or `<DateRangePicker>` component).
- **UI Logic:** Hooks that deal explicitly with UI states (like `useMediaQuery` or `useDisclosure`).

## 🚫 What does NOT belong here?

- **Business Logic:** Do not include API calls, global state management, or product-specific data fetching.
- **Raw Branding and Assets:** SVG logos and exact hex color logic belong in `@kreozalabs/brand`.
- **CSS Configurations:** Global css variables and tailwind presets are now consolidated within this package in `src/styles`.
- **Custom Icons:** Raw custom SVG React icons belong in `@kreozalabs/icons`.

## 🛠️ Adding a New Component

1. Run the component generator (e.g., shadcn/ui CLI) to build the component into the `src/components/` directory.
2. Ensure the component is exported cleanly via the main `src/index.ts` file so consumers can easily import it.
3. If the component requires a new color or design token, add that token to `src/styles/tokens.css`. **Do not** hardcode magic hex colors directly in this package.
