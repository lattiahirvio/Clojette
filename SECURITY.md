# Security Policy

## Supported versions

Security fixes, when available, are applied to the latest code on the `main` branch, including the `all.gs` bundle currently committed there. Clojette does not maintain separate security-support branches or backport fixes to older snapshots.

| Version | Supported |
| --- | --- |
| Latest `main` | Yes |
| Older commits or previous bundled releases | No |
| Forks or modified copies | No |

Users should reproduce a suspected issue against the latest `main` branch before reporting it.

## What counts as a security issue

Clojette is an interpreter. Code passed intentionally to the REPL or evaluation APIs is expected to run, so that behavior alone is not a vulnerability. Security reports should describe unintended behavior, such as execution without an explicit evaluation request, a bypass of a documented boundary, or an issue that exposes or modifies data outside the caller's intended scope.

Issues in GreyHack, GreyScript, MiniScript, or other third-party tools should be reported to their respective maintainers unless the issue is caused by Clojette.

## Reporting a vulnerability

Do not disclose vulnerability details in a public GitHub issue, pull request, discussion, or Discord channel.

1. Check the repository's **Security** tab for a **Report a vulnerability** option. If GitHub offers that option, use it to submit the report privately.
2. If private reporting is not available, open a GitHub issue containing only the title `Private security contact requested`, or use the project Discord linked from the README to ask a maintainer for a private reporting channel. Do not include affected files, impact, reproduction steps, logs, or proof-of-concept details in that public request.
3. Share the technical report only after a private channel has been established.

Include, when possible:

- a description of the issue and its security impact;
- the affected commit, file, or Clojette version;
- the GreyHack/GreyScript environment used;
- minimal reproduction steps or a proof of concept;
- any known mitigations or suggested fix; and
- your preferred credit and any intended disclosure timeline.

This is a volunteer-maintained project, so no fixed response time is guaranteed. Maintainers will review reports as availability permits, may request additional information, and will coordinate remediation and disclosure for confirmed issues. Please keep report details private until a fix or mutually agreed disclosure date is available.

## Research guidelines

Please test only on systems and accounts you own or are explicitly authorized to use. Avoid accessing other users' data, disrupting services, degrading the game experience, or using social engineering. Stop testing and report the issue if you encounter sensitive data or affect another user.
