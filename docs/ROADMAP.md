# Roadmap

Rule: finish a phase (all boxes checked, tests green, PROGRESS.md updated)
before starting the next one.

## Phase 0 - Environment and risk spikes
- [ ] Environment report (OS, compiler, CMake, Ninja, Qt version)
- [ ] spikes/pagination: QTextDocument with page size, ~50 pages, a table, an image;
      report how to read page count and page boundaries, and where Qt fails
- [ ] spikes/docx: compare DOCX/ODT options with license, maturity, integration cost
- [ ] Findings in docs/DECISIONS.md; 5 hardest risks listed
- [ ] Decide: ribbon custom widget vs. tabbed toolbar (document tradeoff)

## Phase 1 - Native foundation
- [ ] CMake project with presets; builds on macOS
- [ ] Main window: menu bar, toolbar, status bar, document tabs
- [ ] File > New opens a tab with a QTextEdit placeholder
- [ ] Standard shortcuts via QKeySequence::StandardKey
- [ ] macOS .app bundle runs, quits and closes correctly
- [ ] Qt Test smoke tests under CTest (offscreen)
- [ ] GitHub Actions: macos-latest + ubuntu-latest build and test
- [ ] BUILDING.md, ARCHITECTURE.md (first version), PROGRESS.md

## Phase 2 - Text editing
- [ ] Editor widget wrapping QTextDocument/QTextCursor
- [ ] Insert, delete, select, navigate, copy/cut/paste, undo/redo
- [ ] Bold, italic, underline, strikethrough, font family/size, color, highlight
- [ ] Unicode and IME tested with sample multilingual text
- [ ] Unit tests for formatting commands

## Phase 3 - Interface
- [ ] Ribbon-style tabs (Home first), functional controls only
- [ ] Font, paragraph, alignment, list, indent, spacing controls
- [ ] Light/dark theme following system, manual override
- [ ] Icons from an open-licensed set (record license)
- [ ] Shortcuts documented

## Phase 4 - Persistence
- [ ] Native format (zip container + JSON/XML, versioned schema)
- [ ] Open/save with atomic replacement, round-trip tests
- [ ] Recent files, autosave (configurable), crash recovery
- [ ] SQLite for preferences/history (only if justified in DECISIONS.md)

## Phase 5 - Page layout (hardest)
- [ ] Page sizes A4/Letter/Legal, orientation, margins
- [ ] Pages displayed as real pages with correct flow and page breaks
- [ ] Page numbering, zoom, multi-page scrolling, print preview
- [ ] DOCUMENT_ENGINE.md explains visual simulation vs true pagination
- [ ] Documented limitations (tables across pages, widows/orphans)
- [ ] Pagination benchmark

## Phase 6 - Advanced content
- [ ] Tables (insert, edit, merge where Qt allows), images, hyperlinks
- [ ] Lists, named styles, heading styles, document outline sidebar

## Phase 7 - File compatibility
- [ ] PDF export respecting page size and margins
- [ ] TXT import/export
- [ ] DOCX import/export via the library chosen in Phase 0
- [ ] ODT investigated, implemented if feasible
- [ ] docs/COMPATIBILITY.md matrix + round-trip tests

## Phase 8 - Advanced word processing
- [ ] Headers/footers, page numbers, table of contents
- [ ] Find and replace, word/character count
- [ ] Spellcheck (e.g., Hunspell, license checked), comments if feasible

## Phase 9 - Packaging
- [ ] macOS .app (macdeployqt), DMG instructions
- [ ] Linux AppImage or Flatpak, built in CI
- [ ] Windows notes only
- [ ] Deployment docs

## Phase 10 - Quality
- [ ] Benchmarks: load, save, insert, scroll, pagination, PDF export
- [ ] Sanitizer runs (ASan/UBSan), leak checks
- [ ] Large-document tests, accessibility pass, UI polish
