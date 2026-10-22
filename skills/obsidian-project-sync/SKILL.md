---
name: obsidian-project-sync
description: Safely synchronize, back up, organize, or connect project records with an Obsidian vault by editing the underlying Markdown files directly. Use when the user asks to update or sync Obsidian project notes, establish the authoritative vault for a project, reconcile duplicate project copies, create project overviews/timelines/action lists/experiment indexes, or verify that an Obsidian write succeeded. Support both a project directory that is itself a vault and a separate engineering directory synchronized to a central vault. Do not trigger for ordinary Markdown editing that has no Obsidian or project-record synchronization intent.
---

# Obsidian Project Sync

Treat Obsidian as a Markdown repository. Edit files directly; use UI automation only for settings, plugins, or actions that cannot be performed through files.

## Start small

Use the current conversation and relevant project records to identify what the user wants synchronized. For a first use, resolve the project source, destination vault and intended notes; ask one concise question only for information that is missing or genuinely ambiguous. Do not scan unrelated folders or require the user to repeat a known vault path.

For a small update, read the existing target note, preserve unrelated content, update the relevant section and verify the saved text and links. Do not create a full dashboard, timeline, task board and experiment index unless the request needs them. Read [examples.md](references/examples.md) for common first-use scenarios and pilot checks.

## Resolve authority before writing

1. Locate the engineering project and all plausible Obsidian copies.
2. Detect the topology:
   - **Project is the vault:** the project root or an intended ancestor contains `.obsidian` and project evidence and notes share one tree.
   - **Separate central vault:** engineering evidence lives elsewhere and curated notes live under a project folder in a shared vault.
3. Determine the authoritative project record from explicit user instruction, canonical markers, current activity, completeness, and project context. The presence of `.obsidian` alone is evidence, not proof.
4. Treat same-named folders, mirrors, exports, and old sync directories as non-authoritative until verified.
5. If authority or destination remains ambiguous, stop before writing and ask the user to choose.

Use project-scoped markers when helpful:

```yaml
authority: canonical
vault_path: D:\path\to\vault
```

Mark retained copies as historical or navigation-only. Never delete or merge an old copy merely because a canonical location was selected.

## Preserve content boundaries

- Let the applicable project workflow decide what conclusions and evidence belong in the notes; this skill controls how they are synchronized.
- Keep raw code, datasets, model weights, images, predictions, and machine-generated results with the engineering project. Link to them from Obsidian instead of duplicating large artifacts.
- Store curated project state in notes such as project overview, timeline, action list, experiment index, decision records, and experiment notes.
- Preserve project-specific isolation rules. Never merge similarly named topics across projects without explicit authorization.
- Never write API keys, passwords, tokens, cookies, or sensitive source data into notes.
- Distinguish a local Vault write from Obsidian Sync, OneDrive, Git, or other cloud synchronization.

## Synchronize safely

1. Read the target notes and inspect nearby structure, frontmatter, links, and user changes.
2. Resolve the exact files to create or update. Do not modify `.obsidian` unless explicitly requested.
3. Before overwriting material content, copy the original target files to a timestamped, non-overwriting backup under the engineering project or another confirmed backup location. Preserve source-relative paths or prefix source identities so same-named files cannot overwrite each other in a flat backup.
4. Prepare edits in a writable staging directory when the vault is outside the active workspace.
5. Use existing user authorization and available filesystem permissions. Do not ask again for an already authorized write. Request only genuinely missing access or clarification of an ambiguous destination; if the environment prevents access, report the exact blocker.
6. Apply only the scoped Markdown changes. Preserve unrelated edits and existing note organization.
7. Compare staged and written files using SHA-256 or exact content checks.
8. Write or retain a synchronization manifest containing source, target, operation type, pre-write hash, post-write hash, backup path, and timestamp when multiple files or material conclusions change.
9. Report the authoritative location, changed files, backup location, verification result, and any copies deliberately left untouched.

Verify relative Markdown links and Obsidian wikilinks against the destination vault, including referenced attachments. When duplicate note names make a wikilink ambiguous, use a vault-relative target. Preserve heading/block anchors; report anchors that cannot be verified. If an attachment must be copied, check for collisions and preserve the original. Do not claim an Obsidian UI or cloud-sync check from filesystem verification alone; report which checks actually ran. Opening Obsidian is useful when requested or needed to resolve a rendering issue, not a mandatory step for every small text update.

For a new note, record why it exists and connect it with Obsidian links. For an existing overview, timeline, action list, or index, update it in place instead of creating competing variants.

Use this record behavior unless the project defines a stricter rule:

- project control page and current task plan: update current state in place;
- timeline and research log: append dated decisions or milestones;
- experiment record: create one immutable evidence note per experiment, then add later corrections as dated amendments;
- raw outputs and large artifacts: keep outside the vault and link to their verified locations.

Before synchronization, detect conflicts between the control page, task plan, experiment records, and vault copy. Do not decide scientific truth from file modification time alone. Prefer frozen protocols and primary experiment evidence, report unresolved conflicts, and avoid propagating a stale conclusion.

## Choose synchronization cadence

Synchronize at durable checkpoints such as:

- completion of an experiment or evaluation;
- formation of a verified conclusion;
- a change in plan, baseline, or project boundary;
- preparation for handoff, restart, or context change.

Do not rewrite the vault after every conversational message unless the user explicitly requests live logging.

## Handle each topology

### Project is the vault

- Write notes inside the project tree.
- Prefer relative links to project evidence.
- Treat the project homepage and task board as navigation surfaces.
- Avoid creating a second full copy in a central vault; use a navigation note there only when requested.

### Separate central vault

- Keep reproducible evidence in the engineering directory.
- Write curated notes into the confirmed project folder in the central vault.
- Record stable links or paths back to the evidence.
- Back up target notes before synchronized overwrites and verify the resulting files.

## Respect adjacent skills

- Project-specific skills and explicit user instructions define project content and special boundaries.
- Research workflow skills define evidence quality, evaluation, and research judgment.
- Skill-maintenance workflows govern changes to this skill itself.
- UI-control skills are a fallback for Obsidian settings and plugin operations, not routine Markdown writes.

Use this precedence when instructions overlap:

1. explicit user instruction;
2. verified project-specific authority and boundaries;
3. applicable project or research workflow;
4. this synchronization procedure.
