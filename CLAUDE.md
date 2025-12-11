# CLAUDE.md - AI Assistant Guide

This document provides comprehensive guidance for AI assistants (like Claude) working with this repository. It outlines the codebase structure, development workflows, conventions, and best practices.

## Repository Overview

**Repository Name:** sulifang19860625-cyber/-
**Current State:** This is a minimal/starter repository
**Primary Branch:** (to be determined based on development needs)

## Current Repository Structure

```
/
├── .git/           # Git version control
├── README.md       # Project documentation
└── CLAUDE.md       # This file - AI assistant guide
```

## Development Workflow

### Branch Management

This repository uses Claude-specific feature branches for development:

- **Feature Branches:** Named with pattern `claude/claude-md-{session-id}-{unique-id}`
- **Current Branch:** `claude/claude-md-mj1bxojm2n8jg53i-01Q1Z1rUR2jW259xw1tnTXKy`

#### Branch Workflow Rules

1. **Always develop on the designated Claude branch** for the current session
2. **Never push to main/master** without explicit permission
3. **Create meaningful commits** with clear, descriptive messages
4. **Push using:** `git push -u origin <branch-name>`
5. **Branch names must start with 'claude/'** and end with matching session ID

### Git Operations Best Practices

#### Pushing Changes
```bash
git push -u origin <branch-name>
```
- CRITICAL: Branch must start with 'claude/' and end with matching session ID
- Retry up to 4 times with exponential backoff (2s, 4s, 8s, 16s) on network failures
- Only retry on network errors, not authentication or permission errors

#### Fetching/Pulling
```bash
git fetch origin <branch-name>
git pull origin <branch-name>
```
- Prefer fetching specific branches
- Retry up to 4 times with exponential backoff on network failures

### Commit Guidelines

1. **Descriptive messages:** Focus on "why" rather than "what"
2. **Follow existing patterns:** Review recent commits with `git log` for style
3. **Atomic commits:** Each commit should represent one logical change
4. **No secrets:** Never commit sensitive files (.env, credentials.json, etc.)

## Code Conventions

### General Principles

1. **Read Before Modifying:** Always read files before making changes
2. **Avoid Over-Engineering:** Only make requested changes
3. **Keep It Simple:** Don't add unnecessary features, abstractions, or "improvements"
4. **Security First:** Be vigilant about OWASP top 10 vulnerabilities
5. **No Backwards Compatibility Hacks:** Delete unused code completely

### What NOT to Do

- Don't add features beyond what was requested
- Don't refactor code unless specifically asked
- Don't add docstrings/comments to unchanged code
- Don't add error handling for impossible scenarios
- Don't create helpers/utilities for one-time operations
- Don't design for hypothetical future requirements
- Don't rename unused variables with `_` prefix - delete them

### Security Considerations

Always check for and prevent:
- Command injection
- Cross-Site Scripting (XSS)
- SQL injection
- Other OWASP Top 10 vulnerabilities
- Hardcoded secrets or credentials

## File Organization

As this repository grows, follow these organizational principles:

### Recommended Structure (for future development)

```
/
├── src/              # Source code
│   ├── components/   # Reusable components
│   ├── utils/        # Utility functions
│   ├── services/     # Business logic/services
│   └── types/        # Type definitions
├── tests/            # Test files
├── docs/             # Additional documentation
├── config/           # Configuration files
├── scripts/          # Build and utility scripts
├── .gitignore        # Git ignore rules
├── README.md         # Project documentation
└── CLAUDE.md         # This file
```

### File Naming Conventions

- Use **kebab-case** for file names: `my-component.js`
- Use **PascalCase** for component files: `MyComponent.jsx`
- Use descriptive, clear names that indicate purpose
- Group related files in appropriate directories

## Development Tasks

### Common Task Patterns

#### Adding a New Feature
1. Read relevant existing code first
2. Understand the current architecture
3. Make minimal, focused changes
4. Test the implementation
5. Commit with clear message
6. Push to the feature branch

#### Fixing a Bug
1. Identify and read the problematic code
2. Understand the root cause
3. Fix only what's broken
4. Verify the fix doesn't introduce new issues
5. Commit with description of the fix
6. Push to the feature branch

#### Code Analysis
1. Use search tools efficiently (Grep, Glob)
2. Read relevant files thoroughly
3. Understand context and dependencies
4. Provide clear, actionable insights

## Tool Usage Guidelines

### Preferred Tools for Common Tasks

- **File Search:** Use `Glob` tool (not `find` or `ls`)
- **Content Search:** Use `Grep` tool (not `grep` or `rg` commands)
- **Reading Files:** Use `Read` tool (not `cat`/`head`/`tail`)
- **Editing Files:** Use `Edit` tool (not `sed`/`awk`)
- **Writing Files:** Use `Write` tool (not `echo >` or `cat <<EOF`)
- **Exploration:** Use `Task` tool with `subagent_type=Explore` for codebase exploration

### Parallel Operations

When operations are independent, execute them in parallel:
```bash
# Good: Parallel independent commands
git status & git diff & git log
```

When operations are dependent, chain them:
```bash
# Good: Sequential dependent commands
git add . && git commit -m "message" && git push
```

## Testing Strategy

### Test File Organization
- Co-locate tests with source files or use `/tests` directory
- Name test files with `.test.js` or `.spec.js` suffix
- Write clear, descriptive test names

### Running Tests
```bash
# Add appropriate test commands as project grows
npm test
# or
pytest
# or other test runner
```

## Documentation Standards

### README.md
- Should contain project overview, setup instructions, and usage
- Keep it updated as features are added
- Include prerequisites and dependencies

### Code Comments
- Only add comments where logic isn't self-evident
- Don't comment obvious code
- Explain "why" not "what"
- Keep comments up-to-date with code changes

### CLAUDE.md (This File)
- Update as the project evolves
- Add new conventions as they emerge
- Document architectural decisions
- Keep AI assistants informed of project-specific patterns

## Error Handling

### Best Practices
- Only validate at system boundaries (user input, external APIs)
- Trust internal code and framework guarantees
- Don't add error handling for scenarios that can't happen
- Use appropriate error types and messages

## Environment and Configuration

### Environment Variables
- Never commit `.env` files
- Use `.env.example` for documentation
- Load environment variables appropriately for the tech stack
- Document all required environment variables

### Configuration Files
- Keep configuration separate from code
- Use appropriate config formats (JSON, YAML, TOML)
- Document configuration options

## Communication Patterns

### For AI Assistants

1. **Be Concise:** Responses should be clear and to the point
2. **No Emojis:** Unless explicitly requested by the user
3. **Markdown Formatting:** Use appropriate formatting for readability
4. **Code References:** Use `file_path:line_number` format for references
5. **Show Progress:** Use TodoWrite tool for multi-step tasks

### Example Reference Format
```
The authentication logic is in src/auth/login.js:42
```

## Troubleshooting

### Common Issues

#### Push Failures
- Verify branch name starts with 'claude/' and has correct session ID
- Check network connectivity
- Retry with exponential backoff on network errors
- Don't retry on authentication failures

#### Merge Conflicts
- Fetch latest changes first
- Understand both versions before resolving
- Test after resolution
- Ask user for guidance on complex conflicts

#### Test Failures
- Read the error messages carefully
- Identify the root cause
- Fix the issue, don't just suppress the error
- Verify all tests pass before committing

## Project-Specific Notes

### Technology Stack
*To be determined as the project grows*

### Key Dependencies
*To be added as dependencies are introduced*

### Architectural Decisions
*Document major architectural decisions here*

### Known Limitations
*Document any current limitations or technical debt*

## Resources and References

### Useful Commands

```bash
# View repository status
git status

# View recent commits
git log --oneline -10

# View file history
git log --follow -- <file_path>

# View current branch
git branch --show-current

# View all branches
git branch -a

# View remotes
git remote -v
```

### External Documentation
*Add links to relevant documentation as needed*

## Changelog

### 2025-12-11
- Initial CLAUDE.md created
- Repository structure documented
- Development workflows established
- Code conventions defined

---

**Last Updated:** 2025-12-11
**Maintainer:** AI Assistant (Claude)
**Version:** 1.0.0

## Notes for Future Updates

This document should be updated whenever:
- New architectural patterns are established
- Technology stack changes
- New conventions are adopted
- Project structure evolves
- New team members or AI assistants join

Keep this document as a living guide that reflects the current state and best practices of the repository.
