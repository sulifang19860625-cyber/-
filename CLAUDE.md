# CLAUDE.md - AI Assistant Guide

This document provides comprehensive guidance for AI assistants working with this repository. It outlines the codebase structure, development workflows, conventions, and best practices.

## Repository Overview

**Repository Name:** `-`
**Owner:** sulifang19860625-cyber
**Status:** Early stage / Minimal codebase
**Primary Branch:** TBD (currently using feature branches)

### Current State

This is a newly initialized repository with minimal structure. As of the last analysis:
- Single README.md file in the root
- No defined technology stack yet
- No package managers or build tools configured
- Clean git history with initial commit

## Repository Structure

```
/
├── .git/              # Git repository metadata
├── README.md          # Project documentation
└── CLAUDE.md          # This file - AI assistant guidelines
```

### Expected Future Structure

As the project develops, typical structure may include:
```
/
├── src/               # Source code
├── tests/             # Test files
├── docs/              # Documentation
├── config/            # Configuration files
├── scripts/           # Build/deployment scripts
├── .github/           # GitHub workflows and templates
├── package.json       # If Node.js project
├── requirements.txt   # If Python project
├── Cargo.toml         # If Rust project
└── [other files]      # Project-specific files
```

## Development Workflow

### Git Branch Strategy

**Feature Branch Convention:**
- All development occurs on feature branches
- Branch naming pattern: `claude/claude-md-<identifier>-<session-id>`
- Current active branch: `claude/claude-md-mj0xkbhgv9qpyf17-01SGEpdoMaraZKtXY2sufY9R`
- Never push to main/master without explicit permission
- Always verify you're on the correct branch before committing

### Git Operations Best Practices

**Pushing Changes:**
```bash
# Always use -u flag for first push
git push -u origin <branch-name>

# CRITICAL: Branch must start with 'claude/' and end with matching session id
# Network failures: Retry up to 4 times with exponential backoff (2s, 4s, 8s, 16s)
```

**Fetching/Pulling:**
```bash
# Prefer specific branch fetches
git fetch origin <branch-name>
git pull origin <branch-name>

# Apply same retry logic for network failures
```

**Committing:**
- Write clear, descriptive commit messages
- Focus on the "why" rather than just the "what"
- Use conventional commit format when applicable:
  - `feat:` for new features
  - `fix:` for bug fixes
  - `docs:` for documentation
  - `refactor:` for code refactoring
  - `test:` for test additions/changes
  - `chore:` for maintenance tasks

### Code Review & Quality

- Never commit changes to files you haven't read first
- Understand existing code before suggesting modifications
- Run tests before committing (when test suite exists)
- Check for security vulnerabilities (OWASP Top 10)
- Avoid over-engineering - keep solutions simple and focused

## AI Assistant Conventions

### General Principles

1. **Read Before Write:** Always read files before modifying them
2. **Minimal Changes:** Only make requested changes, avoid scope creep
3. **No Over-Engineering:** Don't add unnecessary features, abstractions, or error handling
4. **Security First:** Check for injection vulnerabilities, XSS, etc.
5. **Prefer Editing:** Always prefer editing existing files over creating new ones

### Task Management

- Use TodoWrite tool to track multi-step tasks
- Mark tasks as completed immediately after finishing
- Keep only one task in_progress at a time
- Break complex tasks into smaller, actionable steps

### Communication Style

- Be concise and direct (CLI environment)
- Use GitHub-flavored markdown for formatting
- Avoid emojis unless explicitly requested
- Don't use bash echo or comments to communicate with users
- Provide technical accuracy over validation

### Code References

When referencing code, use the pattern: `file_path:line_number`

Example: "The initialization happens in src/main.js:42"

### Tool Usage Guidelines

**File Operations:**
- Use `Read` instead of `cat/head/tail`
- Use `Edit` instead of `sed/awk`
- Use `Write` instead of `echo >` or `cat <<EOF`

**Code Exploration:**
- Use `Task` tool with `subagent_type=Explore` for understanding codebase structure
- Use `Glob` for finding files by pattern
- Use `Grep` for searching file contents
- Avoid using bash `find` or `grep` commands directly

**Parallel Execution:**
- Call independent tools in parallel when possible
- Use single message with multiple tool calls for efficiency
- Only execute sequentially when there are dependencies

## Development Guidelines

### Code Style

As the project develops, update this section with:
- Language-specific style guides
- Naming conventions
- File organization patterns
- Comment and documentation standards

### Testing Strategy

When tests are added, document:
- Testing framework in use
- How to run tests
- Coverage requirements
- Test file organization

### Build & Deployment

When build processes are established, document:
- Build commands
- Environment setup
- Deployment procedures
- Configuration management

### Dependencies

When dependencies are added, document:
- How to install dependencies
- Version management strategy
- Update procedures
- Security scanning practices

## Security Considerations

### Common Vulnerabilities to Avoid

1. **Command Injection:** Never execute user input directly
2. **XSS (Cross-Site Scripting):** Sanitize all user-generated content
3. **SQL Injection:** Use parameterized queries
4. **Path Traversal:** Validate file paths
5. **Insecure Dependencies:** Keep dependencies updated
6. **Exposed Secrets:** Never commit credentials or API keys
7. **Insufficient Authentication:** Implement proper auth mechanisms
8. **Insecure Deserialization:** Validate serialized data
9. **Broken Access Control:** Enforce proper permissions
10. **Insufficient Logging:** Log security-relevant events

### Secret Management

- Never commit files like `.env`, `credentials.json`, or private keys
- Use environment variables for sensitive configuration
- Add sensitive files to `.gitignore`
- Rotate credentials if accidentally committed

## Contributing Workflow

### For AI Assistants

1. **Understand the Request:**
   - Read the task description carefully
   - Ask clarifying questions if needed
   - Check for existing related code

2. **Plan the Work:**
   - Create todos for multi-step tasks
   - Identify files that need to be read or modified
   - Consider security implications

3. **Implement Changes:**
   - Read existing files first
   - Make minimal, focused changes
   - Follow existing patterns and conventions
   - Test changes when possible

4. **Commit & Push:**
   - Stage relevant files with `git add`
   - Write clear commit message
   - Push to the designated feature branch
   - Verify push succeeded

5. **Create Pull Request (if requested):**
   - Analyze full commit history for the branch
   - Write comprehensive PR description with:
     - Summary of changes (1-3 bullet points)
     - Test plan (bulleted checklist)
   - Use `gh pr create` with heredoc for body

## Project-Specific Conventions

*This section should be updated as project conventions are established*

### Naming Conventions

- Files: TBD
- Functions: TBD
- Variables: TBD
- Constants: TBD
- Classes: TBD

### Architecture Patterns

*Document architectural decisions and patterns as they emerge*

### API Conventions

*Document API design patterns when applicable*

## Troubleshooting

### Common Issues

**Git Push Failures:**
- Verify branch name starts with 'claude/' and ends with session ID
- Check network connectivity
- Retry with exponential backoff
- Verify you have push permissions

**Merge Conflicts:**
- Pull latest changes from base branch
- Resolve conflicts carefully
- Test after resolution
- Commit with clear message about conflict resolution

**Build Failures:**
- Check error messages carefully
- Verify all dependencies are installed
- Check for syntax errors
- Review recent changes

## Resources

### Documentation Links

*Add links to relevant documentation as project grows:*
- Project documentation
- API documentation
- Architecture diagrams
- Design documents

### External References

- [Git Best Practices](https://git-scm.com/book/en/v2)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)

## Changelog

### 2025-12-11
- Initial CLAUDE.md creation
- Established basic structure and conventions
- Documented git workflow and branch strategy
- Added security guidelines and best practices

---

## Notes for Future Updates

This document should be updated whenever:
- New technologies or frameworks are added
- Coding conventions are established
- Architecture decisions are made
- New workflows or processes are introduced
- Security requirements change
- Team structure or practices evolve

Keep this document synchronized with the actual state of the repository to ensure AI assistants have accurate, up-to-date guidance.
