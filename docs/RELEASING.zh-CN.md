# 在 GitHub 发布 Project Relay

[English](RELEASING.md) | 简体中文

本说明介绍如何维护和发布 Project Relay 版本。准备本地文件本身不代表已经发布仓库、安装技能或创建 GitHub Release。

## 发布哪些内容

将准备好的 `project-relay/` 源码目录内的内容作为仓库根目录。保留 `README.md`、`README.zh-CN.md`、`skills/`、`docs/`、更新记录和隐藏配置文件之间的相对位置，并包含根目录的 `LICENSE`。不要上传上级工作目录或私人项目记录。

英文可安装技能位于 `skills/project-relay/SKILL.md`，对应中文原文位于 `docs/SKILL.zh-CN.md`。中英文 TXT 使用说明各含 15 组提示词，顺序相同。编辑时同步维护这些对应文件。

## 发布前

1. 审核中英文内容。本版本采用所有者选定的 MIT 许可证。仓库根目录和分发的技能目录均保留完全相同的许可证副本，并保留版权及许可声明。
2. 核对 `name: project-relay` 与技能目录名称一致，description 存在，模板和指令完整。
3. 检查文档相对链接、UTF-8 文本、两个安装路径及压缩包结构。需要验证实际应用加载时，可在一次性测试项目中安装测试。
4. 任何编辑后重新打包并生成校验和。不要把静态包检查称为 Codex 或 Claude 行为验证。

## Release 附件

本次交付另外提供以下文件，供上传为 Release 附件：

- `project-relay.zip`：英文可安装技能目录及 MIT 许可证。包内路径必须为 `project-relay/SKILL.md` 和 `project-relay/LICENSE`，不能是 `skills/project-relay/SKILL.md`，也不能重复嵌套目录。
- `project-relay-user-guide.en.txt`：`docs/USER_GUIDE.en.txt` 的完全相同副本，供直接下载。
- `project-relay-user-guide.zh-CN.txt`：`docs/USER_GUIDE.zh-CN.txt` 的完全相同副本，供直接下载。
- `SHA256SUMS.txt`：以上三个文件的 SHA-256 校验和。

手动重新打包时，将 `skills/` 内的 `project-relay` 文件夹压缩，保留该文件夹作为包内顶层目录。按上面的名称复制两份指南，再使用当前平台的 SHA-256 工具重新生成校验和。GitHub 自动生成的源码包是仓库快照，不能代替这个安装 ZIP。

单独提供的 `project-relay-github.zip` 是供所有者使用的完整交付包，包含 `project-relay/` 源码目录和 `release-assets/`。解压后将 `project-relay/` 内的内容发布为仓库，将 `release-assets/` 内的文件上传为 Release 附件。不要把完整交付包作为技能安装。

## 创建仓库和 Release

1. 在选定的 GitHub 账号下创建名为 `project-relay` 的仓库，并选择可见范围。加入准备好的源码目录内容，包括隐藏文件。
2. 可选仓库简介：`用简洁的项目记录保存数据、方法、成果与下一步，在 Codex 和 Claude 之间继续工作。` 建议 topics：`agent-skills`、`codex`、`claude-code`、`project-handoff`。
3. 准备好发布后，在两份更新记录中添加或更新条目，填写实际版本和发布日期，并提交该修改。
4. 打开 **Releases → Draft a new release**，使用如 `v1.0.0` 的标签并指向预期提交，填写下方发布说明，附上前述四个附件。审核草稿后选择 **Publish release**。

许可证为 MIT，版权声明为 `Copyright (c) 2026 CJ`。

## 建议发布说明

```markdown
## Project Relay v1.0.0

一个简洁的 skill，用于在 Codex 和 Claude 之间双向继续同一个项目。

- 用一份项目记录保存关键数据和算法变化、阶段性产物、实际验证结果及下一步。
- 复用已有工作和进度文档。
- 为 Codex 或 Claude Code 进行项目级安装，或通过 Claude 自定义技能入口上传技能 ZIP。
- 提供对应中英文指南，每份包含 15 组可复制提示词。
- 技能及文档采用 MIT 许可证，可安装 ZIP 包含许可证。

安装技能请下载 project-relay.zip。Source code 压缩包包含整个仓库。SHA256SUMS.txt 提供安装 ZIP 和两份 TXT 指南的校验和。
```

对应英文说明见 [Release instructions](RELEASING.md)。

## 官方参考

- [GitHub README 说明](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes)
- [GitHub 许可证说明](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository)
- [管理 GitHub Release](https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository)
