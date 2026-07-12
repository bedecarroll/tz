# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

TZ is a simple static website for converting natural language date/time strings to different timezones. Users can input phrases like "tomorrow at 3pm" or "next Friday" and see the converted time in their selected timezone.

## Build and Development Commands

- `bun install` - Install dependencies
- `bun run build` - Compile TypeScript to JavaScript (outputs to `dist/`)
- `bun run dev` - Watch mode for TypeScript compilation
- `bun run serve` - Start local development server on port 8000

The application runs entirely in the browser as a static site.

## Architecture

### Core Components

**DateTimeConverter** (`src/dateTimeConverter.ts`):
- Uses Sugar.js (loaded via CDN) for natural language date parsing
- Main method: `parseAndConvert(input, targetTimezone)` returns a `ConversionResult`
- Uses `Intl.DateTimeFormat` for timezone conversion and formatting
- Provides `getAllTimezones()` with fallback for older browsers

**AutocompleteInput** (`src/autocomplete.ts`):
- Generic autocomplete component for the timezone selector
- Handles keyboard navigation (arrow keys, Enter, Escape)
- Filters options based on user input and shows up to 10 results

**App** (`src/main.ts`):
- Main application controller that binds UI elements
- Defaults timezone input to 'America/Los_Angeles' (San Francisco)
- Handles user interactions and displays results

### Dependencies

- **Sugar.js**: Loaded via CDN for natural language date parsing
- **TypeScript**: Compiled to ES2020 modules for browser compatibility
- **Bun**: Package manager and task runner

### Key Design Decisions

- No bundler needed - uses ES modules directly in the browser
- External dependencies loaded via CDN to avoid Node.js module compatibility issues
- Timezone autocomplete uses browser's `Intl.supportedValuesOf('timeZone')` when available
- Results show converted time first, then original parsed date for reference