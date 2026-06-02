# Usage

## Built with
- React Router 6, ShadCN UI, Tailwind, Lucide Icons, ESLint, Vite
- W7S native JavaScript/TypeScript backend support when `worker/index.ts` is used

## Restrictions
- Tailwind: define custom colors in `tailwind.config.js` (not in `index.css`)

## Styling
- Responsive, accessible
- Prefer ShadCN components; Tailwind utilities for custom parts
- Icons from `lucide-react`
- Error boundaries are already implemented

## Animation
- Use `framer-motion` for small interactions when needed

## Components
- Import from `@/components/ui/*` (ShadCN). Avoid reinventing components.

## Example
```tsx
import { Button } from '@/components/ui/button'
import { Card, CardContent } from '@/components/ui/card'

export function Example() {
  return (
    <Card className="max-w-sm">
      <CardContent className="p-4 flex gap-2">
        <Button>Click</Button>
      </CardContent>
    </Card>
  )
}
```

## Backend (optional)
- If you add backend routes, do it in `worker/userRoutes.ts`. Follow the existing `worker/index.ts` pattern carefully to avoid breakage.
- The included GitHub Actions workflow runs `npm run build` before `w7s-io/w7s-cloud@v1`, producing `dist/` for static assets and `worker/index.js` for the bundled backend.

---

## Routing (CRITICAL)

Uses `createBrowserRouter` - do NOT switch to `BrowserRouter`/`HashRouter`.

If you switch routers, `RouteErrorBoundary`/`useRouteError()` will not work (you'll get a router configuration error screen instead of proper route error handling).

**Add routes in `src/main.tsx`:**
```tsx
const router = createBrowserRouter([
  { path: "/", element: <HomePage />, errorElement: <RouteErrorBoundary /> },
  { path: "/new", element: <NewPage />, errorElement: <RouteErrorBoundary /> },
]);
```

**Navigation:** `import { Link } from 'react-router-dom'` then `<Link to="/new">New</Link>`

**Don't:**
- Use `BrowserRouter`, `HashRouter`, `MemoryRouter`
- Remove `errorElement` from routes
- Use `useRouteError()` in your components
