---
name: rebase
description: Clean rebase onto main with interactive conflict resolution
disable-model-invocation: false
---

# Clean Rebase with Smart Conflict Resolution

Perform a clean rebase of the current branch onto main, handling conflicts intelligently.

## Process Overview

1. **Verify State**: Check current branch and git status
2. **Update Main**: Fetch and pull latest main
3. **Attempt Rebase**: Rebase current branch onto main
4. **Handle Conflicts**: If conflicts occur, walk through each one with analysis and recommendations
5. **Complete**: Force push with lease to update the PR

## Step-by-Step Instructions

### Step 1: Check Current State

First, verify the current branch and ensure working directory is clean:

```bash
git status
git branch --show-current
```

If there are uncommitted changes, ask the user if they want to:
- Commit them first
- Stash them
- Abort the rebase

### Step 2: Update Main Branch

Switch to main and pull latest changes:

```bash
git checkout main
git pull origin main
```

Store the original branch name for later.

### Step 3: Attempt Rebase

Switch back to the feature branch and start the rebase:

```bash
git checkout <original-branch>
git rebase main
```

### Step 4: Handle Conflicts

If the rebase encounters conflicts, the output will show which files have conflicts.

For EACH conflicted file:

1. **Read the conflict markers** to understand what's conflicting
2. **Show the user**:
   - File path and line numbers
   - The conflicting sections with context
   - What changed in main (<<<<<<< HEAD to =======)
   - What changed in their branch (======= to >>>>>>> branch-name)

3. **Analyze the conflict** by:
   - Reading surrounding code context
   - Understanding the intent of both changes
   - Checking if changes are complementary or contradictory

4. **Provide recommendation** with reasoning:
   - **"Accept main"**: If main's changes supersede branch changes (e.g., refactor, better implementation)
   - **"Accept yours (HEAD)"**: If branch changes are the intended feature/fix
   - **"Keep both"**: If changes are complementary and can coexist
   - **"Manual merge needed"**: If complex logic requires custom resolution

5. **Ask user to choose**: Present options clearly:
   - Option 1: Accept main's version
   - Option 2: Accept your version (HEAD)
   - Option 3: Keep both changes
   - Option 4: Let me manually resolve (show how to edit the file)

6. **Apply the resolution**:
   - If "Accept main": `git checkout --theirs <file>`
   - If "Accept yours": `git checkout --ours <file>`
   - If "Keep both": Help edit the file to include both
   - If "Manual": Provide clear instructions for editing

7. **Mark as resolved**: `git add <file>`

### Step 5: Continue Rebase

After all conflicts are resolved:

```bash
git rebase --continue
```

Repeat conflict resolution if more conflicts appear in subsequent commits.

### Step 6: Verify and Push

Once rebase is complete:

1. Show the commit log to verify:
   ```bash
   git log --oneline main..HEAD
   ```

2. Ask user to confirm the commits look correct

3. Force push with lease to update remote:
   ```bash
   git push --force-with-lease origin <branch-name>
   ```

4. Confirm the PR on GitHub shows only their changes

## Conflict Analysis Guidelines

When analyzing conflicts, consider:

- **File type**: Is this config, code, tests, or documentation?
- **Change nature**: Refactor, new feature, bug fix, or formatting?
- **Scope**: Does main's change affect the same feature?
- **Dependencies**: Does the branch depend on code that main modified?

## Common Conflict Patterns

- **Import/dependency conflicts**: Usually accept main (they may have updated dependencies)
- **Feature additions**: Usually keep both (merge the features)
- **Refactors**: Usually accept main (they restructured for a reason)
- **Configuration**: Carefully review - may need both merged
- **Tests**: Keep both test cases unless they're testing the same thing

## Error Recovery

If something goes wrong:

- To abort the rebase: `git rebase --abort`
- To skip a problematic commit: `git rebase --skip` (use cautiously)
- To edit a commit during rebase: Follow the rebase-todo instructions

## Arguments

Optional: `$ARGUMENTS` can be a target branch (defaults to main)

Example: `/rebase develop` to rebase onto develop instead of main
