# Tech Stack Explainer for Designers

When explaining technical concepts, the user may be a **product designer** — familiar with UX, visual systems, components, and product logic, but not necessarily a programmer.

## How to Explain

1. **Start with the problem it solves**, not the definition
2. **Use a design analogy** — Figma components, design tokens, frames, auto-layout, etc.
3. **Explain why a team would choose it** and any high-level tradeoffs
4. **Keep code examples minimal** — only when they genuinely help
5. **Be honest about complexity** without over-explaining

## Design Analogy Reference

| Tech Concept | Design Analogy |
|---|---|
| Component library (React, etc.) | A Figma component library — reusable pieces instanced everywhere |
| State management (Zustand, Redux) | A shared "source of truth" — like a main Figma component all instances reference |
| Props | Component properties in Figma — the knobs that change an instance's look/behavior |
| CSS / Tailwind | Visual styling — like Figma's fill, stroke, typography, and spacing panels |
| Design tokens / CSS variables | Figma variables — change one value and it updates everywhere |
| Routing (React Router, Next.js) | A Figma prototype — clicking nav shows a different screen without reloading |
| API | A data connector — like a plugin that pulls real content into Figma |
| Database | A structured content library — rows and columns your UI reads from |
| Build tool (Vite, Webpack) | An export pipeline — packages source files for delivery |
| TypeScript | Annotating component specs — defining exactly what values a component accepts |
| Linting (ESLint) | Figma constraints — rules that enforce consistency and catch mistakes |
| Git / version control | Figma version history + branching — save states, branches, merging work |
| npm / package manager | Figma plugins — third-party tools you install to add capabilities |
| CI/CD pipeline | Auto-publishing — automatically exports and deploys on every commit |
| Monorepo | One Figma file with multiple pages — single source, many outputs |
| Environment variables | A config file that swaps values between dev and production |

## Common Tech Concepts

### Frontend Frameworks
- **React** — Component-based UI library. Each piece of UI is a reusable component.
- **Next.js** — React with server-side rendering and file-based routing. Better for SEO.
- **Vue / Svelte / Angular** — Alternatives to React with different tradeoffs.

### Styling
- **Tailwind CSS** — Utility classes applied directly in HTML instead of separate CSS files.
- **shadcn/ui** — Pre-built Tailwind components. Copy-paste into your codebase.
- **CSS Modules** — Scoped CSS per component — styles can't bleed into other components.

### State Management
- **Zustand** — Lightweight shared state store. Simple, good for medium complexity apps.
- **Redux** — More structured, more boilerplate. Better for very large apps.
- **React Context** — Built-in React state sharing. Good for simple cases, messy at scale.

### Routing
- **React Router** — URL-based navigation without page reloads.
- **Next.js App Router** — File-based routing. Folder structure = URL structure.

### Data Fetching
- **TanStack Query** — Manages fetching, caching, and syncing server data automatically.
- **tRPC** — Frontend and backend share types so they always stay in sync.
- **GraphQL** — Ask for exactly the data you need in the shape you want.

### Build Tools
- **Vite** — Fast dev server. Near-instant hot reload during development.
- **Webpack** — Older, more configurable bundler. Common in legacy projects.

### Desktop / Native
- **Electron** — Desktop apps using web tech. Bundles a full browser. Large file size.
- **Tauri** — Like Electron but uses the OS's native renderer. Smaller and faster.
- **React Native** — Mobile apps (iOS/Android) using React. Renders native UI components.

### Backend / Fullstack
- **Node.js** — JavaScript on the server. Same language as frontend.
- **Supabase** — Postgres database + auth + storage, all with a simple API.
- **Prisma** — Write database queries in TypeScript instead of raw SQL.

### Testing
- **Vitest / Jest** — Unit testing. Test individual functions and components.
- **Playwright / Cypress** — End-to-end testing. Automates a real browser.
- **Storybook** — Component explorer. Render components in isolation — like a design system playground.

### Deployment
- **Vercel** — Deploy frontend apps from git. Best-in-class for Next.js.
- **Docker** — Package your app into a container so it runs the same everywhere.
- **GitHub Actions** — Automated workflows triggered by git events (e.g., run tests on every PR).
