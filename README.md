# my-dso-blog

> Learning journal, knowledge base, and project portfolio from my DevSecOps training at Developer Akademie.

🌐 **Live:** https://pao040883.github.io/my-dso-blog/

Built with [Docusaurus](https://docusaurus.io/) and deployed to GitHub Pages on every push to `main`.

## What this site is

The site has three sections that I keep filling as the training progresses:

- **Blog** — chronological journal entries: what I worked on each day, what worked, what didn't.
- **Docs › Knowledge base** — reference notes I want to look up later, grouped by topic (containers, DevOps, git, linux, …).
- **Docs › Projects** — portfolio entries for the larger projects of the training, with descriptions and links.

## Repository layout

| Path | Purpose |
|---|---|
| `blog/` | Blog posts. Filenames follow `YYYY-MM-DD-slug.md`. |
| `blog/authors.yml` | Author profiles referenced from post frontmatter. |
| `blog/tags.yml` | Tag definitions and descriptions. |
| `docs/knowledge-base/` | Categorised reference notes. |
| `docs/projects/` | Project pages — overview plus one page per project. |
| `docs/guides/` | How-to docs (Docusaurus basics, deployment, etc.). |
| `src/components/` | Custom React components used inside docs (e.g. `GithubLinkAdmonition`). |
| `src/pages/` | Static pages including the home page. |
| `static/img/` | Logo, favicon, social card. |
| `sidebars.ts` | Sidebar structure for the docs section. |
| `docusaurus.config.ts` | Site configuration: title, theme, plugins. |
| `.github/workflows/` | CI/CD: build + deploy to GitHub Pages. |
| `example.env` | Committed template for deploy-time variables. |
| `.env` | Local copy (git-ignored). |

## Running it locally

Prerequisites: [Node.js](https://nodejs.org/) 18 or later, [pnpm](https://pnpm.io/).

```bash
pnpm install
pnpm start         # dev server with hot reload
pnpm build         # production build into build/
pnpm serve         # serve the production build locally
```

Note: the CI workflow uses `npm install --frozen-lockfile` and `npm run build`, so the npm `package-lock.json` is the source of truth for CI builds.

## Adding new content

### A new blog post

Create a file in `blog/` named `YYYY-MM-DD-some-slug.md` with frontmatter:

```yaml
---
slug: some-slug
title: Title shown on the site
authors: [patrick]
tags: [setup, docusaurus]
---
```

Any tags referenced must already exist in `blog/tags.yml`, otherwise the build emits a warning.

### A new doc page

1. Create a markdown file under the relevant `docs/<area>/` folder.
2. The sidebar in `sidebars.ts` is auto-generated, so the new page is picked up automatically.
3. Reorder or rename categories via the `_category_.yaml` file in each folder.

### A new tag or author

Define it in `blog/tags.yml` or `blog/authors.yml` before referencing it from a post.

## Configuration

Deploy-time values live in `example.env` (committed) and `.env` (git-ignored). The deploy workflow copies `example.env` to `.env` before building.

| Variable | Purpose |
|---|---|
| `DEPLOYMENT_URL` | Production host, e.g. `https://pao040883.github.io`. |
| `BASE_URL` | Path prefix served on that host. For a GitHub project page this must be `/<repo-name>/`. |
| `GITHUB_ORG`, `GITHUB_PROJECT` | Used by Docusaurus for deploy metadata. |
| `GIT_REPOSITORY_URL` | Used to derive the `editUrl` for docs and blog pages. |
| `DEPLOYMENT_BRANCH` | Branch the workflow deploys from. |
| `BLOG_ENABLED` | Set to `true` to render the blog section in the navbar and routes. |

## Deployment

The site is automatically deployed to GitHub Pages by a prepared GitHub Actions workflow whenever a commit lands on `main`. No manual deploy step is required.

## Workflow conventions

Solo project, but I still follow a feature-branch workflow (it's a requirement of the training and a good habit anyway):

- Branch off `main` for every change. Branch names follow Conventional Commit prefixes: `chore/…`, `feat/…`, `fix/…`, `docs/…`.
- Multiple small commits per branch are preferred over one mixed commit; unrelated changes go on separate branches.
- Open a pull request and merge via the GitHub UI. CI runs on PR creation and on `main`.

## License

[MIT](./LICENSE)
