# Memory: UniMate Project Context

Updated: 2026-10-20. Project-owned durable summary of the initial setup and vision session. Facts below distinguish completed local actions from proposed future work.

## User preferences

- User enabled `$caveman` at full intensity: terse English, exact technical names, minimal filler. Persist until user requests normal mode. Use clear full wording when compression would create ambiguity. Write documentation, code, commits, and PR descriptions normally.
- Bias toward executing authorized work. Do not repeatedly ask for permission already given. Ask a focused question when a missing decision materially changes scope.
- No unsolicited subagents. Current shared rules explicitly prohibit delegation unless requested.
- Mermaid displayed labels must never contain `#`, even inside quotes. Use words such as “number” instead.
- User wanted AI configuration adopted before milestone planning. Later explicitly requested a horizon vision, a complete Python-side guide, and memory/playbook updates.

## Repository and Git ownership

- Workspace: `G:\Projects\UniMate` on Windows/PowerShell.
- Original public repository: `https://github.com/Friedrich-M/UniMate.git`.
- User account/fork: `HeldenChill/UniMate`.
- Verified local remotes: `origin` points to the user's fork; `upstream` points to Friedrich-M's repository, for both fetch and push URLs.
- Branch observed during initial setup: `Hung`. Inspect current branch before acting; this is historical context, not a requirement.
- User confirmed they could push after fork setup. The assistant configured remotes but did not create the GitHub fork through an authenticated tool or verify a remote push itself.
- Public visibility grants read access, not write access. User changes go to the fork; upstream changes are fetched from `upstream` and deliberately integrated into the chosen local branch.
- `gh` was unavailable and browser inventory was empty during setup. Authentication/tool availability may change; inspect rather than assume.
- Initial `.git/config` writes were denied by sandbox permissions; an authorized escalated `git remote` operation succeeded. Do not infer ordinary workspace file writes need the same escalation.

## Product direction and decisions

Ultimate aspiration: a Unity package that generates and controls character animation using a Python model backend across a language boundary. User compared the desired responsive experience to IK. This analogy does not establish that UniMate is a per-frame IK solver.

Initial practical direction: generate motion offline, export animation, and apply it through Unity's existing animation system. Unity Editor tooling and live generation can follow experiments. Model inference stays in Python; a small C# integration layer is expected for Unity.

The horizon is intentionally aspirational. The user accepts that the final target may never become usable in a real project and wants to go as far as evidence permits. Every stage should retain a useful result.

The [horizon plan](../plans/design/2026-10-20-unity-animation-horizon.md) records six stages: asset handoff, Editor authoring tool, game-useful clips, runtime generation, responsive continuous motion, and real-project trial. It sets decision gates rather than deadlines or promised performance. User acknowledged the vision and then requested the Python documentation. No detailed implementation milestone or runtime protocol has been approved or built.

## AI configuration adoption

- Source checkout: `G:\Unity\claude-unity-shared`.
- User explicitly selected **portable rules now**, deferring full Unity metadata and architecture setup.
- Installed 34 manifest entries whose bucket was `universal`, plus the shared base `.claude/settings.json`, into `.claude/` and `.cursor/`.
- Adoption was a selective file copy driven by the manifest, not a completed standard `sync.ps1 pull`. No automatic ongoing sync or source link was installed.
- Skipped templated `character-core-glue-split-refactor.md`: it describes unrelated `Hung.Character` and gameplay assembly architecture.
- No fabricated Unity version, assembly, locator, or integrity-check path was created. There is no `project.config.json` from this adoption and no installed Unity package guidance.
- Standard upstream `sync.ps1` requires `project.config.json` and would include the skipped template. Do not recommend blindly running it in this consumer. Review portable adoption scope or establish real Unity identity first.
- Universal files remain source-owned; put consumer-specific lessons in project-owned memories/playbooks. Do not modify shared copies casually because later adoption can overwrite them.
- Index checker reported zero findings after adoption. At that time the canonical memory index did not exist, so the memory injector had no routing to emit. The registry and project hub were added during the later memory-update task.
- Claude settings register a memory routing hook and a relevant-edit index check. These hooks are not automatically a Codex/Cursor integration. The hook's text also references `memory-first-workflow.md`, which was not among the manifested Universal rules; do not infer that absent rule was installed.

## Documentation and verified technical findings

- [Python project guide](../../docs/python-project-guide.md): repository-wide architecture, environment, formats, rig preparation, inference, constraints, mesh export, training, troubleshooting, and Unity boundary. Written from local source inspection; approximately 5500 words with five Mermaid diagrams. Local links and forbidden Mermaid character checks passed at creation.
- Plans/specs belong in `.cursor/plans/design/`; executable plans belong in `.cursor/plans/implement/`. Name files `YYYY-MM-DD-<topic>.md`. Python reference documentation currently lives under `docs/`; no universal `DOCS_DIR` value was established.
- `unimate/` owns learning/generation; `data_process/` owns asset/data preparation and mesh export. Follow nested `data_process/rig_preprocess/AGENTS.md` when changing or using that package.
- Sampled NPY arrays are denormalized `(F, J, 12)` motion features, not direct Unity transforms. Use existing recovery code and matched skeleton conditioning.
- Model tensors use `(B, J, 12, F)`. Features contain RIFKE positions, reordered 6D rotations, and local velocities. Root handling and rest-pose conventions matter.
- Checkpoint, resolved `config.json`, and `dataset_stats.npy` form a coupled experiment. Motion files, sample manifest, conditioning, and canonical mesh form a coupled export input.
- Preparation uses Y-up, +Z facing, centering, grounding, and diameter-2 scale. Correct Unity import and authored-scale restoration remain to be established.
- Released UniML3D models trained on up to 70 joints and accept at most 71 slots; inspect each experiment's actual limits. A typical full game rig may require simplification.
- Existing export path produces animated FBX and GLB through Python/Blender. There is no implemented Unity package, importer, persistent inference server, or gameplay bridge in this checkout at session end.
- Flow matching is selected by supplied recipes; diffusion support also exists. In-betweening, joint editing, and motion expansion are existing features, not evidence of a production continuous controller.
- Python 3.10, CUDA-targeted PyTorch, pinned `bpy`, `setuptools<81`, and `--no-build-isolation` are part of the repository environment recipe. Bash wrappers and PowerShell are different execution surfaces.
- No environment installation, model generation, Unity import, latency benchmark, or full native Windows compatibility validation was performed in this session. The guide's commands are references, not successful-run evidence.

## Next-session handoff

Read the horizon vision and Python guide before proposing an implementation milestone. Discuss the first bounded experiment with the user; likely input rig, environment availability, and Unity import target need concrete selection. Keep generated-animation quality, coordinate conversion, root motion, and deployment questions explicit. Update this hub when decisions change rather than treating tentative proposals as approved work.

Reusable procedure: [Project setup and Python-to-Unity exploration playbook](../playbooks/project-setup-and-unity-exploration.md).
