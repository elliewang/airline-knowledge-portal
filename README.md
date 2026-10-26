# Skyline Intelligence — Airline Knowledge Search + Chatbot

A **100% static**, responsive airline knowledge search portal for **GitHub Pages**. No build, dependency, account, API key, or backend is required.

## Demo features

- Dark enterprise dashboard with responsive navigation and category cards
- Keyword-weighted search of sample airline documents; category filters and document detail dialog
- On-device **extractive chatbot** that selects matching passages and cites clickable source documents
- Sample content on operations, customer experience, intelligence layer, AI governance, data access, analytics, and engineering
- Import/export JSON records in the **current browser session only** (not persisted or uploaded)
- GitHub Actions workflow to publish automatically

**Important:** The chatbot is not an LLM; it selects source passages and cannot perform advanced reasoning or connect to company systems. All seeded policies are explicitly **fictional examples** and do not constitute safety or operational advice.

## Deploy to GitHub Pages

1. Create a new repository (for example `airline-knowledge-portal`).
2. Extract this ZIP and upload **all contents of the `airline-knowledge-portal` folder** to the **repository root**, including `index.html`, `app.js`, `data/knowledge.js`, and `.github/workflows/deploy.yml`.
3. Commit to the `main` branch.
4. In **Settings → Pages → Build and deployment**, select **GitHub Actions** as the source.
5. Open **Actions** and wait for the `Deploy static knowledge portal` workflow to finish.
6. Your URL will generally be `https://YOUR-USERNAME.github.io/REPOSITORY-NAME/`.

The site works in a project subpath because it uses relative asset URLs. You can also preview with `python3 -m http.server 8000` and open `http://localhost:8000`.

## Change knowledge records

Edit `data/knowledge.js` and replace `window.SEED_KNOWLEDGE` with public-safe, approved example data. Alternatively, use **Manage Knowledge** to temporarily import a JSON array for local testing, or export the current collection. Import is ephemeral and never updates the deployed website.

Each record must contain seven nonempty string fields:

```json
{
  "id": "TEC-301",
  "title": "Enterprise Intelligence Layer",
  "category": "Technology",
  "summary": "High-level overview",
  "content": "Detailed knowledge article text.",
  "updated": "2026-10-20",
  "owner": "Enterprise Architecture"
}
```

## Production enterprise architecture (not implemented)

Do **not** place confidential internal airline policies or private customer/employee records in GitHub Pages, even if the repository is private. Static assets can be downloaded by site visitors, and **this application has no authentication or authorization**.

A real internal system requires an authenticated web app, enterprise SSO (OIDC/SAML), backend policy enforcement (RBAC/ABAC), permission-filtered retrieval, protected data stores, approved model inference, encryption, secrets handling, audit trails, governance, freshness checks, and operational monitoring. You can use this demo as a presentation UI prototype while separately implementing that controlled architecture.

## Project files

- `index.html` — layout and styling
- `app.js` — lexical search, extractive Q&A, navigation, import/export
- `data/knowledge.js` — fictional sample library
- `.github/workflows/deploy.yml` — GitHub Pages CI/CD
- `.nojekyll` — avoid GitHub Pages Jekyll processing
