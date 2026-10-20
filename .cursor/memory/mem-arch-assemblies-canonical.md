# UniMate Project Memory Registry

Project-owned canonical registry. The filename follows the shared memory hook contract; this repository currently contains Python packages, not Unity assemblies.

## Project orientation

UniMate is the Python motion-generation and asset-processing backend for an intended Unity animation workflow. Start with the [Python project guide](../../docs/python-project-guide.md) and the [horizon vision](../plans/design/2026-10-20-unity-animation-horizon.md).

## Memory index

| Topic | File |
|---|---|
<!-- LOCAL-MEMORY-INDEX:BEGIN -->
| HUB: Project direction, ownership, setup, decisions, and session handoff | `mem-project-context.md` |
| Shared AI configuration ownership and upstream sync mechanics | `mem-shared-ai-config.md` |
<!-- LOCAL-MEMORY-INDEX:END -->

Read the matching memory on demand. Shared Claude prompt hooks route through this index; other clients need an explicit lookup. Playbooks are indexed in `.cursor/playbooks/README.md`.
