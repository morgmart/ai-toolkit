# Market Design System - UX Patterns Reference

## Table of Contents
1. [Actions & Navigation](#actions--navigation)
2. [Error Handling](#error-handling)
3. [Status & Notifications](#status--notifications)
4. [Loading States](#loading-states)
5. [Filtering](#filtering)
6. [Selection Controls](#selection-controls)
7. [Disabled States](#disabled-states)
8. [Footers](#footers)
9. [Modals](#modals)
10. [Scanning](#scanning)
11. [Progress Tracking](#progress-tracking)
12. [AI Features](#ai-features)

---

## Actions & Navigation

Action components trigger contextual changes. Three categories:

### Navigation Components
Navigate to new screens or sections.

| Component | Contextual Change |
|-----------|-------------------|
| Link | Navigates to new screen or section |
| Action card | Navigates to new screen (can also be selection) |
| Item tile | Navigates to new screen (can also be selection) |
| Row | Navigates to new screen or overlay surface |

### Trigger Components
Enable actions or open new contexts within the same screen.

| Component | Contextual Change |
|-----------|-------------------|
| Button | Triggers action, opens context, or navigates |

### State Components
Load different versions of current screen.

| Component | Contextual Change |
|-----------|-------------------|
| Paging tabs | Loads different state based on user input |
| Pagination | Loads different state based on user input |

---

## Error Handling

### Principles
✅ **Be clear** - Describe the issue in plain language, avoid jargon
✅ **Be actionable** - Provide next steps to resolve
✅ **Show empathy** - Focus on support, avoid blame

### Anatomy of Error Messages
```
[What went wrong] + [How to fix it]
```
Can omit "what went wrong" if "how to fix it" covers it.

### Preventing Errors
- **Progressive disclosure**: Show only what's needed at each step
- **Forgiving formats**: Allow different input formats (11-01-2011 or 11.1.11)
- **Default values**: Provide smart defaults when possible
- **Friction before destructive actions**: Use confirmation modals

### Error Types by Scope

#### Field-Level Errors
Place inline, close to the issue. Use component error states or Inline status.

**Timing options:**
- When user completes a field (recommended for most cases)
- As user types (good for character limits, password strength)
- On form submission (for required fields, backend validation)

#### Form-Level Errors
Use Banner at top of form to summarize errors. Keep field-level errors in place.
- Avoid positional language ("fix errors below")
- **Keep buttons active** even when required fields incomplete
- Use error messages over disabled buttons

#### Page-Level Errors

| Component | Use When |
|-----------|----------|
| **Toast** (critical variant) | Lightweight, transient errors that don't block user |
| **Banner** | Persistent, high-priority errors requiring attention |
| **Dialog** | Error requires direct action, blocks critical task |

#### Loading Errors
Use Loading indicator error state + error message explaining what went wrong.

#### File Upload Errors
Use File upload error variant for affected element.

### Accessibility Requirements
- Error messages must be announced by screen readers
- Focus moves to error summary on validation failure
- Messages linked to relevant field/action
- Don't rely on color alone to signal errors

---

## Status & Notifications

### Component Types

| Type | Description |
|------|-------------|
| **Indicator** | Supplementary info about dynamic content |
| **Validation** | Communicates input correctness |
| **Notice** | Informs of system state changes |

### Status Components

| Component | Type | Context | Feedback | Trigger |
|-----------|------|---------|----------|---------|
| Badge | Indicator | Inline | Passive | System |
| Icons | Indicator | Specific | Passive | System |
| Pill | Indicator | Specific | Passive | System |
| Inline status | Validation | Specific | Passive/Required | User action |
| Toast | Validation | Global | Recommended | System |
| Banner | Notice | Specific/Global | Required | System |

### Status Variants

| Variant | Usage |
|---------|-------|
| `neutral` | Neutral content |
| `info` | High-interest informational content |
| `critical` | Serious error |
| `warning` | Potential error or problem |
| `success` | Success at end of process |

---

## Loading States

### When to Show Loading

| Duration | Treatment |
|----------|-----------|
| < 2 seconds | No loading state needed |
| 2-10 seconds | Loading indicator or skeleton |
| 10+ seconds | Loading indicator + messaging + progress |

### Component Selection

| Component | Use When |
|-----------|----------|
| **Loading indicator** | System operations, limited space, unpredictable layouts |
| **Skeleton loader** | Initial page load with predictable layouts |
| **Linear progress bar** | Loading state in Toast |

### Skeleton Loaders
- Match actual content layout
- Show simplified versions of cards, lists, tables
- Don't use for toasts, popovers, dropdowns
- Shimmer animates across full screen
- Smooth transition to loaded content

### Loading Indicators

#### 2-10 Seconds
- Can use alone or with copy ("Loading...", "Sorting...")
- Can show percentage progress

#### 10+ Seconds
- Include clear messaging about what's happening
- Show approximate wait time ("usually takes less than a minute")
- Display exact progress when possible
- Provide Close/Back button to cancel
- Consider allowing navigation away with background completion

### Inline Loading
- Place indicator close to/within affected component
- Use in-button loading when action was initiated by that button

### Full Screen Overlays
Use when action temporarily disables further interaction.

### Pull to Refresh (Mobile)
Show loading indicator if page takes > 400ms to load.

### Error States
Clearly communicate failure and allow retry.

---

## Filtering

### Anatomy
- **Category**: Property of items (color, price)
- **Value**: Specific value or range (red, < $100)
- **Relative**: Relationship (is, between, and/or)

Formula: `category + relative + value = criteria`

### Filtering Components

| Component | Use Case |
|-----------|----------|
| Action cards | Add context to each option |
| Chips | Icons/words in compact area |
| Checkboxes | Multiple independent options |
| Choice buttons | Multi or single-select from set |
| Dropdown button | Choose from group of actions |
| Filter buttons | Refine by predefined dimension |
| Radio buttons | Mutually exclusive, select one |
| Segmented control | Toggle between related views |
| Select field | Single or multi-select dropdown |
| Sliders | No specific min/max (pair with text fields) |
| Toggles | Two mutually exclusive options |

### Best Practices

#### Layout
- Display applied filters in overview
- Use sticky "Apply" button on mobile
- Locate promoted filters at start
- Separate filtering and sorting tools

#### Behavior
- Allow combining multiple options within same category
- Use intuitive logic: categories = AND, values within = OR
- Update filter availability based on current scope
- Truncate lists > 8 options on desktop
- Allow search for lists > 15 options
- Show match count for each option

#### Content
- Provide filters for essential categories
- Use understandable naming (no jargon)
- Visually indicate category hierarchy
- Order untruncated options by popularity
- Use alphabetical for many options
- Use text fields or sliders for numeric values

---

## Selection Controls

### Component Comparison

| Component | Options | Selections | Default | Effect |
|-----------|---------|------------|---------|--------|
| Checkbox (multi) | Multiple | 0 to all | No | On submit |
| Checkbox (standalone) | 1 | Yes/No | Yes | On submit |
| Choice button | Multiple | Varied | Yes | On submit |
| Dropdown button | Multiple | 0 to all | No | On submit |
| Radio button | Multiple | 1 | Optional | On submit |
| Segmented control | 2-5 | 1 | Yes | Immediate |
| Select field | Multiple | 1 | Optional | On submit |
| Toggle | 1 | On/Off | Yes | Immediate |

### When to Use What

- **Checkbox**: Independent options, select any number
- **Radio**: Mutually exclusive, must select one
- **Toggle**: On/off, immediate effect
- **Segmented control**: Toggle views, immediate effect
- **Select field**: Many options, single selection
- **Choice button**: Visual selection from set

---

## Disabled States

### Best Practices

1. **Don't make disabled components interactive**
   - No tooltips on disabled elements
   - Assistive technology skips disabled content
   - No affordances to indicate interactivity

2. **Avoid disabling main CTA in forms**
   - Keep buttons active
   - Use error messages instead

3. **Consider hiding vs disabling**

| Approach | When to Use |
|----------|-------------|
| **Disabled** | Feature discoverability, learning, temporary states |
| **Hidden** | Reduce cognitive load, permissions, privacy |

### Rows with Disabled Elements
- Add inline status to explain why disabled
- Hide control and replace with link or pill

---

## Footers

### What is a Footer?
Opaque container fixed at bottom of modal/sidebar. Holds important info or interactions that must remain visible when scrolling.

### When to Use
- Increase prominence for important CTAs
- Improve ergonomics on mobile (closer to thumb)
- Solve for limited screen space

### Guidelines

1. **Consider common patterns first**
   - Reserve for when content must stay in viewport (e.g., cart/checkout)

2. **Only one primary button at a time**
   - Don't put primary buttons in both header and footer
   - Secondary in header + primary in footer is OK

3. **Only add to narrow containers**
   - Don't add to wide containers (> 400-500px)
   - Not for full page modals on desktop

4. **Don't use with text entry**
   - iOS keyboard covers footer

---

## Modals

### Types
- **Blade**: Adapts to full modal in compact size
- **Partial**: Adapts to full modal in compact size
- **Popover**: Adapts to sheet in compact size
- **Sheet**: Adapts from inset to full-bleed in compact

### Adaptive Behavior
Modals automatically adapt based on breakpoint (web) or size class (native).

All modals inherit padding from viewport size class.

---

## Scanning

### Icons
Use generic scan icon when device supports both barcode and QR code (like T3).

Available icons:
- Scan (generic)
- Scan barcode
- Scan QR code
- QR code
- Scan human
- Scan text
- Scan document
- Scan x / Scan check
- Handheld scanner

### Methods

| Method | Description |
|--------|-------------|
| **Barcode scanner** | Laser technology, integrated or separate device |
| **Camera scanner** | Uses device camera, native or custom UI |

### Common Flows
- Search (find item by barcode)
- Data collection (add SKU to item)
- Adding to group (item to cart)
- Payment (scan gift card)
- Cross-device (QR to continue on phone)

### Barcode vs Camera

**Barcode scanners:**
- Initiated by physical button
- Should have default action per screen
- No UI needed to initiate

**Camera scanners:**
- Require CTA to open camera
- Use scan icon as trailing accessory in fields
- Components supporting scan icon: Text field, Label-less text field, Card field, Search field

### After Scan
- Provide immediate feedback (haptic, sound, visual)
- Animate item into cart or show toast/dialog

### T3 Tips
- Supports barcode and QR code
- Use generic scan icon
- Encourage barcode over camera (faster)
- Green bar appears when scanning active

---

## Progress Tracking

### Types

| Type | Description |
|------|-------------|
| **System progress** | Status from organization (e.g., shipped) |
| **User progress** | User's position in sequence |

### Increments

| Type | Description |
|------|-------------|
| **Fixed** | Set number of steps |
| **Fluid** | Estimated location (can confuse users) |

### Best Practices
- Use descriptive labels for each step (especially > 3 steps)
- Consider breaking fluid progress into fixed stages
- Progress trackers ≠ loading indicators

---

## AI Features

### Labeling AI-Powered Features
Place Square AI label at entry point, before user engages.

**Two label options:**
- **Square AI icon**: For buttons (leading position)
- **Square AI pill**: For rows, popovers, non-button components

### Placement
If multiple pills, AI pill appears first.

### Mixed Experiences
Use **inline status** to indicate after the fact when AI was used:
- "Suggested by Square AI"
- "Order placed by Square AI"

### Disclaimers
Always get legal approval for disclaimer language.

### Non-AI Insights
Use `info` variant of Banner for general suggestions (not AI-specific).

> **Note**: Insight components are deprecated (removed Nov 1, 2025). Use Banner `info` variant instead.

---

## Dashboard Navigation Guidelines

### L1 (Top Level) Navigation
Owned by Dashboard design team. Does not change frequently.

**Principles:**
- Represent broad capabilities of Square ecosystem
- Mutually exclusive from each other
- Avoid compound labels (no "and" / "&")
- Match sellers' mental models

### L2-L4 Navigation
Co-owned by partner teams and Dashboard OS team.

**Guidelines:**
- Integrate into existing structures before adding pages
- One canonical home (no duplication)
- Manageable lists (5-10 items)
- Use nouns/noun phrases (plural)
- Use sentence case
- Avoid Square-specific names when possible
