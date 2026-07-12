# Google Open Knowledge Format (OKF) - Knowledge Catalog Skill

This standalone repository contains the authoritative custom skill definitions, schemas, and progressive disclosure standards for managing a **Google Open Knowledge Format (OKF)** Knowledge Bundle in any software project workspace.

---

## 📂 Repository Structure

*   `SKILL.md`: The complete custom skill instructions defining the OKF directory trees, YAML frontmatter schemas, index-rebuilding schemas, and active traversal rules.
*   `.gitignore`: Repository ignore-lists.
*   `LICENSE`: MIT open source license.

---

## 🚦 System Integration

This skill is designed to be globally symlinked into Google Antigravity's active skills directories:
```bash
~/.gemini/skills/knowledge-catalog -> ~/code/github/skills-knowledge-catalog
```

Once symlinked, the catalog capabilities are natively and dynamically integrated across core execution harnesses, including the **6 AI Personas Framework (`6-personas`)** and the **Prompt-Writer (`prompt-writer`)** pipelines.

---

## 🚀 Usage inside Antigravity (AGY)

When initialized in a project directory, AGY will automatically maintain a version-controlled, human-readable cognitive index under `.gemini/knowledge/`. 

To manually invoke this skill on an existing project, simply trigger the agent inside AGY:
> *"Please catalog this project using our knowledge-catalog skill."*
