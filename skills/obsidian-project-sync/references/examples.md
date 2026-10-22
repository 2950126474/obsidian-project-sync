# First-use examples and pilot checks

These examples describe expected behavior, not completed evaluations.

## A separate central vault

User: “把这个项目的最新进展同步到我的 Obsidian，仓库位置是……，知识库位置是……。”

Read the relevant project records and existing destination notes. Summarize verified progress, unresolved issues and next actions in the existing project note. Keep raw code and data in the project. Back up before material overwrites, then verify saved text and links. Do not invent outcomes from planned tasks.

## The project itself is a vault

User: “这个项目文件夹就是我的 Obsidian vault，更新项目概览。”

Update its existing overview in place. Do not create another central-vault copy. Preserve the user's edits and connect to existing notes with unambiguous links.

## The destination is unclear

User: “帮我同步一下笔记。” Two plausible vaults are present and neither has been designated.

Ask which destination to use before writing. Do not choose solely by modification time or by the presence of `.obsidian`.

## A small update with established access

User: “在刚才的项目笔记里加上今天确认的下一步。”

Reuse the established destination and write scope. Update that section, preserve the rest, and verify. Do not ask for the same permission again or generate an entire management structure.

## Boundary checks

- “润色这一段 Markdown”：ordinary text editing does not require the synchronization workflow.
- Source and vault disagree: identify the discrepancy, prefer explicit decisions and underlying evidence, and do not silently merge incompatible conclusions.
- Same attachment name but different content: preserve both originals; resolve the destination collision and update links.
- Only files were inspected: report local write verification, not UI rendering or cloud synchronization success.
