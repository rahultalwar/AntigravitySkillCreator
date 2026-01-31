# Antigravity Skill Creator

This project is a centralized collection of specialized **Skills** designed for the Antigravity agent environment. These skills encapsulate best practices, workflows, and resource templates to help the agent perform complex development tasks efficiently and predictably.

## Available Skills

| Skill Name | Description |
| :--- | :--- |
| **[creating-resume-generators](.agent/skills/creating-resume-generators/)** | Scaffolds a web-based resume creator application with real-time preview and PDF export capabilities. |
| **[scaffolding-playwright-framework](.agent/skills/scaffolding-playwright-framework/)** | Creates a comprehensive Playwright testing framework with TypeScript, Page Object Model (POM), and custom reporting. |
| **[updating-playwright-framework](.agent/skills/updating-playwright-framework/)** | Analyzes and creates updates for an existing Playwright framework (adding tests, pages, or config). |

## How to use these skills
These skills are located in the `.agent/skills/` directory. When you initialize a task that matches a skill's description, the agent will use the logic defined in the corresponding `SKILL.md` to guide its execution.