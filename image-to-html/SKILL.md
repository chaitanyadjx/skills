---
name: image-to-webpage
description: Convert any image (screenshot, mockup, design, photo of UI) into a pixel-perfect, fully functional HTML/CSS webpage that faithfully reproduces the visual layout. Use this skill whenever a user uploads an image and asks to "convert to HTML", "turn into a webpage", "code this design", "recreate this UI", "build this page", "make this into code", or any similar intent to replicate a visual as a webpage. Also trigger when the user shares a screenshot of a website, app UI, wireframe, or design mockup and wants it built. Prioritize this skill over generic frontend-design when the goal is FAITHFUL REPRODUCTION rather than creative redesign.
---

# Image to Webpage Skill

Convert a provided image into a production-quality HTML/CSS/JS webpage that **exactly matches** the visual appearance of the image — layout, spacing, colors, typography, content, and structure.

## Core Principle: Faithful Reproduction

Your #1 goal is pixel-perfect fidelity to the source image. This is NOT a redesign task. Do not:
- Change colors, fonts, or spacing beyond what's needed to implement faithfully
- Simplify complex layouts
- Add features not visible in the image
- Apply your own design opinions

## Step-by-Step Process

### 1. Analyze the Image Thoroughly

Before writing any code, carefully inspect the image and identify:

**Layout Structure**
- Overall page layout (single column, multi-column, grid, flex)
- Header, nav, hero, sections, sidebar, footer presence
- Approximate proportions and spacing between elements

**Typography**
- Font styles: serif, sans-serif, monospace, display
- Font sizes (relative: large heading, subheading, body, caption)
- Font weights (light, regular, medium, bold, black)
- Text alignment, line height, letter spacing
- Any special text treatments (gradient text, outlined, underlined)

**Colors**
- Background colors (page, sections, cards)
- Text colors
- Accent/brand colors
- Border colors
- Gradient directions and stops

**Components**
- Buttons (shape, style, size, color)
- Cards and their shadows/borders
- Navigation items and style
- Images/icons (describe placeholders if not reproducible)
- Form inputs, tables, lists
- Badges, tags, chips

**Spacing & Sizing**
- Padding and margins (tight, moderate, generous)
- Max-width and centering
- Border radius values
- Box shadows

### 2. Choose the Right Implementation

| Image Type | Recommended Approach |
|---|---|
| Simple landing page / marketing | Single HTML file with inline CSS |
| Dashboard / data UI | HTML + CSS Grid + placeholder charts |
| Mobile app screen | HTML with mobile viewport, flex layout |
| Complex multi-section page | Sectioned HTML with CSS custom properties |
| Form / input-heavy UI | HTML form elements with custom CSS |

Always output a **single self-contained HTML file** unless the user specifies otherwise.

### 3. Implementation Rules

**Fonts**
- Use Google Fonts (`<link>` in `<head>`) to match the closest available font
- For system-looking UIs: use `-apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif`
- For editorial/display: pick a Google Font that closely matches

**Colors**
- Extract exact hex values by carefully observing the image
- Use CSS custom properties (`--color-primary`, etc.) for reuse
- For gradients, replicate direction and approximate stops

**Images & Icons**
- For photos: use `https://picsum.photos/{width}/{height}` as placeholders
- For icons: use inline SVGs from common icon patterns, or Unicode symbols, or Font Awesome via CDN if many icons are needed:
  ```html
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
  ```
- For logos: recreate with CSS/SVG text if simple, or use a placeholder div with the brand name

**Layout**
- Prefer CSS Grid for 2D layouts, Flexbox for 1D
- Use `max-width` + `margin: auto` for centered content
- Match responsive behavior if visible (but default to desktop if unclear)

**Interactivity**
- Add hover states for buttons, links, nav items if the original likely has them
- Add basic JS interactions only if clearly implied (e.g., dropdown nav, tab switching, modal)
- Keep JS minimal and functional — no over-engineering

### 4. Quality Checklist Before Outputting

Before finalizing, verify:
- [ ] Color palette matches the image
- [ ] Font choices approximate the original
- [ ] Spacing and proportions are close
- [ ] All visible text content is included
- [ ] All major sections/components are present
- [ ] Buttons, links, cards are styled correctly
- [ ] No placeholder text left in if real text is visible in image
- [ ] The page renders correctly at a similar viewport width

### 5. Output Format

Output a **single `.html` file** saved to `/mnt/user-data/outputs/webpage.html`.

Structure:
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>[Page title from image]</title>
  <!-- Google Fonts if needed -->
  <!-- Font Awesome if icons needed -->
  <style>
    /* CSS custom properties for colors */
    /* Reset & base styles */
    /* Component styles */
  </style>
</head>
<body>
  <!-- Faithful HTML structure -->
  <script>
    /* Minimal JS only if needed */
  </script>
</body>
</html>
```

### 6. Communication

After outputting the file:
- Briefly note any parts that couldn't be replicated exactly (e.g., custom fonts not on Google Fonts, complex SVG illustrations)
- Mention any assumptions made (e.g., "used Picsum placeholders for product images")
- Offer to refine specific sections if needed

## Common Pitfalls to Avoid

- **Don't guess colors** — look carefully. A "dark blue" might be `#1a2b4c`, not `#003366`.
- **Don't omit small details** — badges, dividers, icon placements, subtle shadows matter.
- **Don't simplify grids** — if a 3-column card grid is visible, implement 3 columns.
- **Don't add unseen elements** — no extra CTAs, sections, or features not in the image.
- **Don't use generic placeholder layouts** — the image IS the spec, follow it exactly.