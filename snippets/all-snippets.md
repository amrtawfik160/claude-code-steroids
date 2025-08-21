## Website Copywriting Best Practices

### Standards Reference
- Comprehensive website copywriting best practices in `/context/copywriting-best-practices.md`
- Use when working on any website content, marketing copy, or user-facing text

### Quick Copywriting Quality Check
IMMEDIATELY after creating or updating any website copy:
1. **Clarity check** - Ensure content uses simple, everyday language (8th-12th grade reading level)
2. **User focus** - Verify content addresses specific user pain points and needs
3. **Accessibility** - Check for inclusive language, proper heading structure, and clear CTAs
4. **Value proposition** - Confirm benefits are clearly stated and compelling

This verification ensures content meets user needs and conversion goals.

### Comprehensive Copywriting Review
Reference the full checklist in `/context/copywriting-best-practices.md` when:
- Starting new website projects
- Creating landing pages or marketing content
- Conducting content audits
- Writing microcopy and UX content
- Planning international content strategy
- Reviewing existing copy for optimization opportunities

## Visual Development

### Design Principles
- Comprehensive design checklist in `/context/design-principles.md`
- Brand style guide in `/context/style-guide.md`
- When making visual (front-end, UI/UX) changes, always refer to these files for guidance

### Quick Visual Check
IMMEDIATELY after implementing any front-end change:
1. **Identify what changed** - Review the modified components/pages
2. **Navigate to affected pages** - Use `mcp__playwright__browser_navigate` to visit each changed view
3. **Verify design compliance** - Compare against `/context/design-principles.md` and `/context/style-guide.md`
4. **Validate feature implementation** - Ensure the change fulfills the user's specific request
5. **Check acceptance criteria** - Review any provided context files or requirements
6. **Capture evidence** - Take full page screenshot at desktop viewport (1440px) of each changed view
7. **Check for errors** - Run `mcp__playwright__browser_console_messages`

This verification ensures changes meet design standards and user requirements.

### Comprehensive Design Review
Invoke the `@agent-design-review` subagent for thorough design validation when:
- Completing significant UI/UX features
- Before finalizing PRs with visual changes
- Needing comprehensive accessibility and responsiveness testing

## Next.js Clean Code

### Clean Code Standards
- Comprehensive Next.js best practices in `/context/nextjs-clean-code.md`
- When working with Next.js projects, always refer to this file for guidance

### Quick Code Quality Check
IMMEDIATELY after implementing any Next.js feature:
1. **TypeScript validation** - Run `tsc --noEmit` to check type safety
2. **Linting check** - Run `npm run lint` or `yarn lint` to validate code standards
3. **Component structure** - Verify single responsibility principle and proper separation of concerns
4. **Performance check** - Ensure proper use of Next.js optimizations (Image, font loading, code splitting)
5. **Security validation** - Check input validation, authentication patterns, and data protection
6. **Test coverage** - Run tests and verify new functionality is properly tested
7. **Bundle analysis** - Check bundle size impact with `npm run analyze` if available

This verification ensures code meets Next.js best practices and clean code standards.

### Comprehensive Clean Code Review
Reference the full checklist in `/context/nextjs-clean-code.md` when:
- Starting new Next.js features or components
- Conducting code reviews
- Refactoring existing code
- Setting up new Next.js projects