# GitHub Copilot Instructions for Mintlify Documentation

This repository contains the documentation site for Edilogic, built using [Mintlify](https://mintlify.com/).

## 🏗 Project Architecture

- **Framework**: Mintlify (Static documentation generator).
- **Configuration**: `docs.json` is the central configuration file. It defines:
  - **Navigation**: The sidebar structure (`navigation` array).
  - **Theme**: Colors, fonts, and branding.
  - **API Configuration**: OpenAPI spec location (`openapi`).
- **Content**: Written in **MDX** (`.mdx`), allowing React components within Markdown.
- **Structure**:
  - `docs.json`: Global config.
  - `api-reference/`: API documentation (often linked to `openapi.json`).
  - `snippets/`: Reusable MDX snippets (imported via `<Snippet file="filename.mdx" />`).
  - `images/`: Static assets.

## 🚀 Developer Workflow

### Prerequisites
- Node.js v19+
- Mintlify CLI: `npm i -g mint`

### Common Commands
- **Start Dev Server**: `mint dev` (Runs on http://localhost:3000)
- **Update CLI**: `mint update` (Run if encountering unexpected errors)
- **Custom Port**: `mint dev --port 3333`

### Validation
- Ensure `docs.json` is valid JSON.
- Check for broken links (Mintlify CLI usually warns about these).
- Verify frontmatter in `.mdx` files.

## 📝 Coding Conventions

### MDX & Content
- **Frontmatter**: Every `.mdx` file MUST have frontmatter:
  ```yaml
  ---
  title: "Page Title"
  description: "Brief description for SEO and subtitle"
  icon: "icon-name" # Optional, FontAwesome icon name
  ---
  ```
- **Components**: Prefer Mintlify built-in components over raw HTML:
  - `<Note>`, `<Warning>`, `<Tip>`, `<Info>` for callouts.
  - `<Card>` and `<CardGroup>` for navigation tiles.
  - `<Steps>` and `<Step>` for instructional guides.
  - `<CodeGroup>` for tabbed code blocks.
- **Links**: Use root-relative paths for internal links (e.g., `[Link Text](/folder/page)`).

### Navigation (`docs.json`)
- When adding a new page, **you must register it in `docs.json`** under the appropriate group in the `navigation` array.
- The path in `docs.json` should exclude the `.mdx` extension (e.g., `"essentials/settings"`).

### API Documentation
- API pages in `api-reference/` can be auto-generated from `openapi.json` or manually written.
- To hide an endpoint, remove it from `docs.json` or use `hidden: true` in frontmatter.

## 🔍 Troubleshooting
- **404 Errors**: Check if the file exists and is correctly referenced in `docs.json`.
- **Component Errors**: Ensure MDX components are properly closed and props are valid.
