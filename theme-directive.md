# Luma Labs Theme Development Directive

This document outlines the core principles and standards for developing and modifying the Luma Labs Shopify Theme. Any future edits or new sections **MUST** strictly adhere to these guidelines.

## 1. Zero Tailwind Dependence
- This theme **DOES NOT** use Tailwind CSS.
- **NEVER** use Tailwind utility classes (e.g., `flex`, `pt-4`, `md:grid-cols-3`) in Liquid files. They will not render correctly and will break the layout.

## 2. Native CSS and BEM Architecture
- Write standard, vanilla CSS within `<style>` blocks in the respective `.liquid` section files.
- Follow **BEM (Block Element Modifier)** methodology for class naming (e.g., `.luma-collection`, `.luma-collection__header`, `.luma-card--barrier`) to prevent global style conflicts.
- Ensure all CSS is scoped to perfectly match its specific section using section IDs or specific wrapper classes to avoid leaking styles.

## 3. Leverage Native Theme Blocks
- The theme comes with a rich set of native blocks (e.g., `luma-pill`, `luma-heading`, `text`, `image`).
- New sections MUST support these native theme blocks by including `{"type": "@theme"}` and `{"type": "@app"}` in their `<schema>` blocks array.
- **Do not hardcode text fields** (like Titles, Descriptions, Eyebrows) directly into a Section's schema if standard theme blocks can be used instead. This reduces schema bloat, ensures consistency, and gives the merchant complete control over content hierarchy and styling.

## 4. Performance & Speed
- **Keep it lightweight:** Exclude arbitrary JavaScript unless strictly necessary for complex functionality. Rely on native CSS features like `mix-blend-mode`, `:hover`, and CSS transitions for interactivity.
- **Optimize Images:** Preload critical assets and ALWAYS use Shopify's native `image_url` and `image_tag` features with `loading: 'lazy'` properly configured for media. Give explicit `sizes` attributes for responsive loading.
- **Fast DOM:** Avoid excessive nesting of `div` elements. Keep the generated DOM lightweight and fast.

## 5. High-Impact Aesthetic (Luma Labs specific)
- **Glassmorphism:** Implement 'frosted glass' effects using standard CSS (`backdrop-filter: blur(x)` and `background: rgba(255,255,255,0.x)`).
- **Branded Gradients:** Use gradient overlays configured via section schema to achieve the branded visual tinting on background images. Ensure gradients blend well with images using `mix-blend-mode: multiply` and adjustable opacities.
- **Micro-interactions:** Add subtle hover effects like slight image scaling (`transform: scale(1.05)`) and smooth shadow elevation (`transform: translateY(-4px)`).
