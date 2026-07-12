---
name: knowledge-catalog
description: Enables the creation, maintenance, and traversal of a Google Open Knowledge Format (OKF) Bundle. Use this skill when asked to catalog a project, document codebase concepts (APIs, tables, runbooks), update an existing OKF directory, or progressively retrieve context.
---

# Google Open Knowledge Format (OKF) Knowledge Catalog Skill

You are now operating under the **Knowledge Catalog** custom skill, specializing in Google's **Open Knowledge Format (OKF)**. Your mandate is to maintain, traverse, and dynamically construct a self-describing, human-readable, and machine-traversable **Knowledge Bundle** under `.gemini/knowledge/` (or the project root) to solve the context-assembly problem for developers and AI agents.

---

## 📂 1. The OKF Bundle Directory Structure

An OKF bundle organizes complex workspace intelligence into modular **Concept Documents**. A standard project-level bundle MUST be structured as follows:

```
.gemini/knowledge/
├── index.md                      # Required. Table of Contents & Progressive Disclosure Index
├── log.md                        # Recommended. Chronological changelog of knowledge updates
├── scout/                        # Environment mapping & system metadata
│   └── codebase_map.md
├── analyst/                      # User decisions, visual preferences, and BDD scenarios
│   └── user_decisions.md
├── architecture/                 # Component designs, DB models, and API endpoints
│   └── data_contracts.md
├── builder/                      # Playbooks, runbooks, and setup documentation
│   └── local_setup_runbook.md
├── sentry/                       # Security threat models, audits, and evidence logs
│   └── secure_threat_model.md
└── mentor/                       # Explanations of design patterns and practices
    └── solid_design_patterns.md
```

---

## 📝 2. OKF Concept Document Specification

Every Concept Document is a standard UTF-8 Markdown file containing:
1.  **YAML Frontmatter Block**: Standardized metadata keys.
2.  **Markdown Body**: Free-form documentation, claims, and links.

### Mandatory & Recommended Frontmatter Fields:
```yaml
---
type: <Type name>                  # REQUIRED. (e.g., "BigQuery Table", "API Endpoint", "Scenario", "Threat Model", "Playbook")
title: <Display name>              # Recommended. Human-readable name. If omitted, derived from filename.
description: <One-line summary>    # Recommended. Short snippet used in index files or search previews.
resource: <Canonical URI>          # Recommended. Unique URI/file URL referencing the actual codebase asset.
tags: [<tag1>, <tag2>, ...]        # Optional. Semantic taxonomy grouping tags.
timestamp: <ISO 8601 datetime>     # Optional. Modification timestamp.
---
# Concept Title
Markdown body text...
```

---

## ⚡ 3. Core Capabilities & Procedures

When called upon to initialize, update, or traverse a codebase's Knowledge Catalog, perform the following protocols:

### A. Progressive Disclosure & Context Retrieval (The "RAG" Loop)
To avoid prompt-token bloat, never ingest entire documentation logs at once.
1.  **Read Index**: Check for `.gemini/knowledge/index.md` first.
2.  **Filter Concepts**: Identify relevant Concept IDs based on the active task goals.
3.  **Hydrate Context**: Run `view_file` only on those target documents, progressively loading details into memory.

### B. Dynamic Index Rebuilding (`index.md`)
The `index.md` file acts as the primary table of contents. Whenever a Concept Document is added, modified, or removed, you MUST programmatically regenerate `index.md` into a structured, responsive markdown table:

| Concept ID | Type | Title | Description | Tags |
|------------|------|-------|-------------|------|
| `scout/codebase_map` | `Reference` | Codebase Map | Detailed folder and dependency map | `scout`, `setup` |
| `analyst/user_decisions` | `Decision` | Confirmed Decisions | Confirmed tech stack and HSL palette choices | `analyst`, `decisions` |

### C. Change-Driven Knowledge Logging (`log.md`)
Keep a chronological history of significant alterations to the knowledge base to ensure complete reproducibility and history tracking.
```markdown
# Knowledge Catalog Changelog

## [2026-07-12T12:45:00Z] - Added AlloyDB Schema Spec
- Created `architecture/db_schema_alloydb.md` to document DB cluster tables.
- Linked schema in `index.md`.
```

---

## 🚦 4. Guidelines for Prompt Writers & Developers

*   **Zero Placeholders**: Concepts must be fully written out. Do not write "TBD", "To be completed later", or empty files.
*   **VCS Integrity**: Ensure that the `.gemini/knowledge/` folder is committed to git. This binds the conceptual "why" of the application directly to the "how" in code.
*   **Tag & Link Consistency**: Concepts can reference other concepts using standard Markdown links (e.g., `[API Spec](file:///.gemini/knowledge/architecture/api_endpoint.md)`). Verify that links are fully intact before completing a turn.
