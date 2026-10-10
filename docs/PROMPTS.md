# Prompts to paste into Codex

Start a FRESH Codex session for each prompt. Commit after each one and read the diff.

## Phase 0
Read AGENTS.md and docs/ROADMAP.md. Do Phase 0 only. Do not write application
code outside spikes/. Inspect my environment (macOS) and tell me what is missing
and how to install it. Build the pagination and DOCX/ODT spikes described in the
roadmap. Write findings and tradeoffs to docs/DECISIONS.md, list the 5 hardest
risks, and update PROGRESS.md. Finish with the report format from AGENTS.md.

## Phase 1
Read AGENTS.md, docs/ROADMAP.md, PROGRESS.md, docs/DECISIONS.md. Implement
Phase 1 only. Every checkbox in the roadmap's Phase 1 must be satisfied or
explicitly reported as not done. Do not start Phase 2.

## Phase 2
Same as the Phase 1 prompt, but for Phase 2. Before coding, propose the class
layout for the editor module in 10 lines or fewer and wait for my approval.

## Phase 3
Same pattern, Phase 3. Report any ribbon limitation you hit and what you chose.

## Phase 4
Same pattern, Phase 4. Include a schema-version field and a test that loads an
older-version fixture.

## Phase 5 (pagination)
Read AGENTS.md, docs/ROADMAP.md, docs/DECISIONS.md (especially the Phase 0
pagination findings). Before writing code, write a design in docs/DOCUMENT_ENGINE.md
covering how pages are computed, how page breaks, tables and images are handled,
and what is only visual simulation. Stop and ask me to approve the design. After
approval, implement incrementally with tests for page count and break positions.

## Phase 6
Same pattern, Phase 6.

## Phase 7
Same pattern, Phase 7. Use the DOCX library chosen in DECISIONS.md. Build
COMPATIBILITY.md from actual round-trip test results, not assumptions.

## Phase 8
Same pattern, Phase 8. Check licenses of any spellcheck dictionaries.

## Phase 9
Same pattern, Phase 9. Do not claim a package works on a platform unless CI or a
real run proved it.

## Phase 10
Same pattern, Phase 10. Profile before optimizing and report numbers.

## Useful extra prompts
- Explain src/<module>/ to me like I'm a beginner, then suggest 3 experiments.
- Review the last commit for bugs, ownership problems, and platform assumptions.
- Update LEARNING_GUIDE.md for what changed in this phase.
