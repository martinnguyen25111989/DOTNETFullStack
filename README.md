# .NET FullStack Architecture — Code → Runtime

An interactive, single-file **HTML/JavaScript** diagram that maps a modern
**.NET (ASP.NET Core) full-stack** system across its entire lifecycle, traced
through a real-world **Shopify Order** example.

> No build step, no dependencies — just open [`index.html`](./index.html) in any browser.

## 🌐 Live demo (GitHub Pages)

Once Pages is enabled (see [Deploy](#-deploy-on-github-pages)), the site is published from `main` at:

```
https://martinnguyen25111989.github.io/dotnetfullstack/
```

## ✨ What's inside

The page has three sections:

### 1. Full lifecycle — from code to runtime
A 7-stage pipeline with the real tooling at each gate:

`Code` → `Commit & PR` → `Build` → `Test` → `Package` → `Deploy` → `Run & Observe`

…with a feedback loop from monitoring back into the next change.

### 2. Layered architecture + cross-cutting concerns
- **Runtime layers (top → bottom):**
  - **Frontend** — Blazor / React / Angular / Razor, TypeScript, REST + SignalR
  - **Backend** — ASP.NET Core Web API, MediatR / CQRS, Clean Architecture, FluentValidation, DI
  - **Database / Data Access** — EF Core / Dapper, SQL Server / PostgreSQL, migrations, Redis, Cosmos DB
  - **Cloud / DevOps** — Docker, Kubernetes / AKS, App Service, GitHub Actions / Azure DevOps, Terraform / Bicep
- **Cross-cutting concerns (wrap every layer):**
  - **Security** — OAuth2 / OIDC, JWT, Azure AD, TLS, Key Vault, OWASP, RBAC
  - **QA / Testing** — xUnit / NUnit, Moq, integration tests, Playwright, k6
  - **Monitoring / Observability** — App Insights / OpenTelemetry, Serilog, Prometheus + Grafana, health checks
  - **Integration / Messaging** — Shopify Admin API & webhooks, Azure Service Bus / RabbitMQ, Kafka, MassTransit
  - **Collaboration / Process** — Agile / Scrum, Jira / Azure Boards, Git flow, PR reviews

### 3. Worked example — creating a Shopify Order
An **animated 9-step trace** of a single "Place Order" action flowing through
the whole stack, with the matching code snippet lighting up at each step:

1. Frontend POSTs the cart (Blazor + JWT)
2. Security middleware validates TLS / JWT / CORS
3. `OrdersController` model-binds & validates the DTO
4. `CreateOrderHandler` applies domain rules (stock, totals, tax)
5. EF Core repository persists the order to SQL Server
6. Integration syncs to Shopify Admin API + publishes `OrderCreated`
7. Monitoring emits structured log, trace span & metric
8. `201 Created` + SignalR push updates the UI
9. Cloud / DevOps: it all runs in a container on AKS, shipped by CI/CD

**Controls:** ▶ Run flow (auto-play) · ⏭ Next step · ↺ Reset · clickable steps · tabbed code snippets.

## 🚀 Deploy on GitHub Pages

The site is a single static file (`index.html`) served straight from a branch —
no build step or workflow required.

**One-time setup (in the GitHub UI):**

1. Go to **Settings → Pages**
   (https://github.com/martinnguyen25111989/DOTNETFullStack/settings/pages).
2. Under **Build and deployment → Source**, choose **Deploy from a branch**.
3. Set **Branch** to `main` and **Folder** to `/ (root)`, then click **Save**.

GitHub then publishes `index.html` at the live URL above (give it a minute on
the first deploy). Every push to `main` re-publishes automatically.

## 🛠 Run locally

Just open the file:

```bash
# macOS
open index.html
# Linux
xdg-open index.html
# Windows
start index.html
```

Or serve it (handy for a clean URL):

```bash
python3 -m http.server 8080
# then visit http://localhost:8080
```

## 📁 Project structure

```
.
├── index.html   # the entire interactive diagram (self-contained)
└── README.md
```

## 📄 License

Free to use for learning, presentations, and documentation.
