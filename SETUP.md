# One-time setup (macOS)

1. Install tools:
   xcode-select --install
   brew install cmake ninja qt git
   (Then run: brew --prefix qt   and make sure it is Qt 6.8 or newer.)
2. Create the repo:
   mkdir wordproc && cd wordproc && git init
   Copy everything from this kit into it (AGENTS.md, PROGRESS.md, docs/, .github/, .gitignore).
3. Add a LICENSE file with the GPL-3.0 text (https://www.gnu.org/licenses/gpl-3.0.txt).
4. git add -A && git commit -m "Project kit"
5. Push to a GitHub repo (needed so CI can verify Linux).
6. Open the folder in Codex desktop. Paste the Phase 0 prompt from docs/PROMPTS.md.
7. After each phase: read the diff, run the app yourself, check CI is green,
   commit, then open a fresh session for the next phase.

Optional Linux VM for visual checks: install UTM or Multipass, Ubuntu 24.04,
then: sudo apt install build-essential cmake ninja-build qt6-base-dev git
(Note: the package qt6-base-dev may be older than 6.8; CI is the source of truth.)

Tip: if CMake cannot find Qt on macOS, pass
-DCMAKE_PREFIX_PATH=$(brew --prefix qt)
