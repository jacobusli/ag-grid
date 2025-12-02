# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Communication Guidelines

- **与用户交流**: 使用中文进行所有对话和交流
- **代码注释**: 所有代码注释必须使用日语

## Project Overview

This is a Vue 3 + TypeScript demo project showcasing AG Grid's multi-header functionality, built with Vite. The project demonstrates deeply nested column group headers (up to 10 levels deep) using the ag-grid-vue3 library.

## Development Commands

### Install Dependencies
```sh
npm install
```

### Development Server
```sh
npm run dev
```
Starts Vite dev server with hot-reload for development.

### Production Build
```sh
npm run build
```
Runs type-check and builds for production. This command uses `npm-run-all2` to execute type-checking and building in parallel.

### Type Checking Only
```sh
npm run type-check
```
Runs `vue-tsc --build` to check TypeScript types across the project.

### Build Without Type Checking
```sh
npm run build-only
```
Builds the project using Vite without type checking (faster for iteration).

### Preview Production Build
```sh
npm run preview
```
Previews the production build locally.

## Architecture

### Key Dependencies
- **ag-grid-vue3**: AG Grid integration for Vue 3 (v33.0.3)
- **vue**: Vue 3.5.13
- **vite**: Build tool and dev server
- **vue-tsc**: TypeScript type checker for Vue files
- **vite-plugin-vue-setup-extend**: Allows naming components in `<script setup>` using the `name` attribute

### Project Structure
- `src/main.ts`: Application entry point
- `src/App.vue`: Root component that renders the AG Grid demo
- `src/components/AgGridMutilHeaderDemo.vue`: Main demo component showcasing multi-header grid
- `src/assets/main.css`: Global styles including AG Grid header customization

### AG Grid Configuration

The project uses AG Grid's Community Edition with `AllCommunityModule` registered globally. Column definitions are structured with deeply nested `ColGroupDef` arrays to create the multi-header layout.

**Custom header classes:**
- `.header-up-extend`: Applied to empty placeholder headers (leftmost column groups), removes borders and resize handles
- `.header-up-data`: Applied to data column headers with light blue background, hides resize handles
- `.header-parent`: Applied to parent headers in the data hierarchy

### TypeScript Configuration

The project uses Vue 3's TypeScript setup with path aliases configured:
- `@/` maps to `src/` directory (configured in vite.config.ts)

### Vite Plugins
- `@vitejs/plugin-vue`: Core Vue 3 support
- `vite-plugin-vue-devtools`: Vue DevTools integration
- `vite-plugin-vue-setup-extend`: Enables component naming in `<script setup>` blocks using the `name` attribute

## Working with AG Grid

When modifying the grid:
- Column definitions use a mix of `ColDef` (leaf columns with `field` property) and `ColGroupDef` (parent groups with `children` array)
- The demo creates a 10-level deep header structure with three main column groups
- Row data is typed as `IRow[]` (note: the interface definition is missing in the current code)
- All AG Grid Community features are available via `AllCommunityModule`
