---
title: Docusaurus Blog
sidebar_position: 1
---

# Docusaurus Learning Journal

> Setup notes and configuration steps for this project.

This page documents how the Docusaurus learning journal at [pao040883.github.io/my-dso-blog](https://pao040883.github.io/my-dso-blog/) was set up, starting from the [`spmse/dev-blog-template`](https://github.com/spmse/dev-blog-template) upstream and customising it for personal use.

## Table of contents

- [What this project is](#what-this-project-is)
- [Repository](#repository)
- [Setup steps](#setup-steps)
  - [1. Repository configuration via env variables](#1-repository-configuration-via-env-variables)
  - [2. Site identity in docusaurus.config.ts](#2-site-identity-in-docusaurusconfigts)
  - [3. Footer layout adjustments](#3-footer-layout-adjustments)
  - [4. Blog module activation](#4-blog-module-activation)
  - [5. Removing template demo content](#5-removing-template-demo-content)
- [One-time GitHub settings](#one-time-github-settings)
- [Live result](#live-result)

## What this project is

A personal learning journal built with [Docusaurus](https://docusaurus.io/). It serves three purposes:

- a chronological **blog** of training entries,
- a categorised **knowledge base** for reference notes,
- a **project portfolio** in `docs/projects/`.

## Repository

- Repository: [Pao040883/my-dso-blog](https://github.com/Pao040883/my-dso-blog)
- Template: [spmse/dev-blog-template](https://github.com/spmse/dev-blog-template)

## Setup steps

### 1. Repository configuration via env variables

The deploy workflow copies `example.env` to `.env` before building, so all repository-specific values live in env variables. The values that needed adjustment for this fork:

| Variable | Value | Purpose |
|---|---|---|
| `DEPLOYMENT_URL` | `https://pao040883.github.io` | Production host |
| `BASE_URL` | `/my-dso-blog/` | Path prefix on that host |
| `GITHUB_ORG` | `Pao040883` | Used by Docusaurus deploy metadata |
| `GITHUB_PROJECT` | `my-dso-blog` | Used by Docusaurus deploy metadata |
| `GIT_REPOSITORY_URL` | `https://github.com/Pao040883/my-dso-blog` | Used to derive editUrl values |
| `BLOG_ENABLED` | `true` | Activates the blog plugin |

Without these the build still pointed at the template's `spmse/dev-blog-template`, all asset paths were broken and the deployed site returned 404 for every page.

### 2. Site identity in docusaurus.config.ts

The following config keys were adjusted to reflect ownership of this fork:

- `title` → `Patrick Offermanns – DevSecOps Journey` (browser tab and home-page hero).
- `tagline` → a descriptive subtitle explaining who runs the site and what content it collects.
- `url` fallback → `https://pao040883.github.io` (was `https://spmse.github.io`).
- `navbar.title` and logo `alt` text → personalised.
- `editUrl` for docs and blog → derived from the new `gitRepositoryUrl` TypeScript variable, which mirrors the existing `blogEnabled` env-driven pattern.
- Navbar GitHub link → points to this repository.

### 3. Footer layout adjustments

The default Docusaurus footer was restructured:

- **Docs column** — Tutorial link kept, new Projects link added pointing to `/docs/projects`.
- **Community column** — removed entirely. The Stack Overflow, Discord and Twitter links targeted the Docusaurus community and were not relevant for a personal learning journal.
- **More column** — the upstream link to `facebook/docusaurus` was replaced with a link to this repository, and a `Template` link to `spmse/dev-blog-template` was added.
- Copyright was extended with the suffix `extended from the developer-akademie-starter` to credit the template this project is derived from.

### 4. Blog module activation

The blog plugin is conditional on `BLOG_ENABLED` and ships off in the upstream template. Setting it to `true`:

- adds a Blog link to the navbar,
- activates the `/blog/` route plus tag and author pages,
- enables the RSS / Atom feed.

Post entries live in `blog/`, authors are defined in `blog/authors.yml`, tags in `blog/tags.yml`.

### 5. Removing template demo content

The upstream template ships with demo blog posts and placeholder doc pages. Removed:

- `blog/2019-05-28-first-blog-post.md` and three other demo posts (plus the welcome banner image).
- `docs/guides/some-demo-guide.md` — an empty placeholder.
- `docs/projects/example-project.md` — an empty template skeleton.

Kept as references:

- `docs/guides/docusaurus-basics/` and `docs/guides/tutorial-extras/` — Docusaurus's own tutorial pages, useful while learning the framework.

## One-time GitHub settings

Without these the build runs but the deploy step fails with HTTP 404 from `actions/deploy-pages`:

- **Settings → Pages → Source: GitHub Actions** (not "Deploy from a branch"). The "Deploy from a branch" mode would serve raw markdown source files instead of the built site.
- **Settings → Actions → General → Workflow permissions: Read and write**. Required so the workflow token can publish to the `github-pages` environment.

## Live result

[https://pao040883.github.io/my-dso-blog/](https://pao040883.github.io/my-dso-blog/)
