---
slug: project-1-docusaurus-setup
title: Project 1 — Docusaurus learning journal set up
authors: [patrick]
tags: [setup, docusaurus, training]
---

First mandatory project of the DevSecOps training at Developer Akademie: set up my own learning journal with Docusaurus, personalize it, and deploy it to GitHub Pages.

<!-- truncate -->

## What happened on day 1

- Created `Pao040883/my-dso-blog` from the `spmse/dev-blog-template` starter.
- Switched the GitHub Pages source from "Deploy from a branch" to "GitHub Actions"; workflow permissions set to read/write.
- Reconfigured `example.env` to point at the new repo (`BASE_URL=/my-dso-blog/`, own `GITHUB_ORG` and `GITHUB_PROJECT`). Without this, the build still pointed at the template and all asset paths were broken.
- Personalized the site identity: title, tagline, footer copyright, navbar and edit links now point to me and my repo.
- Removed the template's demo content and enabled the blog module.

## What's next

- Replace the homepage landing content with my own.
- Rewrite the README to describe this project.
- Fill `docs/knowledge-base/` with first real entries.
- Replace the Docusaurus default logo and social card image.
