# Project Relay｜项目接力

[English](README.md) | 简体中文

一个简洁、仅含指令的 skill，用于在 Codex 和 Claude 之间继续同一个项目。用一份项目记录保存关键数据与算法变化、阶段性成果及下一步。

**支持 Codex → Claude、Claude → Codex，以及同一个工具在后续会话中继续。**

## 工作方式

助手在项目根目录维护 `PROJECT_STATE.md`，或复用已有的同类进度文档，记录：

- 数据位置、版本、范围与重要预处理。
- 当前方法、代码入口、参数及重要变化的原因。
- 阶段性产物，以及实际通过、未通过或尚未完成的验证。
- 具体下一步、前置条件及完成判据。

接手者读取记录、核对相关文件，然后继续已有工作。仅在重要变化、阶段完成、阻塞和交接时更新。技能不会传输文件或在后台运行；双方都需要能够访问最新记录和相关项目文件。

## 项目级安装

使用 Release 附件 **`project-relay.zip`**，其中包含可安装的技能目录。GitHub 自动生成的 **Source code (zip)** 是整个仓库，目录结构不同。

把 `project-relay.zip` 放到目标项目根目录，在 Codex 或 Claude Code 中打开该项目，发送：

```text
请把当前项目根目录中的 project-relay.zip 安装为本项目使用的技能。
确认项目根目录，并检查压缩包中的 project-relay/SKILL.md。
Codex 使用 .agents/skills/project-relay/SKILL.md。
Claude Code 使用 .claude/skills/project-relay/SKILL.md。
只安装当前工具对应的一份，避免重复嵌套 project-relay 文件夹。
如果已有同名技能且内容相同则跳过；不同则先备份到 work/skill-backups/，再更新。
保留 ZIP 和包内的许可证文件，不修改全局配置。
检查安装结构及 SKILL.md 的 name、description，报告最终路径。
本次只安装，不调用技能，不创建项目记录，也不开始项目任务。
```

手动安装时，将本仓库 `skills/project-relay/` 内的文件复制到对应目标目录：

| 工具 | 相对目标项目根目录的安装位置 |
| --- | --- |
| Codex | `.agents/skills/project-relay/` |
| Claude Code | `.claude/skills/project-relay/` |

按实际使用的工具分别安装，两份技能共用同一份项目记录。如果未识别技能，重新打开会话或重启工具。技能发现和调用方式见 [Codex 官方文档](https://learn.chatgpt.com/docs/build-skills)和 [Claude Code 官方文档](https://code.claude.com/docs/en/skills)。

## 调用

在任一工具中发送：

```text
使用 project-relay 技能，读取项目状态记录，核对下一步相关的数据、代码和成果，然后继续该步骤。完成一个阶段或本次工作结束时更新同一份记录。
```

Codex CLI 和 IDE 还支持 `$project-relay`；Claude Code 支持 `/project-relay`。

切换工具前发送：

```text
使用 project-relay 技能准备交接。更新项目记录，写明关键数据和算法变化、阶段性成果、实际验证结果、未解决问题及下一步。本次只整理交接，不启动新任务。告诉我记录和所需文件的位置。
```

把更新后的记录和相关文件提供给接手工具，再使用上面的继续提示词。两个交接方向的步骤相同。

## 文档与语言

- [English user guide](docs/USER_GUIDE.en.txt)：安装和 15 组可复制提示词，涵盖首次使用、只读查看、阶段成果、中断恢复、双向交接和换电脑。
- [中文使用说明](docs/USER_GUIDE.zh-CN.txt)：与英文对应的中文指南。
- [English skill](skills/project-relay/SKILL.md) 和[中文技能原文](docs/SKILL.zh-CN.md)：对应的技能指令和项目状态模板。
- [Release instructions](docs/RELEASING.md) 和[中文发布说明](docs/RELEASING.zh-CN.md)。
- [Changelog](CHANGELOG.md) 和[中文更新记录](CHANGELOG.zh-CN.md)。

可安装技能默认使用英文；仍可用中文发送提示词和维护项目记录。如果希望技能指令也使用中文，将 `docs/SKILL.zh-CN.md` 作为安装目录中的 `SKILL.md`，保持目录名称不变。每个工具安装一种语言，避免重复技能条目。两者是同一工作方式的对应翻译。

普通 Claude 网页版或桌面聊天应使用其自定义技能上传入口，并提供项目记录及相关文件。本地安装 `.claude/skills/` 不会使网页聊天获得项目目录访问权限。参见 [Claude 官方说明](https://support.claude.com/en/articles/12512180-use-skills-in-claude)和使用说明第九节。

## 范围与贡献

无需运行依赖、脚本、hooks 或调度系统。这是按先后顺序接续项目的工作方式，不提供自动同步或并发编辑协议。

遇到问题可提交 issue，说明工具、安装位置、预期行为，并提供移除项目隐私信息的最小示例。贡献应保持技能聚焦，并同步更新对应中英文文档。由仓库所有者及贡献者维护。

## 许可证

技能及其文档采用 [MIT 许可证](LICENSE)。版权署名为 Copyright (c) 2026 CJ。可安装 ZIP 中也包含许可证。
