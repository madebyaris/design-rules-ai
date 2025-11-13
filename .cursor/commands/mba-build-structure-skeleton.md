---
name: mba-build-structure-skeleton
description: Generate project structure skeleton with proper setup
---

# MBA Build Structure Skeleton

Generate a complete project structure with proper setup for professional UI/UX development.

## Arguments

- `project_name` (required): Name of the project
- `platform` (optional): web|desktop|ios|android - default: web
- `framework` (optional): html|react|vue|svelte|react-native|swift|kotlin - default: html
- `css_approach` (optional): vanilla-css|tailwind|css-modules|styled-components - default: vanilla-css

## Instructions

1. **Review Rules**: Read `.cursor/rules/00-core-principles.mdc` for foundational guidance

2. **Create Directory Structure**:
   ```
   project-name/
   ├── src/
   │   ├── components/
   │   ├── pages/
   │   ├── styles/
   │   │   ├── reset.css
   │   │   ├── tokens.css
   │   │   ├── typography.css
   │   │   └── utilities.css
   │   ├── assets/
   │   └── index.html (or main entry)
   ├── public/
   ├── docs/
   ├── .gitignore
   ├── README.md
   └── package.json (if applicable)
   ```

3. **Generate Base Files**:
   - **reset.css**: Modern CSS reset
   - **tokens.css**: Design tokens (colors, spacing, typography)
   - **typography.css**: Type system
   - **utilities.css**: Utility classes
   - **index.html**: Semantic HTML structure

4. **Platform-Specific Setup**:
   - **Web**: HTML + CSS setup
   - **Desktop**: Electron/Tauri config
   - **iOS**: Xcode project structure
   - **Android**: Android Studio structure

5. **Configuration Files**:
   - Package manager config (package.json, etc.)
   - Build tool config (if needed)
   - Linter/formatter config
   - Git ignore file

6. **Documentation**:
   - README with setup instructions
   - Design system documentation stub
   - Component documentation template

## Output Files

Generate the following files with proper content:

1. `src/styles/reset.css` - Modern CSS reset
2. `src/styles/tokens.css` - Design tokens
3. `src/styles/typography.css` - Typography system
4. `src/index.html` - Semantic HTML structure
5. `README.md` - Project documentation
6. `.gitignore` - Appropriate ignores
7. `package.json` - If using npm/yarn

## Quality Checks

- [ ] Proper directory structure
- [ ] All base files created
- [ ] Semantic HTML structure
- [ ] Design tokens defined
- [ ] Documentation included
- [ ] Git setup complete

## Example Usage

```
/mba-build-structure-skeleton project_name="Acme Dashboard" platform="web" framework="react" css_approach="vanilla-css"
```

This will generate a React web project with vanilla CSS and proper MBA design system structure.

