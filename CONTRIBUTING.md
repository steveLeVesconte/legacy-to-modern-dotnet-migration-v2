# Contributing to Legacy to Modern .NET Migration

Thank you for your interest in this project! This is primarily a learning and portfolio project documenting a comprehensive .NET Framework to .NET 9 migration journey. While it's maintained by a solo developer, contributions, feedback, and suggestions are welcome.

## 🎯 Project Goals

This project demonstrates:
- **Enterprise-grade migration methodology** from .NET Framework 4.8 to .NET 9
- **Azure cloud-native architecture** using Azure SQL, Container Apps, Service Bus, and API Management
- **Professional development practices** including trunk-based development, comprehensive testing, and observability
- **Transparent documentation** of decisions, challenges, and lessons learned throughout the migration

## 🤝 Ways to Contribute

### 1. **Report Issues**
Found a bug, unclear documentation, or have a question? [Open an issue](https://github.com/steveLeVesconte/legacy-to-modern-dotnet-migration-v2/issues) using one of these categories:
- **Bug Report**: Something isn't working as expected
- **Documentation**: Clarification or improvement needed
- **Question**: Need help understanding an approach or decision
- **Enhancement**: Suggestion for improvement (subject to scope boundaries)

### 2. **Suggest Improvements**
Have ideas for better approaches, tooling, or patterns? Open an issue with:
- Clear description of the improvement
- Rationale for why it would benefit the project
- Any relevant resources or examples

**Note**: Major architectural changes may be deferred to maintain focus on core migration goals.

### 3. **Share Your Experience**
If you're working on a similar migration, share your lessons learned! This helps the broader .NET community. Consider:
- Commenting on relevant issues with your insights
- Linking to your own migration documentation
- Suggesting alternative approaches you've tried

### 4. **Fix Documentation**
Minor documentation improvements are always welcome:
- Typos or grammatical errors
- Broken links
- Clarity improvements
- Missing context

For documentation PRs, follow the workflow below but expect fast-track approval.

## 🔧 Development Workflow

### Prerequisites

Before contributing code:
1. **Review the README** to understand project goals and current phase
2. **Read the [Git Strategy](docs/process/git-strategy-v2.md)** for workflow conventions
3. **Check existing issues** to avoid duplicate work

### Setup

```bash
# Fork and clone the repository
git clone https://github.com/YOUR-USERNAME/legacy-to-modern-dotnet-migration-v2.git
cd legacy-to-modern-dotnet-migration-v2

# Add upstream remote
git remote add upstream https://github.com/steveLeVesconte/legacy-to-modern-dotnet-migration-v2.git

# Create a feature branch
git checkout -b feat/your-improvement
```

### Making Changes

1. **Keep changes focused**: One logical change per PR
2. **Follow conventions**: Use existing code style and patterns
3. **Add tests**: Include tests for any new functionality
4. **Update documentation**: Reflect changes in relevant docs

### Commit Messages

Use [Conventional Commits](https://www.conventionalcommits.org/) format:

```
<type>(<scope>): <short summary>

<optional body>

<optional footer>
```

**Types:**
- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation only
- `test:` - Adding or updating tests
- `refactor:` - Code refactoring
- `perf:` - Performance improvement
- `chore:` - Maintenance tasks

**Examples:**
```bash
docs: fix broken links in Phase 2 deployment guide

test(phase-1): add shopping cart edge case tests

fix(phase-4): resolve EF Core lazy loading issue
```

### Pull Request Process

1. **Push your branch**
```bash
git push origin feat/your-improvement
```

2. **Create Pull Request** on GitHub with:
   - Clear title following conventional commit format
   - Description of what changed and why
   - Link to related issue if applicable
   - Screenshots or examples if relevant

3. **Address feedback**
   - Respond to review comments
   - Make requested changes
   - Push updates to the same branch

4. **Merge**
   - PRs are squash-merged to maintain clean history
   - Branches are deleted after merge

## 📋 Code Standards

### General Principles
- **Clarity over cleverness**: Code should be easily understood
- **Consistency**: Match existing patterns in the codebase
- **Testability**: Write code that's easy to test
- **Documentation**: Explain non-obvious decisions

### .NET Conventions
- Follow Microsoft's [C# Coding Conventions](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions)
- Use meaningful variable and method names
- Keep methods focused and single-purpose
- Add XML documentation comments for public APIs

### Testing Standards
- Write clear test names: `MethodName_Scenario_ExpectedResult`
- Arrange-Act-Assert pattern for test structure
- Test both happy path and edge cases
- Keep tests independent and repeatable

## 🚧 Scope and Boundaries

### In Scope
- Bug fixes that don't alter core architecture
- Documentation improvements and clarifications
- Test coverage improvements
- Performance optimizations aligned with project goals
- Alternative implementation suggestions (as issues for discussion)

### Out of Scope
- Major architectural changes (project follows established migration path)
- Technology stack changes (e.g., replacing EF Core with Dapper)
- New features unrelated to migration goals
- Changes that would complicate the learning narrative

**Rationale**: This is a learning project with a specific goal—demonstrating a methodical migration approach. Maintaining focus ensures the project remains a clear example for others following similar paths.

### Discussing Out-of-Scope Ideas
If you have suggestions outside the current scope:
1. Open an issue labeled `discussion`
2. Explain the value and use case
3. Be open to "deferred" or "won't implement" decisions
4. Consider it a contribution to the knowledge base even if not implemented

## 📚 Documentation Philosophy

This project uses a three-tier documentation approach:

### Living Documents (Always Current)
- **PROJECT-LOG.md**: Daily progress and decisions
- **README.md**: Project overview and status
- **KNOWN-LIMITATIONS.md**: Current constraints

### Phase Documentation (Frozen at Phase Completion)
- Detailed phase-specific guides in `docs/phase-NN/`
- Preserved as historical reference
- Shows evolution of thinking

### Source of Truth
- Git commit history and tags
- GitHub Issues and Pull Requests
- Phase-specific README files

When contributing documentation, ensure it goes in the right place:
- Current status updates → living documents
- Phase-specific details → phase folders
- Process/workflow changes → docs/process/

## 🤖 AI-Assisted Development

This project leverages AI tools (Claude, GitHub Copilot) as productivity multipliers. If you're contributing:
- **AI assistance is fine** for drafting, exploration, and boilerplate
- **Human validation is required** for all contributions
- **Provide context** if AI suggested an approach that needs explanation
- **Transparency is valued** but not required in PRs

## 🔍 Review Process

As a solo-maintained project:
- **Response time**: Typically within 2-3 days
- **Discussion encouraged**: Questions and clarifications are welcome
- **Collaboration expected**: May request changes or suggest alternatives
- **Respect for time**: Both yours and mine—let's keep it efficient

## 📞 Communication

### Preferred Channels
- **GitHub Issues**: Feature requests, bugs, questions
- **Pull Request comments**: Implementation discussion
- **Discussions**: General migration questions or experience sharing

### Response Expectations
- Issues: Acknowledged within 2-3 days
- PRs: Initial review within 3-5 days
- Questions: Best-effort support, no SLA

## 🙏 Recognition

All contributors will be:
- Acknowledged in commit messages and PR descriptions
- Listed in project acknowledgments for significant contributions
- Thanked genuinely for helping improve this resource

## 📝 License

By contributing, you agree that your contributions will be licensed under the MIT License that covers this project. See the [LICENSE](LICENSE) file for details.

## 🚀 Getting Started Checklist

Ready to contribute? Here's your quick-start:

- [ ] Read this CONTRIBUTING.md
- [ ] Review the [README](README.md) and [Git Strategy](docs/process/git-strategy-v2.md)
- [ ] Check existing issues to avoid duplicates
- [ ] Fork the repository
- [ ] Create a feature branch
- [ ] Make your changes with clear commit messages
- [ ] Push and create a pull request
- [ ] Respond to feedback

## Questions?

Not sure if your contribution fits? Open an issue and let's discuss! The worst that happens is we mark it as out-of-scope—but even those discussions can benefit the broader .NET migration community.

---

**Thank you for considering contributing to this project!** Whether you report a bug, suggest an improvement, or just share your own migration experience, you're helping build a better resource for the .NET community.