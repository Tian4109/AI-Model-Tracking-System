# AI Model Tracking Documentation System

## What This Project Does

This project uses Claude Code to:

1. collect AI model information from official vendor sources
2. generate structured vendor draft files
3. produce a final comparison report

Final output:

```text
models.md
```

The report helps users compare:

- pricing
- context windows
- multimodal support
- deployment options
- recommended use cases

---

# Core Vendors

Supported core vendors:

- OpenAI
- Anthropic
- Google
- Meta
- Microsoft

Additional vendors can also be added dynamically through `links.md`.

---

# Project Structure

```text
.
├── README.md
├── WORKFLOW.md
├── links.md
├── models.md
├── drafts/
└── .claude/
```

Important folders:

| Folder/File | Purpose |
|---|---|
| `links.md` | Official source list |
| `drafts/` | Intermediate vendor outputs |
| `models.md` | Final generated report |
| `.claude/commands/` | Claude Code commands |
| `.claude/subagents/` | Researcher and Reporter agents |

---

# Quick Start

## 1. Install Claude Code

Install Claude Code from the official instructions:

Windows PowerShell:

```powershell
irm https://claude.ai/install.ps1 | iex
```

Windows CMD:

```cmd
curl -fsSL https://claude.ai/install.cmd -o install.cmd && install.cmd && del install.cmd
```

macOS / Linux / WSL:

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

Check installation:

```bash
claude --version
```

---

## 2. Sign In

Open a terminal and run:

```bash
claude
```

Complete the login process.

---

## 3. Open the Project

Recommended:

```text
VS Code
→ Open Folder
→ Select this project
```

Then open:

```text
Terminal
→ New Terminal
```

Make sure the terminal is inside the project root folder.

---

## 4. Start Claude Code

Run:

```bash
claude
```

Claude Code must be started from the project root so it can detect:

```text
.claude/
links.md
drafts/
```

---

# First Test

Run:

```text
/track-openai
```

Expected result:

```text
drafts/openai.md
```

Then run:

```text
/generate-report
```

Expected result:

```text
models.md
```

Open `models.md` to view the final report.

---

# Common Commands

## Update One Core Vendor

```text
/track-openai
/track-google
/track-meta
```

Then:

```text
/generate-report
```

---

## Add and Update a New Vendor

1. Add a new vendor section to `links.md`

Example:

```text
# Mistral
```

2. Run:

```text
/track-vendor Mistral
```

3. Generate the report:

```text
/generate-report
```

This automatically creates:

```text
drafts/mistral.md
```

and includes it in:

```text
models.md
```

---

## Refresh All Vendors

```text
/track-all
```

Then:

```text
/generate-report
```

---

## Full End-to-End Refresh

```text
/update-report
```

This refreshes all drafts and rebuilds `models.md`.

---

# How the System Works

```text
links.md
        ↓
Claude Code command
        ↓
Researcher agent
        ↓
drafts/*.md
        ↓
Reporter
        ↓
models.md
```

---

# Source Policy

The project follows an official-source-first policy.

Preferred sources:

- official documentation
- official pricing pages
- official GitHub repositories
- official Hugging Face organisation pages
- official model cards

Avoid unofficial blogs and random comparison websites.

---

# Troubleshooting

## Slash commands do not appear

Make sure:

```text
claude
```

was started from the project root folder.

---

## Draft file was not generated

Check:

- the `drafts/` folder exists
- the vendor exists in `links.md`
- Claude Code has file write permission

---

## models.md was not generated

Run:

```text
/generate-report
```

after at least one draft file exists.

---

# Notes

- This is a documentation-focused project, not a web app.
- Claude Code commands are the main interface.
- `drafts/` are intermediate files.
- `models.md` is the final client-facing output.
