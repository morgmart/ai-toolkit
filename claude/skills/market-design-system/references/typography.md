# Market Design System - Typography Reference

## Font Family

### Cash Sans (Current - February 2026+)
As of February 2026, Market and all Square products use **Cash Sans** — part of Block's Universal UI unification effort.

**All new design work for Square should use Cash Sans.**

### Access
- **Figma**: Preloaded for all Block Figma org designers
- **Other apps**: Download at go/cashsansfont

### Deprecated Fonts
Replace these with Cash Sans if encountered:
- Square Sans (2022–2025)
- Square Sans Text / Display / Mono
- SQ Market (pre-2022)

### Language Support
- **Latin-based languages**: Full support (Western, Central, Northern European)
- **Japanese**: Use Hiragino Sans
- **Chinese/Korean**: Under consideration

### Fallback Fonts
| Platform | Fallback |
|----------|----------|
| Web (Apple) | Helvetica |
| Web (Windows) | Arial |
| Android | Roboto |
| iOS | SF Pro |

---

## Type Styles

### Display Styles
Largest, most expressive. Reserved for short, important text or numerals.

**Use for:**
- Large stats in Dashboard overview
- Large customer-facing POS screens
- Hero numbers

**Note:** Most seller-facing web/iOS designs won't use Display — use Heading instead.

### Heading Styles
Primary hierarchy for page structure.

| Style | Use |
|-------|-----|
| Heading 30 | Page titles |
| Heading 20 | Section titles |
| Heading 10 | Subsection titles |
| Heading 5 | Eyebrow over heading |

### Paragraph Styles
Body copy and content.

| Style | Use |
|-------|-----|
| Paragraph 30 | **Default** body copy |
| Paragraph 20 | Smaller text (captions, helper text) |
| Paragraph 10 | Smallest (table subtext) |

**Note:** Default text style is Paragraph 20 for historical reasons; may be adjusted so all platforms use Paragraph 30.

### Tabular Styles
For number-only text blocks (not in sentences with words).

- Same size, weight, line height as regular styles
- **Monospaced setting enabled** for better scanning
- Numbers are more spaced out for readability

In Figma: Enable "Tabular figures" in text settings.

### Mono Styles
For displaying developer code.

- Used by Square Developer team
- Used in `code` component
- Use when showing programming language

---

## Type Weights

### Display & Headings
- **Semibold**: Primary emphasis
- **Medium**: Secondary emphasis

### Labels & Paragraphs
| Weight | Use |
|--------|-----|
| **Semibold** | Strong emphasis |
| **Medium** | Subtler emphasis, row/table headers |
| **Regular** | Paragraph text |

---

## Page Hierarchy

Standard page structure:

```
Page Title (Heading 30)
    ↓ 16px spacing
Section Title (Heading 20)
    ↓ 8px spacing
Body Copy (Paragraph 30)
    ↓ 40px spacing
Next Section Title (Heading 20)
```

### Spacing Between Sections
- **40px** between major sections
- **24px** within sections

---

## Bottom Spacing by Type Style

| Type Style | Bottom Spacing | Use Case |
|------------|----------------|----------|
| Display 30 | - | - |
| Display 20 | - | - |
| Display 10 | 24px | Large standalone statistics |
| Heading 30 | 16px | Page title |
| Heading 20 | 8px | Section title |
| Heading 10 | 8px | Subsection |
| Heading 5 | 4px | Eyebrow over heading |
| Paragraph 30 | 16px | Most body copy |
| Paragraph 20 | 14px | Row subtext, helper text |
| Paragraph 10 | 12px | Table subtext, caption |

---

## Text Formatting Guidelines

### Alignment
✅ **Left-align text** (default)
- Easier to read
- Consistent starting point for scanning

### Paragraph Width
✅ **Be aware of line length**
- Too wide = hard to track to next line
- Too narrow = choppy reading
- Optimal: 50-75 characters per line

### Case
✅ **Use sentence case**
- Capitalize first word and proper nouns only
- Enhances legibility
- Provides human tone
- Better for localization

**Examples:**
- ✅ "Create new item"
- ❌ "Create New Item"
- ✅ "Square Dashboard"
- ❌ "square dashboard"

---

## Quick Reference

### Default Styles
```
Page title:     Heading 30
Section title:  Heading 20
Body copy:      Paragraph 30
Helper text:    Paragraph 20
Caption:        Paragraph 10
```

### Spacing Scale
```
Between sections: 40px (spacing-500)
Within sections:  24px (spacing-300)
After headings:   8-16px
After paragraphs: 12-16px
```

### Font Stack
```css
font-family: "Cash Sans", Helvetica, Arial, sans-serif;
```
