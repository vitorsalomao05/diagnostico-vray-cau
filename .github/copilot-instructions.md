# Copilot Instructions for V-Ray & Cau Chocolates Diagnostic Presentation

## Project Overview
This is a standalone, static HTML presentation for a strategic AI diagnosis proposal. It is designed as a single-page scrolling website where each section represents a presentation slide. The presentation is protected by a PIN overlay system using localStorage.

## Tech Stack
- **Core**: HTML5, CSS3, Vanilla JavaScript (no frameworks or build tools).
- **External Libraries**: Font Awesome 6.5.1 (CDN), Google Fonts (Playfair Display, Montserrat).
- **Build System**: None. Pure static files - open `index.html` directly in browser.

## Architecture & File Structure
```
index.html                      # Single-file architecture: HTML + embedded CSS + embedded JS
PROPOSTA_CAU_CHOCOLATES.md      # Original proposal document (reference material)
imgs/                           # Image assets
  ├── logo_cau_transp.png       # Client logo
  ├── logo_vray_transp.png      # V-Ray logo
  ├── interior_loja.png         # Store interior
  ├── mao_chocolate.png         # Product photography
  ├── rede_neural.png           # AI visualization
  ├── reuniao.png               # Meeting photo
  ├── roadmap.png               # Timeline graphic
  └── image.png                 # Generic placeholder
```

## Key Patterns & Conventions

### Slide Layout System
Each slide is a `div.slide-container` with multiple layout variants:
- **Standard Layout**: Full-width centered content (`padding: 80px max(20px, calc(50% - 640px))`)
- **Bleed Image Layout**: `.bleed-image-layout` - Two-column grid (50/50 split), image extends full height
- **Rounded Image Layout**: `.rounded-image-layout` - Circular image with gold border (450x450px)
- **Tiled Content**: `.tiled-content` - Flex-based equal-width tiles with icons
- **Timeline Layout**: `.custom-timeline-wrapper` - Horizontal timeline with positioned badges

**Example**: Adding a new standard slide
```html
<div class="slide-container">
    <div class="content-area">
        <h2 class="slide-title">Título do Slide</h2>
        <p>Conteúdo em português...</p>
    </div>
</div>
```

### Color System
- **Backgrounds**: Cream `#FFF8E1` (odd slides), White `#FFFFFF` (even slides)
- **Primary Text**: Dark Brown `#3E2723`
- **Accent**: Gold `#D4AF37` (borders, badges, buttons, icons)
- **Secondary Text**: `#4E342E`, `#5D4037`
- **Shadows**: `rgba(0,0,0,0.05)` to `rgba(0,0,0,0.1)`

### Typography Hierarchy
- **h1**: 72px, Playfair Display 700 (title slide only)
- **h2**: 56px, Playfair Display 700 (`.slide-title`)
- **h3**: 28px, Playfair Display 700 (subsections)
- **body**: 18px, Montserrat 400, line-height 1.6

### Scroll Animation System
- **Mechanism**: `IntersectionObserver` with 15% threshold triggers `.visible` class
- **Initial State**: `opacity: 0`, `transform: translateY(50px)`
- **Animated State**: `opacity: 1`, `transform: translateY(0)` (0.8s ease-out)
- **Trigger**: `initScrollAnimations()` called after PIN verification
- First slide auto-visible on load

### PIN Protection System
- **Constant**: `const CORRECT_PIN = '1234';`
- **Storage**: `localStorage.setItem('cau_presentation_unlocked', 'true');`
- **Verification**: `checkUnlocked()` checks localStorage on load
- **UI**: `#pin-overlay` with `.hidden` class toggle
- **Input**: Numeric-only (`input` event filters `[^0-9]`), max-length enforced

### Responsive Breakpoints
- **Desktop**: Default (1280px max content width)
- **Tablet**: `@media (max-width: 1024px) and (min-width: 769px)` - Reduced padding, 44px headings
- **Mobile**: `@media (max-width: 768px)` - Single column grids, 32px headings, stacked layouts

## Development Workflow
1. Edit `index.html` (all changes happen here)
2. Refresh browser (`Cmd+R`) to see changes
3. Clear localStorage (`localStorage.clear()` in console) to test PIN overlay
4. Verify images exist in `imgs/` before referencing (8 images available)

## Critical Instructions for AI
- **Language**: All content is in Portuguese (pt-BR). Never translate text to English when editing.
- **Single-File Architecture**: Keep CSS in `<style>` and JS in `<script>` within `index.html`. Do not suggest extracting to separate files unless explicitly requested.
- **No Build Tools**: Do not suggest npm, webpack, Vite, or any build process. This is intentionally a static HTML file.
- **Layout Modifications**: When changing `.slide-container` layouts, preserve the alternating background colors (`:nth-child(odd/even)`) and animation classes.
- **Image Paths**: Use relative paths `imgs/filename.png`. Available images: `logo_cau_transp.png`, `logo_vray_transp.png`, `interior_loja.png`, `mao_chocolate.png`, `rede_neural.png`, `reuniao.png`, `roadmap.png`, `image.png`.
- **Animations**: New slides automatically animate on scroll. Do not add redundant animation logic.
- **Responsive Design**: Test changes against mobile breakpoint - grids should collapse to `grid-template-columns: 1fr` and flexboxes to `flex-direction: column`.

## Common Tasks
- **Add Slide**: Copy existing `.slide-container` structure, maintain alternating backgrounds
- **Change PIN**: Update `CORRECT_PIN` constant (line ~948)
- **Add Image**: Place in `imgs/`, reference as `<img src="imgs/filename.png" alt="...">`
- **Modify Colors**: Search for hex codes (`#FFF8E1`, `#D4AF37`) and replace consistently
- **Test Animations**: Add `threshold: 0.5` in `observerOptions` to delay trigger
