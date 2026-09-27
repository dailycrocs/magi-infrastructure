# Instructions for Coding Agents

These instructions apply to AI and coding agents working on the
MAGI Infrastructure project.

- Work only on the current branch.
- Never commit directly to `main`.
- One GitHub issue should correspond to one branch.
- Make one commit per meaningful change.
- Do not batch unrelated changes into one commit.
- Do not merge until the user confirms the work has been reviewed.
- Ask the user what was personally verified before adding `Checked:` statements.
- Never invent verification results.
- Experimental scripts belong in `sandbox/`.
- Reusable MAGI scripts belong in `scripts/`.
- Do not commit credentials, tokens, passwords, private keys, or other secrets.
- Keep documentation updated when a change affects project behavior or design.
- Before making substantial changes, inspect the relevant existing files and
  explain the proposed changes to the user.

## Agent Logging

`AGENT-LOG.md` records substantial work performed with the assistance of an
AI or coding agent.

Agents should update `AGENT-LOG.md` when they make a substantial contribution
to the MAGI project, such as:

- Creating or significantly modifying scripts or code.
- Implementing a project feature or service.
- Performing substantial configuration or automation work.
- Creating or significantly changing technical project artifacts.
- Assisting with testing, troubleshooting, or validation that materially
  affects the project.

Do not add an `AGENT-LOG.md` entry for routine tasks such as:

- Git commands or branch management.
- Navigating the repository.
- Minor wording or formatting changes.
- Small documentation corrections.
- Read-only research or repository inspection.

Each substantial entry should describe:

- The GitHub issue or task being worked on.
- What the agent contributed.
- Which files or components were changed.
- What the user personally reviewed, tested, or verified.

Never claim that the user tested or verified something unless the user
explicitly confirms that verification.
