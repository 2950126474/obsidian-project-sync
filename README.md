# Obsidian 项目同步 · Obsidian Project Sync

一个让 Codex 把项目进展、决定和待办整理到 Obsidian 的技能。直接编辑 Markdown 文件，保留已有笔记和用户修改，并核对保存结果及链接。

**适合这样的场景：项目工作已经在推进，但 Obsidian 里的项目记录还停在上周。**

## 能做什么

- 把已经确认的项目进展更新到现有笔记。
- 支持“项目文件夹本身就是 vault”和“项目与中央知识库分开”两种结构。
- 写入前确定资料和目标位置，重要覆盖前备份，写入后核对内容。
- 保留项目之间的边界，发现记录冲突时不盲目合并。
- 检查笔记和附件链接，避免同名笔记指向不清。
- 小改动只更新相应部分，不强制生成整套项目管理页面。

这是按请求执行的技能，不是 Obsidian 插件，也不是常驻文件同步程序。

## 安装

在提供 `skill-installer` 的 Codex 环境中发送：

```text
请使用 skill-installer，从以下地址安装 obsidian-project-sync：
https://github.com/2950126474/obsidian-project-sync/tree/main/skills/obsidian-project-sync
```

也可以下载本仓库，将 `skills/obsidian-project-sync` 文件夹复制到 Codex 的用户技能目录，通常为 `~/.codex/skills/`，Windows 对应 `%USERPROFILE%\.codex\skills\`；设置了 `CODEX_HOME` 时使用其下的 `skills/`。已有同名技能时，先比较或备份再更新。

建议安装后新开一个项目聊天。真正的技能入口是 [SKILL.md](skills/obsidian-project-sync/SKILL.md)，不是仓库根目录。

## 怎么用

第一次使用时，告诉 Codex 项目和知识库的位置，并说明想更新什么：

```text
把这个项目最近确认的进展和下一步同步到我的 Obsidian。
项目位置：<你的项目目录>
知识库位置：<你的 vault 目录>
请更新已有项目概览，保留我手写的内容。
```

如果目录已经明确，直接说：

> 帮我把今天确认的结果更新到 Obsidian 项目笔记。

项目本身就是 vault 时：

> 这个项目文件夹就是我的 Obsidian vault，更新现有项目概览，不需要另外复制一份。

需要明确调用技能时：

```text
使用 $obsidian-project-sync，把当前项目进展同步到已指定的 Obsidian 知识库。
```

目的地不明确时，AI 会先询问。目的地和写入范围已经确认时，不应反复要求相同授权。

## 一次更新是什么样的

以下为示例，不是实际项目记录：

1. 读取项目记录，确认某项功能已经完成，而另一项仍只是计划。
2. 找到 vault 中现有的项目概览，保留个人批注。
3. 备份需要覆盖的内容，更新已完成事项和下一步。
4. 核对写入内容及相关链接，告知改了哪些文件、备份在哪里。

原始代码、大型数据和模型文件通常留在工程目录，通过链接关联；不会因为“同步进展”而整份复制项目。

## 使用条件与边界

- Codex 需要能访问本地项目和 vault 文件；技能本身不提供文件访问权限。
- 不需要额外 Obsidian 插件、API key 或付费 Obsidian Sync。
- “已写入本地文件”不代表“已同步到云端或其他设备”。
- 不自动配置 Obsidian Sync、Git、OneDrive 等同步服务。
- 不默认修改 `.obsidian` 设置，也不自动删除原始资料。
- 默认通过文件核对结果；只有实际检查过界面时才会声称已验证 Obsidian 显示。
- 自然语言触发和修改质量取决于模型及运行环境；重要记录应复核。

## 当前状态

早期公开试用版。技能结构已通过校验，提供了[常见场景和边界检查](skills/obsidian-project-sync/references/examples.md)。本次发布做了规则走查和文件检查，尚未完成跨平台、跨 vault 的独立行为评测。

## 反馈与参与

欢迎通过 [Issues](https://github.com/2950126474/obsidian-project-sync/issues) 留言、报告问题或讨论使用体验，也欢迎 Pull Request。

反馈时说明请求、预期和实际行为即可。尤其欢迎：重复确认、覆盖了手写内容、同名链接指错位置、记录冲突处理不当、只写本地却声称云同步成功等案例。请移除私人笔记、账号、密钥和未公开项目内容。

## English overview

A Codex skill for updating project records in an Obsidian vault by editing Markdown files. It resolves the intended source and destination, preserves user edits, backs up material overwrites, and verifies saved content and links. Supports both project-as-vault and separate central-vault workflows. It does not provide background synchronization or configure Obsidian Sync.

## License

[MIT](LICENSE).