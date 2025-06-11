# Vue 3 + TypeScript + Vite

This template should help get you started developing with Vue 3 and TypeScript in Vite. The template uses Vue 3 `<script setup>` SFCs, check out the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

Learn more about the recommended Project Setup and IDE Support in the [Vue Docs TypeScript Guide](https://vuejs.org/guide/typescript/overview.html#project-setup).

# iOS/Android Multi-file Editor (Vue 3 + TypeScript + Pinia)

## Overview
This webapp lets you upload, view, and edit multiple iOS .strings or Android string.xml files (multi-language) side-by-side. You can edit all string values, paste translations, and export the files back. If all files have the same value for a key, only one row is shown. Robust handling for missing/empty fields. No search/filter logic.

## Features
- Upload multiple iOS .strings or Android string.xml files (same keys/structure)
- View and edit all string values side-by-side
- Collapse/expand grouped keys (if any)
- Paste per-field for multi-language input (e.g. from Google Sheet)
- Export all files after editing (export will match the file type)
- Handles undefined/empty fields gracefully

## How to use
1. Upload multiple .strings or .xml files (e.g. en.strings, th.strings, en.xml, th.xml)
2. Click Ready to view and edit all keys/values side-by-side
3. Edit values directly, or use Paste to fill multiple languages at once
4. Export all files when done (export will match the file type)

## Tech Stack
- Vue 3 + TypeScript + Pinia + Vite

---

*This project was bootstrapped and iteratively built with GitHub Copilot.*

# iOS/Android Multi-file Editor

A modern webapp for editing multiple iOS .strings or Android string.xml files side-by-side, with advanced features for translation, review, and export.

## How to Use

1. **Choose Files:** Select multiple iOS .strings or Android string.xml files (one per language, same keys).
2. **Ready:** Click **Ready** to load and edit all keys/values side-by-side.
3. **View:** Use **See All**/**Paging** to switch key views. Use **Search** to filter. Drag column headers to re-order languages.
4. **Edit:** Edit values directly or use **Paste** per row for quick input.
5. **Export:** Use floating buttons to export all, changed, or keep order. Export will match the file type (iOS/Android).
6. **Back:** Use the floating **Back** button to restart (confirmation required).

### Highlight Legend
- 🟩 **Edited (green):** This row has been changed from the original value.
- 🟨 **Duplicate (yellow):** This row has duplicate values across languages.
- 🟩 **All-equal (light red):** All values in this row are identical.

### Tips
- All processing is local. No files are uploaded to a server.
- The key column scrolls if long. Use the same keys in all files for best results.
- You can add new keys and values for all languages using the form above the table.
- You can re-order language columns by dragging the column headers.
- Supports both iOS .strings and Android string.xml formats.

---

## Development

- Install dependencies: `npm install`
- Run locally: `npm run dev`
- Build for production: `npm run build`
- Deploy to GitHub Pages: `npm run deploy`

---

For more details, see the in-app instructions or contact the maintainer.
