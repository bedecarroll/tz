# AGENTS Guide

This document provides guidelines for AI agents interacting with the `dt-datetime-converter` repository.

## Repository Structure
- `index.html`: Static HTML entry point for the UI.
- `styles.css`: Brutalist CSS styling.
- `src/`: TypeScript source code (logic and components).
  - `main.ts`: Application orchestration, event binding, and rendering. Detects the browser (home) timezone and appends `(home)` to the corresponding timezone name in both the conversion list and the timeline.
  - `autocomplete.ts`: Autocomplete widget for timezone input.
  - `dateTimeConverter.ts`: Natural language parsing and timezone formatting logic.
- `dist/`: Compiled JavaScript output.
- `package.json` & `tsconfig.json`: Build and dependency configuration.

## Build Process
1. Install dependencies: `bun install`.
2. Compile TypeScript: `bun run build` (or `tsc`).
3. Serve static files from project root (e.g., `serve .` or `python3 -m http.server`).

## Coding Guidelines
- **Root Cause Fixes**: Address underlying logic rather than superficial patches.
- **Minimal Changes**: Only change what’s necessary for the feature or fix.
- **Styling**: Maintain the existing brutalist look—monospace font, thick black borders, high contrast.
- **Naming**: Follow camelCase for variables and methods in TypeScript.
- **Testing**: No tests in repo; manual verification via browser is expected.

## New Feature Workflow
1. Understand the feature request and locate the relevant component in `src/`.
2. Modify or add TypeScript code; update styles if UI changes.
3. Compile and verify functionality locally.
4. Update documentation (`README.md` and/or this `AGENTS.md` if needed).

## Interactions
- **Autocomplete Enhancements**: Edit `src/autocomplete.ts` and adjust options in `main.ts`.
- **Conversion Logic**: Adjust `src/dateTimeConverter.ts`, ensuring `formatDate` covers new formats.
- **UI Changes**: Update `index.html` and `styles.css`, then wire up handlers in `main.ts`.

Maintainers rely on AI agents to follow these conventions and to always verify output against expected behaviors.
