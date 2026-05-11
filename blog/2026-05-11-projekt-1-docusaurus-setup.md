---
slug: projekt-1-docusaurus-setup
title: Projekt 1 — Docusaurus Lern-Tagebuch aufgesetzt
authors: [patrick]
tags: [setup, docusaurus, ausbildung]
---

Erstes Pflichtprojekt der DevSecOps-Ausbildung an der Developer Akademie: ein eigenes Lern-Tagebuch mit Docusaurus aufsetzen, personalisieren und auf GitHub Pages deployen.

<!-- truncate -->

## Was an Tag 1 passiert ist

- Repo `Pao040883/my-dso-blog` vom Template `spmse/dev-blog-template` abgeleitet.
- GitHub Pages-Quelle von "Deploy from a branch" auf "GitHub Actions" umgestellt; Workflow-Permissions auf Read/Write.
- `example.env` auf das eigene Repo umkonfiguriert: `BASE_URL=/my-dso-blog/`, eigene `GITHUB_ORG` und `GITHUB_PROJECT`. Vorher zeigte der Build noch aufs Template, Asset-Pfade waren kaputt.
- Site-Identitaet personalisiert: Titel, Tagline, Footer-Copyright, Navbar- und Edit-Links zeigen jetzt aufs eigene Repo.
- Demo-Inhalte aus dem Template entfernt, Blog-Modul aktiviert.

## Was als Naechstes ansteht

- Landing-Page (`src/pages/index.tsx`) mit eigenen Inhalten fuellen.
- README auf das eigene Projekt umschreiben.
- `docs/knowledge-base/` mit ersten echten Eintraegen befuellen.
- Eigenes Logo und Social-Card-Bild ersetzen die Docusaurus-Defaults.
