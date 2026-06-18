- A great instruction file is not a novel. It is a concise, structured reference that gives the agent exactly what it needs to work effectively in your codebase.
- A great instruction file has: commands, architecture, conventions, constraints, and known pitfalls

## Commands (the build, test, run, and lint commands you use often)
- `pnpm dev` — start dev server
- `pnpm build` — production build (runs type checks)
- `pnpm test` — run vitest
- `pnpm test:e2e` — run Playwright tests
- `pnpm lint` — ESLint + Prettier check

## Architecture (a short map of how the project is organized and where the important pieces live)

Next.js 15 App Router. React 19. TypeScript strict. Tailwind CSS 4.
 
- `src/app/` — routes and pages (App Router)
- `src/components/` — shared React components
- `src/lib/` — utilities, database, auth
- `src/db/` — Drizzle ORM schema and migrations

## Conventions (how you like things done - naming, style, the 'we use X, not Y' rules.)
- Use Server Components by default. Client Components only when needed.
- All API routes validate input with Zod.
- Database queries go in `src/lib/` — never in components or routes directly.
- Use `var(--token-name)` for all colors — never hardcoded hex values.
 
## Constraints
- Do NOT install new packages without asking.
- Do NOT modify the auth configuration without explicit approval.
- Complex MDX props must be JSON strings, not JSX expressions.

## Known Pitfalls
- `useRef<T>()` without an initial value is a type error in React 19.
  Always use `useRef<T>(null)`.
- PostCSS cannot resolve the `@/` path alias. Use relative paths in
  CSS `@import` statements.
- The Drizzle adapter requires an `as never` cast due to a type conflict.

> [!IMPORTANT]
> A line in CLAUDE.md only helps if Claude can act on it.
> 'Write clean code' sounds nice and says nothing. 'Use named exports, not default exports' is something Claude can actually follow. Specific and concrete beats vague and well-meaning, every time.


> [!TIP]
> - 'Write clean code' → 'Keep functions short - pull anything over 30 lines into its own function'
> - 'Be careful with the database' → 'Never edit migration files by hand, generate them with npm run db:migrate'
> - 'Document the code' → 'Add a one-line comment above every exported function'
> - 'Don't repeat yourself' → 'Put shared logic in utils/ instead of copying it between files'

The left side sounds responsible but decides nothing - 'clean', 'careful', 'documented' each hand the real choice back to whoever's reading. The right side names the actual move, so there's nothing left to interpret.
