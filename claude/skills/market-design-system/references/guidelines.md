# Market Design System - Design Guidelines

## Core Design Principles

### 1. 8px Base Grid
All spacing derives from `--core-base-size: 8px`. Use spacing tokens, not arbitrary values.

### 2. Semantic Tokens First
Use semantic tokens (critical, success, warning, emphasis) over raw color values. This ensures consistency and theme support.

### 3. Theme Aware
All colors support light/dark mode automatically via CSS variables. Never hardcode colors.

### 4. Accessibility First
- Components include ARIA patterns
- Focus management built-in
- Keyboard navigation supported
- Don't rely on color alone

---

## Content & Communication Principles

### Error Messages
✅ **Be clear** - Plain language, no jargon
✅ **Be actionable** - Provide next steps
✅ **Show empathy** - Support, don't blame

### Status Communication
- Use appropriate component for context (inline vs global)
- Match urgency to visual treatment
- Provide clear next steps

### Loading States
- < 2s: No indicator needed
- 2-10s: Show progress
- 10s+: Explain what's happening, show progress, allow cancel

---

## Dashboard Navigation Principles

### Create Quality Structures
- Clear, consistent labels
- Strong, scannable page titles and headings
- No duplicate content—use contextual paths

### Group Things Logically
- Keep related items together
- Balance menu breadth and depth
- Form distinct groups with clear boundaries

### Help Users Navigate with Confidence
- Users always know where they are
- Clear paths to where they can go
- Easy way to return
- Support both browsing and searching

### Design for How Sellers Think
- Match sellers' mental models
- Use their language, not internal jargon
- Consider real-world context
- Anticipate questions

### Prioritize Foundational Solutions
- Design flexible frameworks
- Focus on long-term impact
- Avoid quick fixes creating tech debt

---

## Component Usage Guidelines

### Buttons
- One primary button per view
- Use destructive variant for dangerous actions
- Keep buttons active (don't disable for validation)
- Show loading state when action is processing

### Forms
- Label all fields clearly
- Mark required fields
- Show errors inline, close to the issue
- Provide helper text for complex fields
- Use forgiving input formats

### Modals
- Use sparingly—prefer inline solutions
- Match modal type to content importance
- Provide clear exit path
- Don't nest modals

### Navigation
- L1: Broad capabilities (rarely changes)
- L2-L4: Specific features (integrate before adding)
- One canonical location per feature
- 5-10 items per list

---

## Accessibility Guidelines

### General
- Each error must be announced by screen readers
- Focus moves to error summary on validation failure
- Messages linked to relevant fields
- Don't rely on color alone

### Disabled States
- Disabled elements are not interactive
- Don't put tooltips on disabled elements
- Screen readers skip disabled content
- Consider hiding vs disabling

### Focus States
- Use `--core-focus-ring-*` tokens
- Ensure all interactive elements are keyboard accessible
- Maintain visible focus indicators

### Loading
- Announce loading states to screen readers
- Provide text alternatives for visual progress
- Allow pausing/stopping animations

---

## Visual Design Guidelines

### Typography
- Use Square Sans font family
- Maintain text hierarchy with text-10, text-20, text-30
- Ensure sufficient contrast

### Color Usage
- Semantic colors for status (critical, success, warning)
- Fill colors for backgrounds
- Text colors for content
- Surface colors for containers

### Spacing
- Use spacing tokens exclusively
- Maintain consistent rhythm
- Respect the 8px grid

### Animation
- Use enter/exit/move transition tokens
- Match duration to importance
- Respect reduced motion preferences

---

## Pattern-Specific Guidelines

### Filtering
- Display applied filters visibly
- Allow combining options within categories
- Use AND between categories, OR within
- Truncate long lists (> 8 items)
- Provide search for very long lists (> 15 items)

### Selection
- Checkbox: Multiple independent options
- Radio: Mutually exclusive, one required
- Toggle: Immediate on/off effect
- Segmented control: View switching, immediate

### Scanning
- Use generic scan icon when device supports multiple types
- Barcode scanning: No UI needed to initiate
- Camera scanning: Requires CTA to open
- Always provide immediate feedback after scan

### Progress
- Use fixed steps over fluid when possible
- Label all steps (especially > 3)
- Distinguish progress trackers from loading indicators

### AI Features
- Label AI features at entry point
- Use Square AI icon (buttons) or pill (other components)
- Include legal-approved disclaimers
- Use inline status for after-the-fact AI attribution

---

## Anti-Patterns to Avoid

### Don't
- ❌ Disable buttons for form validation
- ❌ Put tooltips on disabled elements
- ❌ Use compound L1 navigation labels
- ❌ Duplicate content across navigation
- ❌ Rely on color alone for status
- ❌ Use fluid progress without clear stages
- ❌ Show loading for < 2 second operations
- ❌ Use positional language in errors ("below", "above")
- ❌ Hardcode color values
- ❌ Use arbitrary spacing values

### Do
- ✅ Keep buttons active, show errors on submit
- ✅ Use inline status to explain disabled states
- ✅ Use clear, single-word navigation labels
- ✅ One canonical location per feature
- ✅ Combine color with icons/text for status
- ✅ Break progress into fixed stages
- ✅ Match loading treatment to duration
- ✅ Write device-agnostic error messages
- ✅ Use semantic color tokens
- ✅ Use spacing scale tokens
