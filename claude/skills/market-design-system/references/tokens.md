# Market Design System - Complete Token Reference

## Design Token Philosophy

Design tokens are values needed to construct and maintain a design system — spacing, color, typography, object styles, animation — represented as data. They create an **abstract identity** and centralize the source of truth, enabling consistency across platforms (design, web, mobile).

---

## Base Unit
```css
--core-base-size: 8px
--core-text-size: 16px
```

---

## Spacing Scale

Market uses the **8pt grid system** — all spacing values are divisible by 4.

| Token | Value | Use Case |
|-------|-------|----------|
| `--core-metrics-spacing-25` | 2px | Hairline gaps |
| `--core-metrics-spacing-50` | 4px | Tight spacing, icon gaps |
| `--core-metrics-spacing-100` | 8px | Default spacing |
| `--core-metrics-spacing-150` | 12px | Comfortable spacing |
| `--core-metrics-spacing-200` | 16px | Component padding |
| `--core-metrics-spacing-300` | 24px | Within sections |
| `--core-metrics-spacing-400` | 32px | Large gaps |
| `--core-metrics-spacing-500` | 40px | Between sections |
| `--core-metrics-spacing-600` | 48px | Page sections |
| `--core-metrics-spacing-800` | 64px | Major sections |
| `--core-metrics-spacing-1000` | 80px | Large page sections |

### Spacing Guidelines
- **Relationships**: Elements near each other appear meaningfully related
- **Hierarchy**: More space = more importance
- **White space**: Use to break up sections and create focus
- **Responsive**: OK to step down scale on mobile (e.g., 1000 → 800 or 500)

---

## Border Radius

| Token | Value | Use Case |
|-------|-------|----------|
| `--core-radius-50` | 3px | ~50% of default |
| `--core-radius-100` | 6px | **Default** - most components |
| `--core-radius-150` | 9px | ~150% of default |
| `--core-radius-200` | 12px | Larger elements |
| `--core-radius-full` | 9999px | Fully rounded (pills, avatars) |

### Border Radius Guidelines
- Default is **6px** (radius-100)
- Smaller objects → smaller radius
- Larger objects → larger radius
- Don't use custom values (e.g., 7px) — use tokens only
- Most elements use same radius on all four corners

### Size-Based Recommendations
| Object Size | Recommended Radius |
|-------------|-------------------|
| Small (< 32px) | radius-50 (3px) |
| Medium (32-64px) | radius-100 (6px) |
| Large (> 64px) | radius-150 or radius-200 |

---

## Breakpoints

| Name | Min Width | Max Width | Use Case |
|------|-----------|-----------|----------|
| Narrow | 0px | 599px | Mobile phones |
| Medium | 600px | 839px | Tablets |
| Wide | 800px | 1023px | Small desktops |
| Extra Wide | 1024px | - | Desktop/large screens |

### CSS Variables
```css
--core-breakpoint-narrow-min-width: 0px
--core-breakpoint-narrow-max-width: 599px
--core-breakpoint-medium-min-width: 600px
--core-breakpoint-medium-max-width: 839px
--core-breakpoint-wide-min-width: 800px
--core-breakpoint-wide-min-max-width: 1023px
--core-breakpoint-extra-wide-min-width: 1024px
```

---

## Color System

### Mode Support
- **Light mode**: Default, optimal for bright environments
- **Dark mode**: Set via product settings, for low-light environments

### Transparency
Text, Fill, and Divider colors use transparency to blend with surfaces. **Don't convert translucent colors to opaque** — use the library colors directly.

---

## Text Colors

Text colors meet accessibility standards.

| Token | Light Mode | Dark Mode | Use |
|-------|------------|-----------|-----|
| `--core-text-10-color` | rgba(0,0,0,0.9) | rgba(255,255,255,0.95) | Primary text (headings, paragraphs) |
| `--core-text-20-color` | rgba(0,0,0,0.55) | rgba(255,255,255,0.55) | Secondary (subtext, helper, placeholder) |
| `--core-text-30-color` | rgba(0,0,0,0.3) | rgba(255,255,255,0.3) | Tertiary/disabled (doesn't need a11y) |
| `--core-text-inverse-color` | rgba(255,255,255,0.95) | rgba(0,0,0,0.9) | Text on contrasting background |
| `--core-text-black-color` | rgba(0,0,0,0.9) | rgba(0,0,0,0.9) | Always black (error text) |
| `--core-text-white-color` | rgba(255,255,255,1) | rgba(255,255,255,1) | Always white (button text) |

### Semantic Text Colors

| Token | Use |
|-------|-----|
| `--core-text-emphasis-color` | Themeable. Interactive elements (links, secondary buttons) |
| `--core-text-success-color` | Positive (password updated) |
| `--core-text-warning-color` | Prevent issues (low inventory) |
| `--core-text-critical-color` | Alarming (delete, errors) |

**Rule**: Icons paired with text labels share the same Text color.

---

## Fill Colors

Applied to all UI elements except text and background.

| Token | Light Mode | Dark Mode | Use |
|-------|------------|-----------|-----|
| `--core-fill-10-color` | rgba(0,0,0,0.9) | rgba(255,255,255,0.95) | Primary elements (nav icons) |
| `--core-fill-20-color` | rgba(0,0,0,0.3) | rgba(255,255,255,0.3) | Secondary, component borders |
| `--core-fill-30-color` | rgba(0,0,0,0.15) | rgba(255,255,255,0.15) | Non-interface borders (text fields) |
| `--core-fill-40-color` | rgba(0,0,0,0.05) | rgba(255,255,255,0.08) | Component backgrounds (secondary button) |
| `--core-fill-50-color` | rgba(0,0,0,0.03) | rgba(255,255,255,0.05) | Section contrast |
| `--core-fill-inverse-color` | rgba(255,255,255,0.95) | rgba(0,0,0,0.9) | Elements on contrasting background |
| `--core-fill-black-color` | rgba(0,0,0,0.9) | rgba(0,0,0,0.9) | Always black (modal overlay) |
| `--core-fill-white-color` | rgba(255,255,255,1) | rgba(255,255,255,1) | Always white (toast error icon) |

### Semantic Fill Colors

| Token | Use |
|-------|-----|
| `--core-fill-emphasis-color` | Themeable. Primary button, selected checkbox |
| `--core-fill-success-color` | Banner success icon |
| `--core-fill-warning-color` | Toast warning icon |
| `--core-fill-critical-color` | Error text icon |

---

## Surface Colors

Convey elevation from background.

| Token | Light Mode | Dark Mode | Use |
|-------|------------|-----------|-----|
| `--core-surface-5-color` | #FFFFFF | #0D0D0D | No elevation (index page, full modal) |
| `--core-surface-10-color` | #FFFFFF | #1A1A1A | Minimal elevation (card, banner) |
| `--core-surface-20-color` | #F7F7F7 | #262626 | Considerable elevation (modal) |
| `--core-surface-30-color` | #F0F0F0 | #333333 | Highest elevation (popover, dialog) |
| `--core-surface-inverse-color` | - | - | Surface on contrasting background (toast) |

---

## Divider Color

Separates content and creates boundaries. Noticeable but subtle.

```css
--core-divider-10-color  /* Theme-aware border/divider */
```

---

## Extended Color Palette

14 color categories with tints and shades for recognition and wayfinding.

### Color Variants (using Orange as example)

| Variant | Use |
|---------|-----|
| `fill` | UI elements (item tile, badge fill) |
| `text` | Text to meet a11y (link, tertiary button) |
| `10` | System shade (primary button active) |
| `20` | System shade (primary button hover) |
| `30` | System tint (secondary button active) |
| `40` | System tint (banner fill) |

### Available Colors
- **Blue** - Primary interactive, emphasis
- **Green** - Success states
- **Red** - Critical/error states
- **Yellow** - Warning states
- **Orange** - Accent
- **Purple** - Accent
- **Pink** - Accent
- **Burgundy** - Accent
- **Teal** - Accent
- **Sky** - Accent
- **Forest** - Accent
- **Gold** - Accent
- **Brown** - Accent
- **Taupe** - Neutral accent

---

## Focus States

| Token | Value |
|-------|-------|
| `--core-focus-color` | Blue fill (theme-aware) |
| `--core-focus-ring-color` | Blue fill (theme-aware) |
| `--core-focus-ring-border-size` | 2px |
| `--core-focus-ring-buffer-size` | 2px |

### Usage
```css
.custom-element:focus-visible {
  outline: var(--core-focus-ring-border-size) solid var(--core-focus-ring-color);
  outline-offset: var(--core-focus-ring-buffer-size);
}
```

---

## Animation Tokens

### Enter Transitions (elements appearing)
```css
--core-animation-enter-transition-easing: cubic-bezier(0.26, 0.10, 0.48, 1.0)
--core-animation-enter-transition-fast-speed-duration: 0.10s
--core-animation-enter-transition-moderate-speed-duration: 0.24s
--core-animation-enter-transition-slow-speed-duration: 0.40s
```

### Exit Transitions (elements disappearing)
```css
--core-animation-exit-transition-easing: cubic-bezier(0.52, 0.0, 0.74, 0.0)
--core-animation-exit-transition-fast-speed-duration: 0.10s
--core-animation-exit-transition-moderate-speed-duration: 0.16s
--core-animation-exit-transition-slow-speed-duration: 0.30s
```

### Move Transitions (elements repositioning)
```css
--core-animation-move-transition-easing: cubic-bezier(0.76, 0.0, 0.24, 1.0)
--core-animation-move-transition-fast-speed-duration: 0.10s
--core-animation-move-transition-moderate-speed-duration: 0.24s
--core-animation-move-transition-slow-speed-duration: 0.40s
```

### Keyframe Animations
- `market-fade-in` / `market-fade-out`
- `market-popup` / `market-popdown`
- `market-slideup` / `market-slidedown`
- `market-slide-left-enter` / `market-slide-left-exit`

---

## Grid System

### CSS Classes
```css
.market-grid-container   /* Responsive grid wrapper */
.market-grid-item-small  /* Small grid item */
.market-grid-item-medium /* Medium grid item */
.market-grid-item-large  /* Large grid item */
.market-grid-item-full   /* Full-width item */
```

### Grid Variables
```css
--core-grid-extra-wide-viewport-column-count
--core-grid-extra-wide-viewport-gutter-size
--core-grid-extra-wide-viewport-margin-size
--core-grid-medium-viewport-column-count
--core-grid-medium-viewport-gutter-size
--core-grid-medium-viewport-margin-size
--core-grid-narrow-viewport-column-count
--core-grid-narrow-viewport-gutter-size
--core-grid-narrow-viewport-margin-size
--core-grid-wide-viewport-column-count
--core-grid-wide-viewport-gutter-size
--core-grid-wide-viewport-margin-size
```
