# UI & Project Structure Standardization Plan

The goal of this refactor is to consolidate the styling system, migrate to modern OKLCH colors, and ensure full compatibility with Tailwind CSS v4 features across the `@kreozalabs/ui` package and consumer apps.

## 1. Styling System Migration

- [ ] **Migrate to OKLCH Colors**:
  - Translate all existing HSL tokens in `tokens.css` to their OKLCH equivalents for better perceptual uniformity.
  - Standardize the `--primary`, `--background`, and `--foreground` definitions.
- [ ] **Tailwind CSS v4 Optimization**:
  - Fully embrace the v4 `@theme` engine.
  - Remove all legacy `tailwind.config.js` or `postcss.config.js` files (Drop v3 support).
  - Consolidate theme definitions into a single source of truth in `packages/ui`.
- [ ] **Enable Cross-Package Scanning**:
  - Add `@source` directives to ensure Tailwind scans `packages/ui`, `apps/web`, and any other relevant folders.

## 2. Package Consolidation

- [ ] **Merge `@kreozalabs/styles` into `@kreozalabs/ui`**:
  - Move `tokens.css`, `base.css`, and any shared utility styles into `packages/ui/src/styles`.
  - Update all imports in `apps/web` to point to the new consolidated locations.
  - Deprecate/Delete the standalone `packages/styles` package.
- [ ] **Icons Strategy**:
  - Evaluate if a separate `@kreozalabs/icons` is needed or if they should be consolidated into the main UI package.

## 3. Project Structure & Branding

- [ ] **Standardize UI Folder Structure**:
  - Ensure all Shadcn components are located in `packages/ui/src/components/`.
  - [ ] **Naming Cleanup**:
  - Ensure all internal workspace references use the `@kreozalabs/` prefix consistently.
- [ ] **Update `components.json`**:
  - Sync the `components.json` across the monorepo to point to the new consolidated paths and aliases.

## 4. Quality & Tooling

- [ ] **Husky & lint-staged**:
  - Set up pre-commit hooks in the root to run Prettier and ESLint.
- [ ] **Consistency Check**:
  - Ensure `Select`, `Button`, and other core components match the high-quality "vibe" found in the reference `vite-monorepo` project.

## Constraints

- **Typography**: Keep **PT Sans** for now; do not switch to Montserrat/Nunito Sans in this phase.
- **No Code Changes to Components**: Focus on the CSS environment and structure rather than rewriting the React logic of components.
