<div align="center">

<img src="src/assets/logo.svg" alt="ScrapThatPage logo" width="96" height="96" />

# ScrapThatPage

**Point-and-click web scraping for the desktop — no code required.**

A cross-platform desktop app that lets you build reusable scraping scripts by
stacking simple steps — open a page, click, type, extract data — and run them
against a real browser window. Extracted values land in a table you can export
or copy.

[![License: MIT](https://img.shields.io/badge/License-MIT-3DA639?logo=opensourceinitiative&logoColor=white)](LICENSE) [![Electron](https://img.shields.io/badge/Electron-43-47848F?logo=electron&logoColor=white)](https://www.electronjs.org) [![React](https://img.shields.io/badge/React-19-087EA4?logo=react&logoColor=white)](https://react.dev) [![TypeScript](https://img.shields.io/badge/TypeScript-5.9-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org)

</div>

---

## Screenshots

|                                   |                                       |
| --------------------------------- | ------------------------------------- |
| ![Home](./screenshots/Home.png)   | ![Scripts](./screenshots/Scripts.png) |
| ![Editor](./screenshots/Editor.png) | ![Run](./screenshots/Run.png)       |

<details>
<summary>More screenshots</summary>

![Favorites](./screenshots/Favorites.png)
![History](./screenshots/History.png)
![Settings](./screenshots/Settings.png)

</details>

## Features

- **Visual script builder** — compose a script step by step; drag to reorder,
  undo/redo, and a searchable step picker for adding operations.
- **Browser steps** — `open` a URL, `click` an element, `type` into a field,
  `extract` values by CSS selector and attribute, plus `wait`, `delay`, and
  `scroll`.
- **Element picker** — click an element in the scraper window and its CSS
  selector is filled in for you.
- **Reliable execution** — steps auto-wait for their target to appear before
  acting; runs can be headless and paced with a configurable delay between steps.
- **Variables and control flow** — `set`/`increase`/`decrease` variables and
  branch or loop with `if`/`while`; reference variables in inputs with
  `{{variable}}` placeholders.
- **Results table** — extracted data is collected into a table and exported to
  **CSV**, **JSON**, or **XLSX**, or copied to the clipboard.
- **Run history** — every run is recorded with its results and a per-step log.
- **Library management** — create, edit, delete, favorite, search, and
  import/export scripts as JSON.
- **Command palette** — `Cmd/Ctrl-K` to jump anywhere or run/edit a script.
- **Local-first** — scripts and runs are stored on-device in IndexedDB; nothing
  leaves your machine.

## How It Works

Scripts run in a dedicated Chromium window that ScrapThatPage drives over the
**Chrome DevTools Protocol** using Electron's in-process
`webContents.debugger`. That means no remote debugging port is opened, so
scraping keeps working in the signed, packaged app — while still getting
Puppeteer-style ergonomics: navigation waits for the document, actions auto-wait
for their selector, clicks and typing dispatch trusted input events, and hidden
windows stay active so lazily rendered content still loads.

## Tech Stack

| Area          | Tools                                                                 |
| ------------- | --------------------------------------------------------------------- |
| **Framework** | [Electron](https://www.electronjs.org/) + [Electron Forge](https://www.electronforge.io/) · [Vite](https://vite.dev/) |
| **UI**        | [React 19](https://react.dev/) · [shadcn/ui](https://ui.shadcn.com/) · [Tailwind CSS v4](https://tailwindcss.com/) · [Motion](https://motion.dev/) |
| **State**     | [Zustand](https://zustand.docs.pmnd.rs/) (with [zundo](https://github.com/charkour/zundo) for undo/redo) · [Dexie](https://dexie.org/) (IndexedDB) · [Zod](https://zod.dev/) |
| **Testing**   | [Vitest](https://vitest.dev/)                                        |
| **Tooling**   | [TypeScript](https://www.typescriptlang.org/) (strict) · [Biome](https://biomejs.dev/) (lint and format) |

## Getting Started

These instructions will get you a copy of the project up and running on your
local machine for development purposes.

### Requirements

To install and run this project you need:

- [Node.js](https://nodejs.org/) 20.19+ (or 22.12+)
- [pnpm](https://pnpm.io/) 10+
- [git](https://git-scm.com/downloads) (only to clone this repository)

### Installation

To set up everything on your local machine, follow these steps:

1. Clone this repo and then change directory to the `scrap-that-page` folder:

```bash
git clone https://github.com/kaushalmeena/scrap-that-page.git
cd scrap-that-page
```

2. Install project dependencies using pnpm:

```bash
pnpm install
```

### Running

To run the app in development with hot reload:

```bash
pnpm start
```

### Testing

To run the unit tests:

```bash
pnpm test
```

To lint the project:

```bash
pnpm lint
```

### Building

To build distributable installers/archives for the current platform:

```bash
pnpm make
```

Artifacts are written to `out/`. Forge is configured to produce a Squirrel
installer (Windows), a ZIP (macOS), and `.deb` / `.rpm` packages (Linux); build
on the target OS to produce that platform's package.

## Contributing

Contributions are welcome! If you find a bug or have a feature request, please
[open an issue](https://github.com/kaushalmeena/scrap-that-page/issues/new/choose)
first to discuss it. For code changes, fork the repository, create a branch,
and open a pull request.

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE)
file for details.
