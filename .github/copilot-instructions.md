# Copilot Instructions for V-Ray & Cau Chocolates Diagnostic Presentation

## Project Overview
This is a standalone, static HTML presentation for a strategic AI diagnosis proposal. It is designed as a single-page scrolling website where each section represents a presentation slide.

## Tech Stack
- **Core**: HTML5, CSS3, Vanilla JavaScript.
- **External Libraries**: Font Awesome 6.5.1 (CDN), Google Fonts (Playfair Display, Montserrat).
- **Build System**: None. Pure static files.

## Architecture & File Structure
- `index.html`: Contains all markup, styles (in `<style>`), and logic (in `<script>`).
- `imgs/`: Directory for local image assets.

## Key Patterns & Conventions

### Layout & Styling
- **Slide Structure**: Each "slide" is a `div.slide-container`.
- **Color Palette**:
  - Backgrounds: Cream `#FFF8E1`, White `#FFFFFF` (alternating).
  - Text/Accents: Dark Brown `#3E2723`, Gold `#D4AF37`, Light Brown `#5D4037`.
- **Typography**:
  - Headings: 'Playfair Display' (Serif).
  - Body: 'Montserrat' (Sans-serif).
- **CSS Approach**: Styles are embedded in the `<head>` of `index.html`. Keep them there for simplicity unless refactoring is explicitly requested.

### Behavior
- **Animations**: Uses `IntersectionObserver` to trigger `.visible` class on `.slide-container` for fade-in/slide-up effects.
- **Navigation**: Currently scroll-based.

### Development Workflow
1.  Edit `index.html`.
2.  Refresh browser to see changes.
3.  Ensure images are placed in `imgs/` before referencing.

## Critical Instructions for AI
- **Language**: The content is in Portuguese (pt-BR). Maintain this language for all text content.
- **Simplicity**: Do not introduce build tools (npm, webpack, etc.) or frameworks (React, Vue) unless specifically asked.
- **Responsiveness**: When modifying layout, ensure flexbox/grid properties handle different screen sizes gracefully, although the primary design is desktop-centric.
- **Asset Management**: Always check if an image exists in `imgs/` or use a placeholder if adding new image elements.
