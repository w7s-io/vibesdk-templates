# Template Selection

Single stateful object app on W7S. Minimal setup that uses one global object for persistence and stateful features.

Use when:
- You need server-side state with one global DO
- Real-time/stateful services, dashboards, counters

Avoid when:
- Static/SPAs with no backend
- SEO/SSR landing pages
- You only need database-like storage across many entities (see DO v2 runner)

Built with:
- React Router, ShadCN UI, Tailwind, Lucide Icons, ESLint, Vite
- W7S native backend + single stateful object for persistence

