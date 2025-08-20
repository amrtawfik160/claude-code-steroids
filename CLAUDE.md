# Claude Code Components Guide

A comprehensive guide to creating context files, agents, snippets, and commands for Claude Code.

## Table of Contents

1. [Context Files](#context-files)
2. [CLAUDE.md Snippets](#claudemd-snippets)
3. [Slash Commands](#slash-commands)
4. [Agents (via Task Tool)](#agents-via-task-tool)
5. [File Structure Best Practices](#file-structure-best-practices)
6. [Integration Examples](#integration-examples)

---

## Context Files

Context files provide domain-specific knowledge and guidelines that Claude can reference during development.

### Purpose
- Store comprehensive checklists and best practices
- Provide detailed guidelines for specific technologies or domains
- Serve as reference material for complex workflows

### Structure
```markdown
# Technology/Domain Name

## Section 1: Core Concepts
- [ ] Checklist item 1
- [ ] Checklist item 2

### Subsection
- [ ] Detailed implementation step
- [ ] Validation requirement

## Section 2: Best Practices
- [ ] Practice 1 with explanation
- [ ] Practice 2 with code example

## Section 3: Common Patterns
### Pattern Name
- [ ] Implementation step
- [ ] Testing requirement
```

### Example: Next.js Clean Code Context
```markdown
# Next.js Clean Code Best Practices

## TypeScript & Type Safety
- [ ] Enable strict TypeScript configuration settings
- [ ] Avoid using `any` type - use `unknown` or proper type definitions
- [ ] Implement proper generic types for reusable components

## Component Architecture
- [ ] Follow container-presentational pattern
- [ ] Implement single responsibility principle
- [ ] Use functional components with hooks
```

### File Location
- Store in `/context/` directory
- Use descriptive filenames: `nextjs-clean-code.md`, `design-principles.md`
- Keep separate from implementation files

---

## CLAUDE.md Snippets

Snippets provide immediate, actionable guidance that gets automatically loaded into Claude's context.

### Purpose
- Provide quick reference and immediate actions
- Enforce quality checks after code changes
- Guide Claude's workflow for specific domains

### Structure
```markdown
## Domain Name

### Standards & Guidelines
- Reference to comprehensive context file
- Brief description of when to use

### Quick Quality Check
IMMEDIATELY after implementing [specific changes]:
1. **Action 1** - Specific command or validation
2. **Action 2** - Another verification step
3. **Action 3** - Final check with expected outcome

This verification ensures [specific quality outcome].

### Comprehensive Review
Reference [context file] when:
- Starting new features
- Conducting code reviews
- [Other specific scenarios]
```

### Example: Next.js Snippet
```markdown
## Next.js Clean Code

### Clean Code Standards
- Comprehensive Next.js best practices in `/context/nextjs-clean-code.md`
- When working with Next.js projects, always refer to this file for guidance

### Quick Code Quality Check
IMMEDIATELY after implementing any Next.js feature:
1. **TypeScript validation** - Run `tsc --noEmit` to check type safety
2. **Linting check** - Run `npm run lint` to validate code standards
3. **Performance check** - Ensure proper use of Next.js optimizations

### Comprehensive Clean Code Review
Reference the full checklist in `/context/nextjs-clean-code.md` when:
- Starting new Next.js features
- Conducting code reviews
```

### Integration
- Add directly to project's `CLAUDE.md` file
- Multiple snippets can coexist in same file
- Reference context files for detailed guidance

---

## Slash Commands

Slash commands provide specialized workflows that can be invoked on-demand for complex tasks.

### Purpose
- Automate complex review processes
- Provide specialized analysis tools
- Create reusable workflows for common tasks

### Structure
```markdown
---
allowed-tools: Tool1, Tool2, Tool3
description: Brief description of what the command does
---

You are an expert [domain] specialist. You [specific role description].

GIT STATUS:
```
!`git status`
```

FILES MODIFIED:
```
!`git diff --name-only origin/HEAD...`
```

DIFF CONTENT:
```
!`git diff --merge-base origin/HEAD`
```

OBJECTIVE:
[Specific instructions for analysis/review]

## Analysis Areas:
1. **Area 1**
   - Specific check 1
   - Specific check 2

2. **Area 2**
   - Specific check 3
   - Specific check 4

[Final instructions for output format]
```

### Example: Next.js Clean Code Review
```markdown
---
allowed-tools: Grep, LS, Read, Edit, MultiEdit, Write, Bash, Glob
description: Review Next.js code for clean code compliance
---

You are an expert Next.js developer and clean code specialist.

GIT STATUS:
```
!`git status`
```

DIFF CONTENT:
```
!`git diff --merge-base origin/HEAD`
```

OBJECTIVE:
Conduct comprehensive Next.js clean code review based on `/context/nextjs-clean-code.md`.

## Review Areas:
1. **TypeScript & Type Safety**
   - Strict typing compliance
   - Proper interface definitions

2. **Component Architecture**
   - Single responsibility principle
   - Container-presentational patterns
```

### File Location
- Store as `.md` files in project root or `.claude/commands/` if using Claude Code
- Use descriptive names: `nextjs-review.md`, `design-review.md`

### Usage
- Invoke with `/command-name` in Claude Code
- Commands automatically receive git context
- Output should be formatted reports or actionable feedback

---

## Agents (via Task Tool)

Agents are specialized AI assistants created through the Task tool for complex, multi-step workflows.

### Purpose
- Handle complex analysis requiring multiple tools
- Perform autonomous research and implementation
- Provide specialized expertise for specific domains

### Creation
```javascript
// In Claude Code conversation
Task({
  subagent_type: "general-purpose", // or specific agent type
  description: "Brief task description",
  prompt: `You are an expert [domain] specialist.
  
  Your task: [Specific objective]
  
  Requirements:
  1. [Specific requirement]
  2. [Another requirement]
  
  Process:
  1. [Step 1 with specific tools to use]
  2. [Step 2 with expected outcomes]
  
  Return: [Specific format for results]`
});
```

### Example: Design Review Agent
```javascript
Task({
  subagent_type: "general-purpose",
  description: "Design review analysis",
  prompt: `You are an elite design review specialist.
  
  Analyze the current git diff for:
  1. Visual design compliance with /context/design-principles.md
  2. Accessibility standards (WCAG 2.1)
  3. Responsive design implementation
  4. Brand consistency with /context/style-guide.md
  
  Use browser tools to navigate and screenshot changed pages.
  
  Return: Comprehensive markdown report with specific recommendations.`
});
```

### Best Practices
- Provide specific, detailed prompts
- Include expected output format
- Reference relevant context files
- Specify which tools the agent should use

---

## File Structure Best Practices

### Recommended Directory Structure
```
project/
├── CLAUDE.md                    # Main Claude Code context with snippets
├── context/                     # Detailed reference materials
│   ├── nextjs-clean-code.md    # Technology-specific guidelines
│   ├── design-principles.md    # Design standards
│   └── security-standards.md   # Security requirements
├── .claude/                     # Claude Code specific files
│   └── commands/               # Slash commands (if using Claude Code)
│       ├── nextjs-review.md    # Technology reviews
│       └── design-review.md    # Design analysis
└── agents/                      # Component definitions
    ├── nextjs-snippet.md       # Snippet examples
    └── review-commands.md       # Command templates
```

### Naming Conventions
- **Context files**: `technology-domain.md` (e.g., `nextjs-clean-code.md`)
- **Snippets**: Include in `CLAUDE.md` or separate as `technology-snippet.md`
- **Commands**: `action-domain.md` (e.g., `review-nextjs.md`)
- **Agent definitions**: Descriptive names matching their purpose

### Content Organization
1. **Context Files**: Comprehensive, checkbox-based guidelines
2. **Snippets**: Immediate actions and quick references
3. **Commands**: Git-aware analysis and review workflows
4. **Agent Prompts**: Detailed, autonomous task specifications

---

## Integration Examples

### Full Integration Example: React Clean Code

#### 1. Context File (`context/react-clean-code.md`)
```markdown
# React Clean Code Standards

## Component Design
- [ ] Use functional components with hooks
- [ ] Implement single responsibility principle
- [ ] Separate container and presentational components

## Performance
- [ ] Use React.memo for expensive components
- [ ] Implement proper dependency arrays in useEffect
- [ ] Avoid inline object/function creation in props
```

#### 2. CLAUDE.md Snippet
```markdown
## React Clean Code

### Standards Reference
- Comprehensive guidelines in `/context/react-clean-code.md`

### Quick Quality Check
IMMEDIATELY after React changes:
1. **Component structure** - Verify single responsibility
2. **Performance** - Check memo usage and dependency arrays
3. **Testing** - Ensure proper test coverage

### Comprehensive Review
Use `/react-review` command for thorough analysis.
```

#### 3. Slash Command (`react-review.md`)
```markdown
---
allowed-tools: Grep, Read, Bash
description: Review React code for clean code compliance
---

You are a React expert conducting clean code review.

Review git diff against `/context/react-clean-code.md` standards.

Focus on:
1. Component architecture
2. Performance optimizations  
3. Hook usage patterns
```

#### 4. Agent Usage
```javascript
Task({
  subagent_type: "general-purpose",
  description: "React refactor analysis",
  prompt: `Analyze React components for refactoring opportunities.
  
  Use /context/react-clean-code.md as reference.
  Identify components violating clean code principles.
  Provide specific refactoring recommendations.`
});
```

### Usage Workflow
1. **Development**: Claude references snippets during coding
2. **Quick checks**: Snippets trigger immediate validations
3. **Detailed review**: Slash commands analyze complete changes
4. **Complex analysis**: Agents handle multi-step investigations
5. **Reference**: Context files provide comprehensive guidelines

---

## Best Practices Summary

### Do's
- ✅ Keep context files comprehensive but organized
- ✅ Make snippets actionable with specific commands
- ✅ Design commands to work with git diffs
- ✅ Provide detailed prompts for agents
- ✅ Reference context files from snippets/commands
- ✅ Use consistent naming conventions

### Don'ts
- ❌ Don't duplicate content across files
- ❌ Don't make snippets too verbose
- ❌ Don't create commands without clear objectives
- ❌ Don't forget to specify allowed tools for commands
- ❌ Don't make context files too abstract

### Maintenance
- Regularly update context files with new best practices
- Keep snippets concise and focused on immediate actions
- Test slash commands with real git diffs
- Refine agent prompts based on output quality
- Archive outdated components and update references

This guide provides the foundation for creating effective Claude Code components that enhance development workflows and maintain code quality standards.