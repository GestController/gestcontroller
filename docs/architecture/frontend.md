# Frontend

**Version:** 0.1 · **Status:** Draft (GestC12)

## 1. Stack
React + Vite. It compiles to static files.

## 2. Hosting on S3
The output of `vite build` is uploaded to an S3 bucket configured as a static site.
- Client-side navigation requires returning `index.html` for unknown routes.
- If the lab allows CloudFront, it is used for HTTPS and caching; if not, alternatives are evaluated for QA.
- A separate bucket per environment (QA and Production).

## 3. Rendering (ADR-0004)
| Option | Description | Use |
|---|---|---|
| CSR (SPA) | The browser builds the page with JavaScript and API data | Chosen for this semester |
| SSR | A server generates the HTML | Requires extra compute; out of scope |

Since the dashboard is internal and behind authentication, SEO is not a requirement and CSR is enough.

## 4. Dynamic pages
Screens are built from API data: routes with parameters (for example `/areas/:id`), lists with filters and pagination, and loading and error states.

## 5. Real time with WebSocket
- The dashboard opens a connection and receives access events.
- Automatic reconnection with increasing wait.
- Authentication when the connection opens and closing when the session expires.
- The load balancer must allow WebSocket.

## 6. Environment variables
API and WebSocket addresses per environment, defined at build time. No secrets are stored in the frontend.
