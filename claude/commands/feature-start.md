# Feature Start: Branch + Context + Plan

**Execute this workflow immediately.**

## Arguments

The command accepts: `$ARGUMENTS`

Format: `<description>` - A short description of the feature

Examples:
- `/feature-start add empty state to spaces`
- `/feature-start improve space card hover states`
- `/feature-start figma integration`

## Step 1: Create Branch

1. **Check git status** to see current branch
2. **If not on main**: Switch to main with `git checkout main`
3. **Pull latest**: Run `git pull origin main`
4. **Create branch**:
   - Read user's branch prefix from `~/.claude/branch-config.json`
   - Convert description to kebab-case
   - Create branch: `{branchPrefix}/{kebab-case-description}`
   - Run: `git checkout -b <branch-name>`

## Step 2: Understand the Feature

Ask the user clarifying questions to understand the feature:

1. **What is this feature?** Get a 1-2 sentence description of what we're building
2. **Where does it fit?** Which page/component/feature area will this affect?
3. **User interaction?** How will users interact with this feature?
4. **Any design reference?** Ask if there's a Figma link, screenshot, or existing pattern to follow

Keep questions brief - aim for 3-4 max. If the user's initial description is clear, skip obvious questions.

## Step 3: Gather Context

Based on the feature description, **proactively** search the codebase for relevant files:

1. **Find the target area**: Use glob/grep to locate the files we'll likely modify
   - For UI features: Look in `web/src/features/` and `web/src/routes/`
   - For components: Check `web/src/shared/components/`
   - Read the main files that will need changes

2. **Check existing patterns**: Search for similar features or components
   - If adding an empty state, find other empty states in the codebase
   - If adding a dialog, find existing dialog implementations
   - Note patterns to follow (component structure, naming, etc.)

3. **Review design system**: Identify which shadcn/ui components we should use
   - List available components from `web/src/shared/components/ui/`
   - Check `web/src/shared/components/patterns/` for reusable patterns
   - Note if we should create new variants or use existing ones

## Step 4: Create Implementation Plan

Present a clear, actionable plan:

### Files to Modify
List each file that needs changes with a brief explanation:
- `path/to/file.tsx` - What changes are needed here

### Files to Create (if needed)
List any new files with their purpose:
- `path/to/new/file.tsx` - What this file will contain

### Design System Components
List which shadcn/ui components we'll use:
- `Button` - For CTA actions
- `Card` - For layout structure
- etc.

### Implementation Steps
Number the steps in logical order:
1. [First thing to do]
2. [Second thing to do]
3. [Final step]

### Potential Challenges
Note any tricky parts or decisions needed:
- Should we add this to shared patterns?
- How does this work with existing state?
- Any animation/interaction concerns?

## Step 5: Confirm and Begin

Ask: **"Does this plan look good? Any changes before I start implementing?"**

Wait for user confirmation before proceeding. If approved, begin implementing Step 1 from the plan.

## Step 6: After Implementation - Testing

Once implementation is complete:

1. **Run linter** to check for any errors: `ReadLints` on modified files
2. **Fix any linter errors** if present
3. **Ask about testing**: Present these options to the user:
   - "Would you like to test the changes yourself, or should I open the browser to verify the implementation?"
   - If they want to test themselves: Confirm dev server is running and summarize what to test
   - If they want me to test: Use browser MCP tools to navigate and verify the changes


