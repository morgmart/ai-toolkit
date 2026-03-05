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

## Deploying to a New Project

To activate these rules in any project, copy the `ai-rules/` source directory into that project and regenerate:

```bash
cp -r ~/Development/ai-toolkit/ai-rules /path/to/your-project/ai-rules
cd /path/to/your-project
sq ai-rules generate
```

This creates tool-specific files (`CLAUDE.md`, `AGENTS.md`, `.cursor/rules/`, etc.) in that project directory.

For Claude Code global context (applies across all projects), `~/.claude/CLAUDE.md` is symlinked to `~/Development/ai-toolkit/CLAUDE.md`. Any changes here take effect immediately.

## Adding a New Rule (Cross-Tool)

1. Create `ai-rules/<rule-name>.md` with YAML frontmatter (`description`, `alwaysApply`)
2. Run `sq ai-rules generate` from `~/Development/ai-toolkit/`
3. Commit and push

## Adding a New Claude Skill

1. Create `claude/skills/<skill-name>/SKILL.md`
2. Symlink it: `ln -s ~/Development/ai-toolkit/claude/skills/<skill-name> ~/.claude/skills/<skill-name>`
3. Commit and push

## Git Workflow

- Commit messages should be clear and descriptive
- Run `sq ai-rules generate` before committing whenever `ai-rules/*.md` files change
