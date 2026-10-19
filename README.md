# Project Relay

English | [简体中文](README.zh-CN.md)

A small, instruction-only skill for continuing the same project across Codex and Claude. Keep key data and algorithm changes, milestone results, and the next step in one project record.

**Codex → Claude, Claude → Codex, or the same tool in a later session.**

## How it works

The assistant maintains `PROJECT_STATE.md` at your project root, or reuses an equivalent progress document. It records:

- Data locations, versions, scope, and important preprocessing.
- Current methods, code entry points, parameters, and reasons for important changes.
- Milestone outputs and what actually passed, failed, or remains unvalidated.
- The next concrete step, prerequisites, and completion criteria.

The next assistant reads that record, checks relevant files, and continues existing work. Updates happen at meaningful changes, milestones, blockers, and handoffs. The skill does not transfer files or run in the background. Both tools need access to the latest record and relevant project files.

## Install in a project

Use the **`project-relay.zip` release asset**, which contains the installable skill folder. GitHub's automatically generated **Source code (zip)** contains the whole repository and has a different layout.

Place `project-relay.zip` in your target project's root, open that project in Codex or Claude Code, and send:

```text
Install project-relay.zip from the current project root as a project-local skill.
Confirm the project root and inspect project-relay/SKILL.md in the archive.
For Codex, use .agents/skills/project-relay/SKILL.md.
For Claude Code, use .claude/skills/project-relay/SKILL.md.
Install only the copy for the current tool, without an extra nested project-relay folder.
If the destination skill already exists and matches, skip it. If it differs, back it up under work/skill-backups/ before updating it.
Keep the ZIP and any bundled license file. Do not change global configuration.
Verify the installed layout and the name and description in SKILL.md; report the installed path.
Only install the skill. Do not invoke it, create a project record, or start project work.
```

For a manual installation, copy the contents of this repository's `skills/project-relay/` into the appropriate destination folder:

| Tool | Destination, relative to the target project root |
| --- | --- |
| Codex | `.agents/skills/project-relay/` |
| Claude Code | `.claude/skills/project-relay/` |

Install for each tool you use. Both copies share the same project record. If the skill does not appear, reopen the session or restart the tool. See the [Codex documentation](https://learn.chatgpt.com/docs/build-skills) and [Claude Code documentation](https://code.claude.com/docs/en/skills) for discovery and invocation details.

## Use it

In either tool, ask:

```text
Use the project-relay skill. Read the project record, check the data, code, and results relevant to the next step, then continue from that step. Update the same record when a stage finishes or the session ends.
```

Codex CLI and IDE also support `$project-relay`; Claude Code supports `/project-relay`.

Before switching tools:

```text
Use the project-relay skill to prepare a handoff. Update the project record with key data and algorithm changes, milestone results, actual validation results, unresolved issues, and the next step. Only prepare the handoff; do not start a new task. Tell me where the record and required files are located.
```

Provide the updated record and relevant files to the receiving tool, then use the continuation prompt above. The same sequence works in either direction.

## Documentation and languages

- [English user guide](docs/USER_GUIDE.en.txt): installation and 15 copyable prompts, including first use, read-only status, milestones, interruptions, both handoff directions, and moving computers.
- [中文使用说明](docs/USER_GUIDE.zh-CN.txt): the corresponding Chinese guide.
- [English skill](skills/project-relay/SKILL.md) and [中文技能原文](docs/SKILL.zh-CN.md): corresponding instructions and project-state templates.
- [Release instructions](docs/RELEASING.md) and [中文发布说明](docs/RELEASING.zh-CN.md).
- [Changelog](CHANGELOG.md) and [中文更新记录](CHANGELOG.zh-CN.md).

The installable skill is in English. You can still send prompts and maintain project records in Chinese. For Chinese skill instructions, use `docs/SKILL.zh-CN.md` as the installed `SKILL.md`, keeping the same folder name. Install one language per tool to avoid duplicate skill entries. These are translations of the same workflow.

For regular Claude web or desktop chat, use its custom-skill upload interface and provide the project record and relevant files. Installing `.claude/skills/` locally does not give a web chat access to your project. See the [Claude guide](https://support.claude.com/en/articles/12512180-use-skills-in-claude) and section 9 of the user guide.

## Scope and contributions

No runtime dependencies, scripts, hooks, or orchestration are required. This is a sequential project handoff workflow. It adds no automatic synchronization or concurrent editing protocol.

For questions or problems, open an issue with the tool, installation path, expected behavior, and a small example with private project information removed. Contributions should keep the skill focused and update the corresponding English and Chinese documents together. Maintained by the repository owner and contributors.

## License

The skill and its documentation are licensed under the [MIT License](LICENSE). Copyright (c) 2026 CJ. The installable ZIP also includes the license.
