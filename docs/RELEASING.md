# Publishing Project Relay on GitHub

English | [简体中文](RELEASING.zh-CN.md)

These instructions describe how to maintain and publish Project Relay releases. Preparing local files does not itself publish a repository, install a skill, or create a GitHub release.

## What to publish

Use the contents of the prepared `project-relay/` source directory as the repository root. Keep `README.md`, `README.zh-CN.md`, `skills/`, `docs/`, the changelogs, and the dotfiles in their existing relative locations. Include the root `LICENSE`. Do not upload the parent working directory or private project records.

The English installable skill is `skills/project-relay/SKILL.md`. Its corresponding Chinese source is `docs/SKILL.zh-CN.md`. The English and Chinese TXT guides each contain 15 prompts in the same order. Keep these pairs in sync when editing.

## Before publishing

1. Review the English and Chinese content. This release uses the MIT License, selected by the owner. Keep identical license copies in the repository root and the distributed skill folder, and retain the copyright and permission notices.
2. Check that `name: project-relay` matches the skill folder, that the description is present, and that the template and instructions are complete.
3. Check local documentation links, UTF-8 text, both installation paths, and the archive layout. Test a local installation in a disposable project if application-level verification is needed.
4. Rebuild archives and checksums after any edit. Do not claim that static package checks prove behavior in Codex or Claude.

## Release assets

The prepared delivery includes these separate files for release attachments:

- `project-relay.zip`: the English installable skill folder and MIT License. Its internal paths must be `project-relay/SKILL.md` and `project-relay/LICENSE`, not `skills/project-relay/SKILL.md` or an extra nested folder.
- `project-relay-user-guide.en.txt`: an exact copy of `docs/USER_GUIDE.en.txt` for direct download.
- `project-relay-user-guide.zh-CN.txt`: an exact copy of `docs/USER_GUIDE.zh-CN.txt` for direct download.
- `SHA256SUMS.txt`: SHA-256 checksums for those three files.

To rebuild manually, ZIP the `project-relay` folder inside `skills/`, retaining that folder as the archive's top level. Copy the two guides to the names above and regenerate the checksums with your platform's SHA-256 tool. GitHub's automatic source archives are repository snapshots, not replacements for this installable ZIP.

The separate `project-relay-github.zip` is the complete delivery for the owner, containing the `project-relay/` source directory and `release-assets/`. Extract it and publish the contents of `project-relay/` as the repository; upload the files in `release-assets/` as release attachments. Do not install the complete delivery archive as a skill.

## Create the repository and release

1. Create a repository named `project-relay` under your chosen GitHub account and choose its visibility. Add the prepared source directory's contents, including dotfiles.
2. Set an optional repository description: `Continue projects across Codex and Claude with a concise record of data, methods, results, and next steps.` Suggested topics: `agent-skills`, `codex`, `claude-code`, `project-handoff`.
3. When ready, add or update the entry in both changelogs with the actual version and publication date, then commit that change.
4. Open **Releases → Draft a new release**. Use a tag such as `v1.0.0`, point it at the intended commit, add the release notes below, and attach the four assets above. Review the draft before selecting **Publish release**.

The license is MIT, with the copyright notice `Copyright (c) 2026 CJ`.

## Suggested release notes

```markdown
## Project Relay v1.0.0

A small skill for continuing the same project across Codex and Claude in either direction.

- Maintain one project record for key data and algorithm changes, milestone outputs, actual validation results, and the next step.
- Reuse existing work and progress documents.
- Install locally for Codex or Claude Code, or upload the skill ZIP through Claude's custom-skill interface.
- Read the corresponding English and Chinese guides, each with 15 copyable prompts.
- The skill and documentation are licensed under MIT; the installable ZIP includes the license.

Download project-relay.zip to install the skill. Source code archives contain the full repository. SHA256SUMS.txt provides checksums for the installable ZIP and the two TXT guides.
```

For the corresponding Chinese notes, see [中文发布说明](RELEASING.zh-CN.md).

## Official references

- [GitHub README guidance](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes)
- [GitHub licensing guidance](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository)
- [Managing GitHub releases](https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository)
