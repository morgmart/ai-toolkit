Analyze the current branch and generate a PR summary for designer-to-engineer review.

## Instructions

1. Run `git log main..HEAD --oneline` (or the appropriate base branch) to understand the commits on this branch.
2. Run `git diff main..HEAD --stat` to get the list of changed files.
3. Run `git diff main..HEAD` to understand what changed in each file.
4. Generate a PR summary with these three sections:

### Section 1: Overview
A brief paragraph explaining the intent of the PR — what it aims to accomplish from a design perspective. Keep it to 2-3 sentences max. No fluff.

### Section 2: Changes
List every changed file. For each file, use the filename as a bold header, then underneath write one or two sentences about what was changed and why. Focus on intent, not implementation details.

### Section 3: Reproduction Steps
Numbered steps in plain English for how an engineer can see the outcome of this PR. Assume they know how to run the project. Focus on where to look and what they should see.

## Output format

Output the summary as a single fenced Markdown code block (```markdown ... ```) so the user can copy it directly into a GitHub PR description. Do NOT create any files. Do NOT output formatted text outside the code block.

## Tone

Write from the perspective of a product designer explaining their thinking to engineers. Be clear and concise — just enough to establish intent. They can read the code; your job is to guide their understanding of the "why."
