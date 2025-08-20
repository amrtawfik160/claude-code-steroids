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