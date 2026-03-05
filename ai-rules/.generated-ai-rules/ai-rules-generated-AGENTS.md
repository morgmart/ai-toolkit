# Base repository guidelines

# Repository Guidelines

This repository is an AI toolkit containing Claude AI skills and commands designed to streamline development workflows. It provides reusable patterns for common development tasks like code review, PR summaries, git rebasing, tech stack explanations, and feature development workflows.

## Project Structure & Module Organization

The repository is organized into two main areas:

- `claude/skills/` - Reusable AI skills that can be invoked as commands
  - `rebase/SKILL.md` - Interactive git rebase workflow with conflict resolution
  - `tech-stack/SKILL.md` - Tech stack explainer for product designers
  - `market-design-system/SKILL.md` - Design system guidelines and references
- `claude/commands/` - Command templates for specific workflows
  - `pr-summary.md` - Generate PR summaries for designer-to-engineer review
  - `code-review.md` - Pre-PR code review checklist and process
  - `feature-start.md` - Branch creation, context gathering, and implementation planning

## File Format & Structure

All skills and commands follow a consistent Markdown format:

**Skills** (`SKILL.md` files):
- Include YAML frontmatter with `name`, `description`, and `disable-model-invocation` fields
- Contain detailed step-by-step instructions for AI agents to follow
- May accept `$ARGUMENTS` for parameterization

**Commands** (`.md` files):
- Plain Markdown without frontmatter
- Provide instructions for specific one-off tasks
- Focus on output format and tone

## Content Guidelines

When creating or modifying skills and commands:

1. **Be explicit and procedural** - Write clear step-by-step instructions that AI agents can follow deterministically
2. **Include examples** - Show concrete examples of commands, outputs, and expected formats
3. **Define decision points** - When choices are needed, provide clear criteria for making decisions
4. **Specify output format** - Be explicit about how results should be presented to users
5. **Consider user interaction** - Include prompts for user confirmation at key decision points

## Naming Conventions

- Skills use kebab-case directory names with `SKILL.md` inside: `rebase/SKILL.md`
- Commands use kebab-case filenames: `pr-summary.md`, `code-review.md`
- Reference files use descriptive names: `guidelines.md`, `patterns.md`, `tokens.md`

## Design Philosophy

This toolkit is designed for:

- **Product designers** working with code who need plain-language explanations
- **Development workflows** that benefit from AI assistance (reviews, summaries, rebasing)
- **Consistency** across projects through reusable patterns
- **Interactive guidance** rather than fully automated execution

Skills should guide the AI agent through complex workflows while keeping the human in the loop for key decisions.

## Adding New Skills or Commands

When adding new content:

1. Determine if it's a reusable skill (goes in `claude/skills/`) or a one-off command (goes in `claude/commands/`)
2. Follow the existing format patterns (YAML frontmatter for skills, plain Markdown for commands)
3. Include clear instructions, examples, and expected outputs
4. Test the workflow to ensure instructions are complete and unambiguous
5. Consider edge cases and error recovery paths

## Git Workflow

Based on repository history:
- Commit messages should be clear and descriptive
- Initial commit pattern: "Initial commit: [description of contents]"
- TODO: Verify commit conventions as more history accumulates

# Rules

**CRITICAL DIRECTIVE**: You MUST evaluate EVERY optional rule below for potential relevance to the current task. These are NOT suggestions - they are specialized rules that MUST be loaded when their domain matches the user's request. Scan the user's input for keywords and immediately load ALL applicable rules. 
**IMPORTANT**: YOU MUST READ the rule as soon as they are relevant. YOU MUST DO THIS BEFORE ANYTHING ELSE. 
**IMPORTANT**: Before looking for solutions in the codebase YOU MUST READ the rule.

**LOADING PROTOCOL**: 
- If a rule description mentions a topic/tool/framework AND the user's request involves that topic/tool/framework → YOU MUST READ THE RULE
- If a rule title contains keywords from the user's request → YOU MUST READ THE RULE
- Multiple rules can and should be loaded simultaneously when applicable
- "Optional" means conditionally mandatory, NOT ignorable

**EXAMPLE**: 
- If a rule mentions "database migrations" and the user asks about "updating database schema" → YOU MUST READ that rule
- If a rule mentions "authentication" and the user mentions "login", "auth", or "security" → YOU MUST READ that rule
- If multiple rules could apply to the task → YOU MUST READ ALL relevant rules

**REMEMBER**: These rules contain critical domain-specific expertise. Failing to load a relevant rule means missing essential guidance that could prevent errors or provide required patterns. When in doubt, load the rule.

**HOW TO LOAD RULES**: Each rule below is listed with its description followed by a colon and the file path. When a rule's description matches your task, YOU MUST READ THE FILE at the specified path using the provided reference. The file contains the actual rule content that you need.

**RULE FORMAT**: 
`[Rule Description]: [File Path]`

When you identify a relevant rule based on its description, immediately read the file at the specified path. The descriptions are activation triggers - the actual guidance is in the referenced files.

Explain frontend/fullstack tech stack concepts to a product designer using plain language and design analogies (Figma, components, tokens, etc.): ai-rules/.generated-ai-rules/ai-rules-generated-tech-stack.md


