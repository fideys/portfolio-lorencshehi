# Copilot Instructions for Portfolio Project

## Project Overview
This is a personal developer portfolio website for Lorenc Shehi, built as a single-page application (SPA) using vanilla HTML, CSS, and JavaScript. It's a **work in progress** with some sections being refactored from "vibecoded" placeholder content. No backend, build tools, or frameworks are used—the site is designed to be directly servable as static HTML.

## Architecture & Structure

### Core Stack
- **HTML**: Single semantic document (`index.html`, 178 lines) with no build process or templating
- **CSS**: Unified style sheet (`styles.css`, 313 lines) with dark theme and modern design patterns
- **JavaScript**: Minimal vanilla JS for smooth scrolling and form demo (no external libraries)

### Page Sections (Anchor-based Navigation)
The site is organized into horizontal sections, each identified by an ID used for smooth scroll navigation:
1. `#home` (.hero) - Hero section with name, tagline, CTA
2. `#skills` - Grid of current skills (React, Node.js, Python, SQL, AI/ML, AWS)
3. `#learning` - Grid of currently learning topics
4. `#projects` - Project cards with GitHub links (2 projects shown: Lorentz's Theory game, PyTorch Number Classifier)
5. `#videos` - Video content grid linking to YouTube
6. `#contact` - Demo contact form with validation

### Design Patterns
- **Dark theme**: Background `#09090b`, card backgrounds `#18181b`, accent colors red/orange (#ff3636) and blue (#3b82f6)
- **Gradient accents**: Primary gradient on h1 (red to pink), project card shadows use red, video thumbnails use purple
- **Responsive grids**: CSS Grid with `repeat(auto-fit, minmax(...))` for fluid layouts on all screen sizes
- **Smooth interactions**: All hover states include transitions (0.2-0.3s), button scaling, and subtle shadows

## Key Development Conventions

### Content Management
- **No CMS or database**: All content is hardcoded in HTML
- **External links**: GitHub repos and YouTube videos are linked directly; images load from external CDNs or relative paths
- **To update content**: Edit HTML directly; changes are immediately visible when served
- **Incomplete sections**: Video cards 2-3 use placeholder YouTube URLs ("example2", "example3"); replace with real URLs when content is ready

### Style Consistency
- **CSS organization**: Global reset at top, navigation, hero, sections, components, form elements, footer, then media queries
- **Hover states**: Cards use `transform: translateY(-2px)` or `scale()`, buttons use `background` shifts, links use `color` transitions
- **Colors**: Use CSS variables aren't implemented yet; all colors are hardcoded hex values for simplicity (refactor opportunity)
- **Responsive breakpoint**: Single media query at 768px for mobile; heading sizes and grid layouts adjust

### Form Behavior
- **Contact form is non-functional demo**: Form submission shows alert and resets (see inline script). No backend integration yet.
- **Accessibility gap**: Form has labels and required attributes but no ARIA or error handling

## Common Editing Tasks

### Adding/Updating Project Cards
Project cards are in the `.projects-grid` div. Each card has two variants:
- `.project-image1` with red gradient background (for project images)
- `.project-image2` with white background (for logos/icons)

Example structure:
```html
<a href="https://github.com/..." class="project-card">
    <div class="project-image1">
        <img src="https://...">
    </div>
    <div class="project-content">
        <h3>Project Name</h3>
        <p>Description</p>
        <div class="project-tags">
            <div class="tag">Status</div>
        </div>
    </div>
</a>
```

### Adding Skills or Learning Topics
Skills are simple cards in `.skills-grid` divs. Update either section by adding:
```html
<div class="skill-card">
    <div style="font-size: 2rem; margin-bottom: 0.5rem;">🔧</div>
    <h3>Skill Name</h3>
</div>
```

### Updating Navigation Links
Navigation links in `<nav>` use anchor href targeting section IDs. Add new sections by creating a `<section id="...">` and adding corresponding `<li><a href="#...">Name</a></li>` in nav.

## Known Limitations & TODOs
- Form submission is a demo—no backend email functionality exists
- Some video card thumbnails are placeholder play button emojis (▶️)
- No CSS variables for DRY color management (all colors hardcoded)
- No build process—serve HTML directly
- No testing framework or CI/CD configured
- Accessibility: Missing ARIA labels, heading hierarchy could be improved
- Replace placeholder emojis with images/URLs

## Development Workflow
1. **Edit HTML/CSS directly** in editor
2. **Serve with Five Server** (built-in VS Code extension) or any static server
3. **Test in browser**: Smooth scroll, hover effects, form reset should work
4. **Deploy**: Copy files to hosting (GitHub Pages, Netlify, etc.)—no build step required

## When Enhancing This Codebase
- Prioritize preserving the vanilla JS approach unless a framework is explicitly needed
- Maintain the dark theme and red/blue accent color scheme for visual consistency
- Keep CSS organized in the current order (globals → nav → sections → components → responsive)
- Use CSS Grid/Flexbox; avoid frameworks like Bootstrap to keep dependencies minimal
- Test responsive behavior at 768px breakpoint and below
