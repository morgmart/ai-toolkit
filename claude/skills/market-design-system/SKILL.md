---
name: Market Design System
description: Square's Market design system for building consistent, accessible UI components. Use when working with Market web components, design tokens, or building Square seller interfaces. Covers component usage, token reference, typography (Cash Sans), UX patterns (errors, loading, filtering, navigation), theming, and accessibility. Essential for any Square Dashboard or seller-facing UI work.
compatibility: Web Components, React, TypeScript, CSS
---

# Market Design System

Market is Square's design system built on Web Components. It provides UI components and design tokens for building consistent, accessible seller interfaces across Square products.

## Quick Start

### Import Components
```html
<!-- Load Market -->
<script type="module" src="./build/market.esm.js"></script>
<link rel="stylesheet" href="./build/market.css">

<!-- Enable features -->
<body market-features="typography">

<!-- Use components -->
<market-button>Click me</market-button>
<market-input-text label="Email" type="email"></market-input-text>
```

### Enable Dark Mode
```html
<body market-features="typography" data-market-theme="dark">
```

### Storybook
**URL**: https://market-storybook.s3.amazonaws.com/2.10.0/index.html

---

## Core Principles

| Principle | Description |
|-----------|-------------|
| **8px Grid** | All spacing from `--core-base-size: 8px` |
| **Semantic Tokens** | Use `critical`, `success`, `warning` over raw colors |
| **Theme Aware** | Colors auto-adapt to light/dark mode |
| **Accessibility First** | ARIA, focus management, keyboard nav built-in |

---

## Typography (Cash Sans)

As of February 2026, all Square products use **Cash Sans** font.

### Type Hierarchy
```
Page title:     Heading 30    (+ 16px bottom spacing)
Section title:  Heading 20    (+ 8px bottom spacing)
Body copy:      Paragraph 30  (+ 16px bottom spacing)
Helper text:    Paragraph 20  (+ 14px bottom spacing)
```

### Formatting Rules
- ✅ Left-align text
- ✅ Use sentence case ("Create new item" not "Create New Item")
- ✅ 50-75 characters per line

> **Full reference**: See `references/typography.md`

---

## Essential Tokens

### Spacing (8px grid)
```css
--core-metrics-spacing-100   /* 8px - default */
--core-metrics-spacing-200   /* 16px - comfortable */
--core-metrics-spacing-300   /* 24px - within sections */
--core-metrics-spacing-500   /* 40px - between sections */
```

### Border Radius
```css
--core-radius-100   /* 6px - default */
--core-radius-50    /* 3px - small elements */
--core-radius-200   /* 12px - large elements */
```

### Text Colors
```css
--core-text-10-color   /* Primary - 90% */
--core-text-20-color   /* Secondary - 55% */
--core-text-30-color   /* Disabled - 30% */
```

### Semantic Colors
```css
--core-critical-fill-color   /* Error backgrounds */
--core-critical-text-color   /* Error text */
--core-success-fill-color    /* Success backgrounds */
--core-warning-fill-color    /* Warning backgrounds */
--core-fill-emphasis-color   /* Themeable interactive */
```

### Surfaces (Elevation)
```css
--core-surface-5-color    /* No elevation (page bg) */
--core-surface-10-color   /* Minimal (card) */
--core-surface-20-color   /* Moderate (modal) */
--core-surface-30-color   /* Highest (popover) */
```

> **Full reference**: See `references/tokens.md`

---

## Key Components

### Actions
- `<market-button>` - Primary, secondary, destructive variants
- `<market-link>` - Navigation links

### Forms
- `<market-input-text>` - Text inputs with validation
- `<market-select>` - Dropdowns
- `<market-checkbox>` / `<market-radio>` - Selection
- `<market-toggle>` - On/off switches

### Layout
- `<market-accordion>` - Collapsible sections
- `<market-card>` - Content containers
- `<market-modal>` / `<market-dialog>` - Overlays
- `<market-tabs>` - Tabbed navigation

### Feedback
- `<market-toast>` - Transient notifications
- `<market-banner>` - Persistent alerts
- `<market-loading>` - Loading indicators
- `<market-inline-status>` - Field validation

> **Full reference**: See `references/components.md`

---

## Critical UX Patterns

### Error Handling
```
✅ Be clear (plain language)
✅ Be actionable (provide next steps)  
✅ Show empathy (don't blame)
```

| Scope | Component | Use When |
|-------|-----------|----------|
| Field | Inline status | Input validation |
| Form | Banner (top) | Multiple errors on submit |
| Page | Toast | Transient, non-blocking |
| Page | Banner | Persistent, high-priority |
| Page | Dialog | Requires immediate action |

**Key rule**: Keep buttons active. Show errors on submit, don't disable.

### Loading States
| Duration | Treatment |
|----------|-----------|
| < 2s | None needed |
| 2-10s | Loading indicator or skeleton |
| 10s+ | Indicator + message + progress + cancel |

### Status Variants
```
neutral  - Informational
info     - High-interest
success  - Completion
warning  - Potential issue
critical - Error/failure
```

> **Full reference**: See `references/patterns.md`

---

## Color System

### Semantic Naming
Colors are contextual and memorable:
- **Text**: For typography (text-10, text-20, text-30)
- **Fill**: For UI elements except text/background
- **Surface**: For backgrounds/elevation
- **Divider**: For separators

### Mode Support
- Light mode: Default
- Dark mode: Set via `data-market-theme="dark"`

### Transparency
Text, Fill, Divider use transparency. **Don't convert to opaque** — use library colors directly.

---

## Responsive Design

### Web: Breakpoints
| Name | Range |
|------|-------|
| Narrow | 0-599px |
| Medium | 600-839px |
| Wide | 800-1023px |
| Extra Wide | 1024px+ |

### Native: Size Classes
iOS and Android use horizontal/vertical size classes for adaptive layouts.

---

## Accessibility Checklist

- [ ] Errors announced by screen readers
- [ ] Focus moves to error summary on validation
- [ ] Don't rely on color alone for status
- [ ] All interactive elements keyboard accessible
- [ ] Use `--core-focus-ring-*` for custom focus states
- [ ] Labels on all form inputs
- [ ] Icons paired with text share same color

---

## Anti-Patterns

| ❌ Don't | ✅ Do Instead |
|----------|---------------|
| Disable buttons for validation | Keep active, show errors on submit |
| Tooltips on disabled elements | Use inline status to explain |
| Hardcode colors | Use semantic tokens |
| Arbitrary spacing (7px) | Use spacing scale tokens |
| Color-only status | Combine with icons/text |
| Title Case for UI text | Use sentence case |
| Custom border radius | Use radius tokens |

---

## Resources

| Resource | Description |
|----------|-------------|
| `references/tokens.md` | Complete token reference (spacing, colors, radius) |
| `references/typography.md` | Cash Sans, type styles, hierarchy |
| `references/components.md` | Component API & examples |
| `references/patterns.md` | UX patterns (errors, loading, filtering) |
| `references/guidelines.md` | Design principles & anti-patterns |
| [Storybook](https://market-storybook.s3.amazonaws.com/2.10.0/index.html) | Live component examples |
| [Market Icon Library](https://go/MarketIconLibrary) | Figma icon library |
| go/cashsansfont | Cash Sans font download |
| go/mr | Mobile releases (catalog apps) |
