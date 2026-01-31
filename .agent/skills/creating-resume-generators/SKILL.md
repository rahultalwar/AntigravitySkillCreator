---
name: creating-resume-generators
description: Scaffolds a web-based resume creator application with real-time preview and PDF export capabilities. Use when the user wants to build a resume builder, CV generator, or personal portfolio tool.
author: Rahul Talwar
---

# Creating Resume Generators

## When to use this skill
- When the user wants to create a tool to generate resumes.
- When the user asks for a resume builder application.
- When the user needs a web-based CV generator with live preview.

## Workflow
- [ ] Ask for preferred style (Modern, Professional, Minimalist).
- [ ] Confirm the fields required (e.g., Summary, Experience, Education, Skills, Awards).
- [ ] Initialize the project structure:
    - `index.html`: Structure and main form.
    - `style.css`: Modern styling with CSS variables.
    - `script.js`: Real-time preview logic and PDF/Print handling.
- [ ] Populate with beautiful placeholder data.
- [ ] Implement "Download PDF" using `window.print()`.

## Instructions

### 1. Requirements Gathering
Ask the user if they have any specific design preferences or if they want to stick to a default "Modern Professional" look.

### 2. Scaffold HTML (`index.html`)
Create a semantic HTML layout with:
- A `header` for the title.
- A `main` section divided into `left-panel` (Form Inputs) and `right-panel` (Live Preview).
- Use `contenteditable` or standard `input`/`textarea` fields that trigger the preview update.

### 3. Styling (`style.css`)
- Use a premium aesthetic:
    - CSS Variables for easy color adjustments.
    - Modern fonts (Inter, Roboto).
    - Subtle shadows and glassmorphism for the form.
    - **Print Media Queries**: Ensure the preview looks perfect when printed.
    ```css
    @media print {
        .no-print { display: none; }
        .resume-preview { /* specific print styles */ }
    }
    ```

### 4. Logic (`script.js`)
- Implement an Event Listener on form inputs to update the preview DOM immediately.
- Implement a `downloadResume()` function that calls `window.print()`.
- Add a "Add New Experience" button that dynamically adds input fields.

## Resources
- `resources/base-template.html`: Standard layout for the resume generator.
- `resources/modern-style.css`: Default sleek styling.
