# Code Agents

A comprehensive collection of Claude Code components for enhancing development workflows with AI-powered assistance.

## Overview

This repository provides a complete framework for creating and organizing Claude Code components including context files, snippets, slash commands, and agent definitions. These components work together to provide domain-specific guidance, automated quality checks, and specialized workflows for software development.

## Components

### 📁 Context Files (`/context/`)
Comprehensive reference materials and checklists for specific technologies and domains:

- **`design-principles.md`** - S-Tier SaaS dashboard design standards inspired by Stripe, Airbnb, and Linear
- **`nextjs-clean-code.md`** - Next.js development best practices and patterns  
- **`style-guide.md`** - Brand and visual consistency guidelines

### 📝 Snippets (`/snippets/`)
Quick-reference snippets for immediate guidance in `CLAUDE.md`:

- **`design-review-claude-md-snippet.md`** - Design review integration snippet
- **`nextjs-clean-code-snippet.md`** - Next.js quality check snippet

### ⚡ Slash Commands (`/commands/`)
Specialized workflow commands for complex analysis tasks:

- **`design-review-slash-command.md`** - Comprehensive design review automation
- **`nextjs-clean-code-slash-command.md`** - Next.js code quality analysis

### 🤖 Agents (`/agents/`)
Agent definitions for autonomous multi-step workflows:

- **`design-review.md`** - Design review agent specification

## File Structure

```
code-agents/
├── README.md                                    # This file
├── CLAUDE.md                                   # Main guide and component documentation
├── context/                                    # Detailed reference materials
│   ├── design-principles.md                   # Design standards checklist
│   ├── nextjs-clean-code.md                  # Next.js best practices
│   └── style-guide.md                        # Brand guidelines
├── snippets/                                   # CLAUDE.md integration snippets
│   ├── design-review-claude-md-snippet.md    # Design review snippet
│   └── nextjs-clean-code-snippet.md          # Next.js quality snippet
├── commands/                                   # Slash command definitions
│   ├── design-review-slash-command.md        # Design analysis command
│   └── nextjs-clean-code-slash-command.md    # Code quality command
└── agents/                                     # Agent specifications
    └── design-review.md                       # Design review agent
```

## Getting Started

### 1. Integration with Claude Code

Copy the relevant components to your project:

```bash
# Copy main guide to your project
cp CLAUDE.md /path/to/your/project/

# Copy context files you need
cp -r context/ /path/to/your/project/

# Copy commands to Claude Code directory (if using Claude Code)
cp commands/*.md /path/to/your/project/.claude/commands/
```

### 2. Customization

1. **Update `CLAUDE.md`** with your project-specific snippets
2. **Modify context files** to match your technology stack and standards
3. **Customize slash commands** for your specific workflows
4. **Adapt agent definitions** for your project's needs

### 3. Usage Workflow

1. **Development**: Claude references snippets during coding
2. **Quick checks**: Snippets trigger immediate quality validations  
3. **Detailed review**: Slash commands analyze complete changes
4. **Complex analysis**: Agents handle multi-step investigations
5. **Reference**: Context files provide comprehensive guidelines

## Component Types

### Context Files
- **Purpose**: Comprehensive checklists and detailed guidelines
- **Format**: Markdown with checkbox-based structure
- **Usage**: Referenced by snippets, commands, and agents

### Snippets  
- **Purpose**: Immediate actions and quick quality checks
- **Format**: Markdown sections for `CLAUDE.md`
- **Usage**: Automatically loaded into Claude's context

### Slash Commands
- **Purpose**: Git-aware analysis and specialized workflows
- **Format**: Markdown with frontmatter for tool permissions
- **Usage**: Invoked with `/command-name` in Claude Code

### Agents
- **Purpose**: Autonomous multi-step complex workflows
- **Format**: Task tool prompts with specific instructions
- **Usage**: Created via `Task()` function calls

## Best Practices

### Organization
- Keep context files comprehensive but well-structured
- Make snippets actionable with specific commands
- Design commands to work with git diffs
- Provide detailed, specific prompts for agents

### Maintenance
- Regularly update context files with new best practices
- Keep snippets concise and focused on immediate actions  
- Test slash commands with real git diffs
- Refine agent prompts based on output quality

### Naming Conventions
- **Context**: `technology-domain.md`
- **Commands**: `action-domain.md`  
- **Snippets**: Include in `CLAUDE.md` or separate files
- **Agents**: Descriptive names matching their purpose

## Contributing

1. Follow the established file structure and naming conventions
2. Ensure all components reference each other appropriately
3. Test components with real development workflows
4. Update documentation when adding new components

## License

This project is provided as-is for educational and development purposes.