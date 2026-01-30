---
name: scaffolding-playwright-framework
description: Creates a comprehensive Playwright testing framework with TypeScript, Page Object Model (POM), and custom reporting. Use when the user requests to set up a new Playwright project or automated testing framework.
author: Rahul Talwar
---

# Scaffolding Playwright Framework
# Author: Rahul Talwar

## When to use this skill
- When the user asks to create a Playwright framework.
- When the user wants to set up automated testing with proper structure (POM).
- When the user asks for a Playwright setup with custom reporters and TypeScript.

## Workflow
- [ ] Ask for or confirm the Domain/URL to automate and specific test instructions.
- [ ] Initialize Playwright project (`npm init playwright@latest`).
- [ ] Create POM directory structure (`pages`, `tests`, `utils`, `fixtures`).
- [ ] Copy `CustomReporter.ts` from resources.
- [ ] Configure `playwright.config.ts`.
- [ ] Create `BasePage.ts` and domain-specific Page Objects.
- [ ] Create example spec file using the Page Objects.
- [ ] Run a test to verify setup.

## Instructions
<!-- Follow these steps to scaffold the framework -->

### 1. Initialization
1.  **Ask for Domain**: If not provided, ask the user for the target domain and specific flows to test.
2.  **Scaffold Project**:
    Run the following command to initialize Playwright (use default options or `yes` to all to ensure non-interactive where possible, or guide user):
    ```bash
    # Initialize Playwright with TypeScript and no browsers (install them later for speed if needed)
    npm init playwright@latest --yes -- --quiet --lang=TypeScript --no-browsers --gha
    ```
    *Note: Adjust arguments if user specifies otherwise.*

### 2. Structure Setup
<!-- Create the Page Object Model directories -->
Create the following folders:
```bash
mkdir -p pages utils fixtures
```

### 3. Implement Custom Reporter
<!-- Copy the custom reporter template -->
Read the resource `resources/CustomReporter.ts` and write it to `utils/CustomReporter.ts` in the user's project.
*Use `cp` if possible or read-and-write.*

### 4. Implement Page Object Model
<!-- Setup the base page and domain pages -->
1.  **Base Page**: Read `resources/BasePage.ts` and write it to `pages/BasePage.ts`.
2.  **Domain Pages**: Create a class in `pages/[PageName].ts` extending `BasePage`.
    -   Include selectors and methods for the user's requested flow.
    -   Example:
        ```typescript
        import { BasePage } from './BasePage';
        export class LoginPage extends BasePage {
            // Selectors and actions
        }
        ```

### 5. Configure Playwright
<!-- Register the custom reporter in the config -->
Update `playwright.config.ts` to use the custom reporter.
-   Import the reporter or reference it by path.
-   Set `reporter: [['./utils/CustomReporter.ts'], ['list']]`.

### 6. Create Tests
<!-- Create the implementation test spec -->
Create a test file in `tests/` (e.g., `tests/example.spec.ts`).
-   Import Page Objects.
-   Write a test case following the user's instructions.
-   Use `test.beforeEach` to navigate to the domain.

## Resources
-   `resources/CustomReporter.ts`: Template for the custom reporter.
-   `resources/BasePage.ts`: Template for the base page class.
