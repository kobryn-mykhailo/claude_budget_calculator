# Project Budget Calculator

A web-based replacement for the FPP (Fixed Price Project) budget estimation Excel template. This tool replicates and improves upon the multi-sheet Excel workflow with an interactive single-page application.

## Quick Start

```bash
# Just open in browser — no build tools needed
open index.html
```

Or use VS Code Live Server, or any local HTTP server.

## What This Replaces

The original Excel template (`Project-Budget-for-FPP-v7_3.xlsx`) contains 9 interconnected sheets:
- **Project Team** — roles, rates, headcount
- **Features Estimate** — PERT-based feature estimation (Optimistic/Pessimistic/Most Likely)
- **Input Data** — project parameters (stabilization %, contingency %, preparation weeks, etc.)
- **Project Level Risks** — risk register with EMV calculation
- **Project Expenses** — equipment, travel, licenses, infrastructure
- **Project Estimate** — auto-calculated budget summary across phases

## Features

- **PERT Estimation** — 3-point estimation with automatic expected value and standard deviation
- **Team Composition** — define roles with internal/external rates and headcount
- **Phase-based Planning** — allocate features across Phase 1/2/3 + Out of Scope
- **Risk Management** — risk register with probability, EMV, and contingency reserve
- **Auto-calculated Budget** — COGS, Revenue, DPM, margins computed in real-time
- **Data Persistence** — save/load projects via browser localStorage
- **Export** — download budget summary as JSON (CSV/XLSX export planned)

## Architecture

Single-file React application (`index.html`) using:
- React 18 (CDN)
- Tailwind CSS (CDN)
- Recharts for charts (CDN)
- Zero build step — opens directly in browser

## Project Structure

```
├── index.html          # The complete app (open this!)
├── README.md           # This file
├── .gitignore
├── docs/
│   └── excel-logic.md  # Documentation of original Excel formulas
└── .github/
    └── ISSUE_TEMPLATE/
        ├── feature.md
        └── bug.md
```

## Development Roadmap

See [GitHub Issues](https://github.com/kobryn-mykhailo/Claude-Code-Practice/issues) for planned features.

### Phase 1 (Current) — Clickable Prototype
- [x] Team roles & rates input
- [x] PERT-based feature estimation
- [x] Risk register
- [x] Budget dashboard with phase breakdown
- [x] Project settings (stabilization %, contingency %, etc.)

### Phase 2 — Data & Export
- [ ] XLSX export matching original template format
- [ ] Import from existing Excel templates
- [ ] PDF report generation
- [ ] Multiple project support

### Phase 3 — Collaboration
- [ ] Cloud storage backend
- [ ] Multi-user editing
- [ ] Version history
- [ ] Approval workflow

## Based On

Project Budget for FPP v7.3 template — calculation logic faithfully reproduced from the original Excel formulas.
