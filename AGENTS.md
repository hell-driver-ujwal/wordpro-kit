# AGENTS.md

## Project
Cross-platform native word processor. C++20, Qt 6 Widgets, CMake + Ninja,
Qt Test + CTest. Not Electron, not a web view, not a browser-based editor.

## Targets
- Primary: macOS (Apple Silicon). Equal priority: Linux (Ubuntu, Fedora).
- Windows: keep code portable, but do no Windows packaging work yet.
- Platform-specific code lives only in src/platform/ behind interfaces.
- Linux is verified only via GitHub Actions CI or a Linux VM. Never claim
  Linux (or Windows) works unless a real run on that platform passed.

## License and dependencies
- App license: GPL-3.0-or-later. Dependencies must be GPL-compatible.
- Qt 6.8 LTS, LGPL modules only (Core, Gui, Widgets, PrintSupport, Test),
  linked dynamically. No GPL-only or commercial-only Qt modules.
- Record every third-party dependency and its license in docs/DEPENDENCIES.md.
- No proprietary SDKs, no mandatory cloud or internet. No Microsoft code,
  icons, or branding.

## Workflow rules
- Read docs/ROADMAP.md and PROGRESS.md before starting.
- Work on ONE phase at a time. Never start the next phase unprompted.
- Stop and ask before big architectural changes; record them in docs/DECISIONS.md.
- Commit-sized changes. Do not rewrite unrelated files.

## Code rules
- Modern C++20, RAII, smart pointers, const correctness, no raw owning pointers.
- Document model logic separate from Qt widgets where practical.
- One responsibility per class; keep files under ~400 lines.
- Comment non-obvious algorithms and state who owns what.
- No hardcoded paths, fonts, or separators. Use Qt abstractions.
- No fake functionality or placeholder buttons that do nothing silently:
  unfinished features must be hidden or visibly marked "not implemented".
- No silent loss of document content. Warn when a format cannot preserve something.
- Never export HTML renamed to .docx. Never claim perfect Word compatibility;
  maintain docs/COMPATIBILITY.md with a tested matrix.
- Use atomic file replacement (write temp, then rename) when saving.

## Verification (end of every task)
1. cmake -S . -B build -G Ninja && cmake --build build
2. QT_QPA_PLATFORM=offscreen ctest --test-dir build --output-on-failure
3. Update PROGRESS.md (done / not done / unverified) and docs/DECISIONS.md
4. Confirm .github/workflows/ci.yml still covers macOS and Ubuntu
5. Final report: what was implemented, how it works, key files, how to run,
   what the student should study, remaining limitations (including what was
   NOT verified on each platform).

## Audience
The user is a student learning native desktop development. Prefer clarity over
cleverness. Explain design choices. Keep LEARNING_GUIDE.md current with
small experiments the student can try.

## Priorities
- Must have: editing, formatting, real pagination, native format, PDF and TXT export, basic DOCX
- Important: tables, images, lists, styles, find/replace, autosave/recovery, themes
- Stretch: ribbon polish, ODT, citations, comments, spellcheck, Flatpak/AppImage
