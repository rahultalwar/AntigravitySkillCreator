---
name: creating-linkedin-post-generators
description: Scaffolds a web-based LinkedIn post generator application. Use when the user wants to create a tool for drafting and previewing LinkedIn content.
author: Rahul Talwar
---

# Creating LinkedIn Post Generators

## When to use this skill
- When the user wants to build an application for LinkedIn content creation.
- When the user asks for a LinkedIn post previewer or drafting tool.
- When the user needs a tool that structures posts (Topic, Hook, Body, CTA) for LinkedIn.

## Workflow
- [ ] Ask for the primary goal (e.g., thought leadership, product launch, networking).
- [ ] Initialize the project structure:
    - `index.html`: Main interface with input fields for Topic, Tone, and Core Message.
    - `style.css`: Clean UI with a high-fidelity LinkedIn post preview area.
    - `script.js`: Logic to generate post structure and update the preview.
- [ ] Implement a "Post Preview" that mimics the LinkedIn desktop feed look.
- [ ] Add a "Copy to Clipboard" feature for the generated text.

## Instructions

### 1. Requirements Gathering
Determine the "Ingredients" for the post:
- **Topic**: What is the post about?
- **Tone**: Professional, Casual, Controversial, or Instructional?
- **Call to Action (CTA)**: What should the reader do next?

### 2. Scaffold HTML (`index.html`)
- **Input Panel**: Fields for Topic, Keywords, Tone dropdown, and a "Generate" button.
- **Preview Panel**: A div container styled to look EXACTLY like a LinkedIn post (profile picture placeholder, name, timestamp, "Follow" button, etc.).

### 3. Styling (`style.css`)
- Use LinkedIn's signature colors (Blue: #0a66c2, Text: #000000e6, Background: #f3f2ef).
- Implement the "Post Card" with:
    - Rounded corners (8px).
    - Subtle borders.
    - Standard LinkedIn typography.
- **Glassmorphism**: Apply subtle glass effects to the input panel for a premium feel.

### 4. Logic (`script.js`)
- **Template Logic**: Use pre-defined post structures based on tone.
    - *Expert Tip*: Start with a "Hook" (first 2 lines), then "Value", then "CTA".
- **Live Preview**: Sync the generated content with the preview card elements.
- **Copy Logic**: 
    ```javascript
    function copyText() {
        const text = document.getElementById('final-post').innerText;
        navigator.clipboard.writeText(text);
    }
    ```

## Resources
- `resources/post-generator.html`: Base layout for the LinkedIn tool.
- `resources/linkedin-theme.css`: Precise styles for the LinkedIn feed preview.
