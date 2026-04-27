<div align="center">

# ⚡ MuleSoft Skills for AI Agents

### Supercharge your MuleSoft development with AI-powered automation

[![GitHub Stars](https://img.shields.io/github/stars/Naoufal-Charafat/muleSoft-skills?style=for-the-badge&color=FFD700&labelColor=1a1a2e)](https://github.com/Naoufal-Charafat/muleSoft-skills/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/Naoufal-Charafat/muleSoft-skills?style=for-the-badge&color=00D4FF&labelColor=1a1a2e)](https://github.com/Naoufal-Charafat/muleSoft-skills/network)
[![License](https://img.shields.io/badge/License-MIT-7B2FBE?style=for-the-badge&labelColor=1a1a2e)](LICENSE)
[![MuleSoft](https://img.shields.io/badge/MuleSoft-4.x-00A1E0?style=for-the-badge&labelColor=1a1a2e)](https://www.mulesoft.com/)

---

> **Stop writing boilerplate. Stop hunting through docs.**
> Let your AI agent handle the heavy lifting while you focus on what matters.

</div>

---

## What is this?

This repository contains custom **skills for AI coding agents** (Claude, GitHub Copilot, and others) that dramatically accelerate MuleSoft development workflows. Instead of manually writing repetitive integration code or documentation, you describe what you need — and your AI agent does the rest.

These skills act as expert-level domain knowledge injected directly into your AI agent, transforming it from a general-purpose assistant into a **MuleSoft specialist**.

---

## 🚀 Available Skills

### `mulesoft-api-patterns` — API Pattern Generator

Generate complete, production-ready MuleSoft 4.x projects implementing proven API design patterns from **JJ Geewax's *"API Design Patterns"*** book.

**What it does:**

- Scaffolds full MuleSoft projects from scratch based on a named pattern
- Covers **15+ industry-standard patterns** across resource lifecycle, data retrieval, API evolution, and data consistency
- Enforces correct Maven plugin versions, Java 17 config, and namespace declarations — no more mysterious build failures
- Includes proper `pom.xml`, `mule-artifact.json` (in both required locations), global configs, and flow XMLs
- Embeds pattern-specific troubleshooting knowledge to avoid known pitfalls

**Supported patterns:**

| Category | Patterns |
|---|---|
| Resource Lifecycle | Long Running Operations, Batch Operations, Partial Updates (PATCH) |
| Data Retrieval | Pagination, List Filtering & Sorting, Resource Expansion, Field Selection |
| API Evolution | Versioning, Deprecation, Backward Compatibility |
| Data Consistency | Conditional Requests, Idempotency, Optimistic Locking |

---

### `mulesoft-documentor` — Documentation Generator

Analyze any existing MuleSoft project and generate **comprehensive, professional technical documentation** in Markdown — automatically.

**What it does:**

- Parses Mule XML flows, sub-flows, connectors, and global configs
- Extracts metadata from `pom.xml` and `mule-artifact.json`
- Documents every flow with its trigger type, processing steps, error handling, and DataWeave transformations
- Generates API endpoint docs (paths, methods, request/response formats, auth schemes)
- Produces deployment guides, configuration tables, and error strategy documentation
- Handles any connector type: Salesforce, Database, HTTP, MQ, and more

---

## 💡 Why This Matters

MuleSoft development involves significant amounts of repetitive, error-prone work: configuring XML namespaces, remembering Maven plugin quirks, structuring flows correctly, and writing documentation that nobody has time to write. This repository eliminates those friction points.

| Without these skills | With these skills |
|---|---|
| Hours spent scaffolding new projects | Full project generated in seconds |
| Debugging cryptic Maven build errors | Correct configuration from the start |
| Documentation written manually (or never) | Auto-generated from your existing project |
| Pattern implementations from memory | Best-practice implementations on demand |
| Context-switching between Anypoint Studio and docs | Everything stays in your editor |

The result: **less context-switching, fewer bugs, faster delivery.**

---

## 📦 Installation

Skills live in your AI agent's skills directory. Once installed, they activate automatically when relevant — no extra commands needed.

### Claude (Claude Code / Claude Desktop)

```bash
# macOS / Linux
cd ~/.claude/skills/
git clone https://github.com/Naoufal-Charafat/muleSoft-skills.git

# Windows
cd %USERPROFILE%\.claude\skills\
git clone https://github.com/Naoufal-Charafat/muleSoft-skills.git
```

### GitHub Copilot (VS Code)

Place the skill folders inside your workspace's `.copilot/skills/` directory, or in the global skills path configured in your Copilot settings.

### Verify Installation

After installing, restart your AI agent session and ask:

```
What MuleSoft skills do you have available?
```

Your agent should describe both `mulesoft-api-patterns` and `mulesoft-documentor`.

---

## 🛠️ How to Use

Skills are triggered automatically when your request matches their domain. You can also invoke them explicitly:

**Generate a MuleSoft project with a pattern:**
```
Create a MuleSoft project implementing the Pagination pattern for a products API
```

```
Using the mulesoft-api-patterns skill, scaffold a Long Running Operations 
project for an async report generation endpoint
```

**Generate documentation for an existing project:**
```
Document my MuleSoft project located at ./my-integration-project
```

```
Using the mulesoft-documentor skill, generate full technical documentation 
for this project including all flows, connectors, and deployment info
```

---

## 🗂️ Repository Structure

```
muleSoft-skills/
├── README.md
└── skills/
    ├── mulesoft-api-patterns/
    │   ├── SKILL.md                        # Skill definition & instructions
    │   ├── assets/
    │   │   └── mule-base-template/         # Base project template
    │   └── references/
    │       ├── patterns/                   # Per-pattern implementation guides
    │       │   ├── pagination.md
    │       │   ├── batch-operations.md
    │       │   ├── long-running-operations.md
    │       │   └── ...
    │       ├── advanced/
    │       │   └── field-masks.md
    │       └── troubleshooting/            # Known issues & fixes
    │           ├── maven-build-errors.md
    │           ├── validation-module.md
    │           └── bulk-operations.md
    └── mulesoft-documentor/
        └── SKILL.md                        # Skill definition & instructions
```

---

## ✏️ Creating Your Own Skills

Want to contribute a new skill or build one for your team? Each skill is a folder with a `SKILL.md` file at its root.

### Skill Structure

```
your-skill-name/
├── SKILL.md          # Main skill file (required)
├── templates/        # Reusable templates (optional)
├── examples/         # Usage examples (optional)
└── references/       # Supporting reference docs (optional)
```

### SKILL.md Frontmatter

```markdown
---
name: your-skill-name
description: One sentence used by the AI to decide when to activate this skill.
---

# Skill Title

## When to Use This Skill
- Scenario A
- Scenario B

## Capabilities
- What it can generate or do

## Instructions for the Agent
[Step-by-step instructions the AI will follow]
```

**Best practices:**
- Keep the `description` frontmatter field precise — it determines when the skill auto-activates
- Include concrete examples with expected inputs and outputs
- Reference external files for complex patterns rather than embedding everything in `SKILL.md`
- Document known pitfalls so the agent avoids them proactively

---

## 🤝 Contributing

All contributions are welcome — new skills, improved patterns, bug fixes, or better examples.

1. **Fork** this repository
2. **Create** a feature branch: `git checkout -b feature/your-skill-name`
3. **Add** your skill following the structure above
4. **Update** the Available Skills table in this README
5. **Commit**: `git commit -m "Add: skill for [functionality]"`
6. **Push**: `git push origin feature/your-skill-name`
7. **Open** a Pull Request

### Contribution checklist

- [ ] Skill has a clear, descriptive `SKILL.md` frontmatter
- [ ] Includes at least two usage examples
- [ ] Doesn't duplicate existing functionality
- [ ] Folder name uses kebab-case
- [ ] README Available Skills table updated

---

## 🌍 Spread the Word

If these skills save you time, consider:

- ⭐ **Starring** this repo so others can find it
- 🔁 **Sharing** it with your MuleSoft or integration community
- 💬 **Opening a discussion** to suggest new skills or patterns

The goal is simple: make MuleSoft development faster and more accessible for everyone — whether you're a seasoned integration architect or just getting started.

---

<div align="center">

Built for the MuleSoft community · Powered by AI · Made to be shared

</div>
