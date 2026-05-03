# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

GitHub profile README repository for [Blysspeak](https://github.com/Blysspeak). Contains:
- `README.md` — profile page with badges, tech stack, and a TimeForged activity card
- `.github/workflows/snake.yml` — GitHub Action generating a contribution snake animation (Platane/snk@v3), runs every 12h and on push to `main`, outputs to `output` branch
- `snane.yml` — legacy/duplicate snake config at repo root (not used by GitHub Actions)

## Key Details

- No build system, no dependencies, no tests — this is a static content repo.
- The snake workflow pushes generated SVGs to the `output` branch via `crazy-max/ghaction-github-pages@v4`.
- README uses centered HTML layout with shields.io badges and skillicons.dev icons.
- TimeForged card is served from `timeforged.nexalix.ru`.
