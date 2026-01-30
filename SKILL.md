---
name: updating-playwright-framework
description: Analyzes and creates updates for an existing Playwright framework. Use when the user requests to add tests, pages, or change configuration in an existing Playwright project.
author: Rahul Talwar
---

# Updating Playwright Framework
# Author: Rahul Talwar

## When to use this skill
- When the user asks to add a new test case to an existing Playwright project.
- When the user wants to add a new Page Object to an existing POM structure.
- When the user requests to update the reporting configuration of an existing framework.
- When the user mentions "update", "add to", or "modify" in the context of a Playwright framework.

## Workflow
- [ ] **Analyze Configuration**: Read `playwright.config.ts` to understand environments, base URLs, and reporters.
- [ ] **Analyze Structure**: Locate the POM directory (e.g., `pages/`, `src/pages/`, `lib/`) and test directory.
- [ ] **Analyze Style**: Read a sample Page Object and Test file to understand naming conventions and coding style.
- [ ] **Confirm Requirements**: If ambiguous, ask user for target environment or specific reporting needs.
- [ ] **Implement Updates**:
    - [ ] Create/Update Page Objects matching existing style.
    - [ ] Create/Update Tests importing correct pages and using config-defined Base URLs.
    - [ ] Modify `playwright.config.ts` if reporting changes are requested.
- [ ] **Verify**: Run the new test or build to ensure no breaking changes.

## Instructions

### 1. Analysis Phase
<!-- Identify the project structure and configuration -->
1.  **Find Config**: Look for `playwright.config.ts` or `playwright.config.js` in the root.
    ```bash
    find . -maxdepth 2 -name "playwright.config.*"
    ```
    *Read this file to identify `projects` (environments), `reporter` settings, and `use: { baseURL }`.*

2.  **Find Page Objects**: Identify where Page Objects are stored. Common patterns: `pages/`, `src/pages/`, `lib/pages/`.
    ```bash
    find . -type d -name "pages" -o -name "lib"
    ```
    *If found, list a few files to understand the naming convention (e.g., `LoginPage.ts` vs `login.page.ts`).*

3.  **Read Sample**:
    Read the content of one Page Object and one Spec file to understand:
    -   Are they using classes or functions?
    -   Are they using a custom `test` fixture or standard `@playwright/test`?
    -   How are selectors defined (getters, properties, or strings)?

### 2. Implementation Phase - Adding Pages
**Goal**: Create a new page object that looks like it belongs in the existing project.

1.  **Create File**: Create the file in the identified POM directory using the established naming convention.
2.  **Scaffold Class**:
    -   Copy the structure of the "Sample" page object.
    -   Extend a BasePage or use the same constructor pattern found in the analysis.
    -   Add methods and selectors for the User's requested feature.

### 3. Implementation Phase - Adding Tests
**Goal**: Add a test that utilizes the framework's features (environments, fixtures).

1.  **Create/Edit Spec**: Create a new file in the tests directory or append to an existing one.
2.  **Write Test**:
    -   Import the new Page Object.
    -   Use `test.beforeEach` to navigate (using `baseURL` from config if applicable).
    -   **Important**: If the config has multiple projects (e.g., 'staging', 'prod'), ensure the test uses the correct one or is compatible with the default.
    -   If the user requested a specific URL and it differs from `baseURL`, override it in the `test.use()`.

### 4. Implementation Phase - Custom Reporting
**Goal**: Update reporting without breaking existing config.

1.  **Check Existing**: Check `reporter` field in `playwright.config.ts`.
2.  **Modify**:
    -   If the user wants a **new** reporter, create the reporter file (e.g., `utils/MyCustomReporter.ts`) *first*.
    -   Then, edit `playwright.config.ts`.
    -   **Crucial**: Do not overwrite existing reporters unless asked. Use an array to add multiple:
        ```typescript
        // Change reporter: 'html' to:
        reporter: [['html'], ['./utils/MyCustomReporter.ts']]
        ```

### 5. Verification
<!-- Verify the update -->
Run the newly created test to confirm it works and fits into the framework.
```bash
npx playwright test tests/my-new-test.spec.ts
```
