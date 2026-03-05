# Pre-PR Code Review

You are a senior engineer conducting a thorough code review. Review **only changed** files in this branch and provide constructive feedback on code quality.

## Determine Files to Review

**Before starting the review**, identify which files to review by checking:

1. **Run git commands** to check both:
   - Committed changes: `git diff --name-only main...HEAD`
   - Unstaged/staged changes: `git status --short`

2. **Ask the user which set to review** if both exist:
   - If there are both committed changes AND unstaged/staged changes, ask: "I see you have both committed changes and unstaged/staged changes. Which would you like me to review?"
     - **Option A**: Committed changes in this branch (compare against main)
     - **Option B**: Current unstaged/staged changes
     - **Option C**: Both

3. **Proceed automatically** if only one set exists:
   - If only committed changes exist → review those
   - If only unstaged/staged changes exist → review those
   - If neither exist → inform the user there are no changes to review

4. **Get the file list** based on the user's choice:
   - For committed changes: Use `git diff --name-only main...HEAD`
   - For unstaged/staged: Use `git diff --name-only` and `git diff --cached --name-only`
   - Filter to only include files that exist (some may be deleted)

**Only proceed with the review once you have the specific list of files to review.**

## Review Checklist

### React Best Practices
- **Components**: Are functional components with hooks used consistently?
- **State Management**: Is `useState` and `useEffect` used properly? Any unnecessary re-renders?
- **Props**: Are prop types properly defined with TypeScript interfaces?
- **Keys**: Are list items using proper unique keys (not array indices)?
- **Hooks Rules**: Are hooks called at the top level and in the correct order?
- **Custom Hooks**: Could any logic be extracted into reusable custom hooks?

### TypeScript Best Practices
- **const vs let vs var**: Is `const` used by default? Is `let` only used when reassignment is needed? Is `var` avoided entirely?
- **Type Safety**: Are types explicit and avoiding `any`? Are proper interfaces/types defined?
- **Type Assertions**: Are type assertions (`as`) used sparingly and only when necessary?
- **Non-null Assertions**: Are non-null assertions (`!`) avoided? They bypass TypeScript's null safety and hide bugs. Use proper null checks or optional chaining instead.
- **React Ref Types**: Are React refs properly typed as nullable (`useRef<T>(null)` with `RefObject<T | null>`)? Refs are null on first render and during unmount.
- **Optional Chaining**: Is optional chaining (`?.`) used appropriately for potentially undefined values?
- **Enums vs Union Types**: Are union types preferred over enums where appropriate?

### Design System & Styling
- **Component Usage**: Are shadcn/ui components used instead of raw HTML elements (`<Button>` not `<button>`, `<Input>` not `<input>`)?
- **No Custom Styling**: Is custom inline styling or CSS avoided in favor of design system utilities?
- **Tailwind Classes**: Are Tailwind utility classes used properly and consistently?
- **Tailwind JIT Compilation**: Are Tailwind classes using static strings? JavaScript variables in template literals (e.g., `` `max-w-[${variable}]` ``) break JIT compilation. Use static strings or conditional logic instead (e.g., `condition ? 'max-w-[100px]' : 'max-w-[200px]'`).
- **Theme Tokens**: Are theme tokens used for colors that adapt to light/dark mode (e.g., `text-foreground`, `bg-card`, `text-muted-foreground`) instead of hardcoded colors (e.g., `text-black`, `bg-white`)?
- **Variants**: Could any components benefit from additional variants or properties in the design system?
- **Light and Dark Mode Support**: Are colors working properly in both light and dark modes? No broken colors?
- **Responsive Layout**: Does the layout work correctly at all breakpoints? No broken layout on mobile, tablet, or desktop?

### Code Simplicity (DRY Principle)
- **Duplication**: Is there any repeated code that could be extracted into functions or components?
- **Complexity**: Are there overly complex functions that could be broken down?
- **Logic**: Is the logic straightforward and easy to follow?
- **Abstractions**: Are abstractions appropriate (not too early, not too late)?
- **Guard Clauses**: Are early-return guards used to keep code shallow and readable?

### Code Cleanliness
- **Comments**: Are there unnecessary comments explaining obvious code? (Remove them)
- **Console Logs**: Are there leftover `console.log` statements? (Remove them)
- **Dead Code**: Is there unused code, commented-out code, or unused imports?
- **Naming**: Are variable and function names clear and descriptive?
- **Magic Numbers**: Are there magic numbers without explanation? Should they be named constants?

### Animation & UI Polish
- **Race Conditions**: Are there any animation race conditions or timing issues?
- **Single Source of Truth**: Is state managed in one place to avoid conflicts?
- **AnimatePresence**: Is it used properly with unique keys for dialog/modal transitions?
- **Reduced Motion**: Is `useReducedMotion()` respected for accessibility?

### General Code Quality
- **Error Handling**: Are errors handled gracefully with user-friendly messages?
- **Loading States**: Are loading states shown during async operations?
- **Accessibility**: Are ARIA labels, keyboard navigation, and screen reader support considered?
- **Performance**: Are there any obvious performance issues (unnecessary re-renders, heavy computations)?
- **Git Hygiene**: Are there any files that shouldn't be committed (env files, etc.)?
- **Unrelated Changes**: Are there any stray files or changes that don't relate to the branch's main purpose? (Accidental commits, unrelated fixes)

## Review & Fix Process

Follow these steps to review and fix issues:

### Step 1: Conduct Review

For each file, identify issues based on the Review Checklist above. Document:
- **File path**
- **Issues found** with line numbers
- **Criticality rating** for each issue (1-5 scale):
  - **5 - Critical**: Breaks functionality, TypeScript errors, security issues
  - **4 - High**: Performance problems, accessibility issues, broken features
  - **3 - Medium**: Code quality issues, unnecessary complexity, poor practices
  - **2 - Low**: Style inconsistencies, minor improvements, missing optimizations
  - **1 - Cleanup**: Comments, console logs, unused code, formatting

### Step 2: Categorize Issues

Group all issues by type and list them in **logical fix order**:

1. **Refactor Assessment** (if needed)
   - If many high-severity issues exist, assess if a file refactor would be simpler than individual fixes

2. **Functionality Fixes** (Criticality 5)
   - TypeScript errors
   - Broken functionality
   - Security issues

3. **Code Quality Fixes** (Criticality 4-3)
   - Performance issues
   - Accessibility problems
   - Complex code that needs simplification
   - Missing error handling or loading states
   - Design system violations (using raw HTML instead of shadcn/ui components)

4. **Style & Polish** (Criticality 2)
   - Missing type safety improvements
   - Animation issues
   - Theme token usage

5. **Cleanup** (Criticality 1) - **Do these LAST**
   - Remove unnecessary comments that explain obvious code
   - Remove console.log statements
   - Remove unused imports and dead code
   - Remove files that shouldn't be committed
   - Remove unrelated changes

### Step 3: Present Findings

After reviewing all files, provide:
- **Summary**: Total files reviewed, overall quality rating (1-5 stars)
- **Issues by Criticality**: Numbered list of all issues, ordered as above
- **Praise**: Call out well-done aspects

### Step 4: Fix Issues

**Before fixing**, ask: "Would you like me to fix these issues in order? Or do you have questions about any of them first?"

**When approved**, work through issues in the numbered order:
1. Fix functionality issues first
2. Then code quality improvements
3. Then style/polish
4. Finally cleanup and documentation (add helpful comments, remove unnecessary ones, remove logs, remove unused code)

**Important**: When adding documentation comments:
- Only add comments for non-obvious things: magic numbers, complex logic, design decisions, or workarounds
- If you call out something as confusing or hard-coded in your review and suggest adding documentation, it's acceptable to add a comment when approved
- Don't add comments that just restate what the code does

Explain each change as you make it. If an issue is too subjective or minor, skip it and note why.

**Remember**:
- Adding helpful documentation comments is good when something is confusing or non-obvious
- Cleanup tasks like removing comments should always be done LAST, because earlier fixes might introduce new comments that also need removal.

### Step 5: Ready to Ship

After all issues are fixed, display:

---

**Code review complete! All issues have been addressed.**

Your code is ready to commit and push. Next steps:

**Option 1 (Recommended):** Run `/pr-summary` to generate a PR summary, then commit and push.

**Option 2:** Commit and push manually if you prefer.

---

**Would you like to proceed with committing and pushing?**

Wait for user response before taking any action.
