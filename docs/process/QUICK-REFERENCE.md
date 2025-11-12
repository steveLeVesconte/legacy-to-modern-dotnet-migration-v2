# Developer Quick Reference

> Personal cheat sheet for daily development. For detailed rationale, see CONTRIBUTING.md and DOCUMENTATION-PLAN.md

## Branch Naming

**Format**: `<type>/phase-N-description`

```
feat/phase-N-description      # New features
fix/phase-N-description       # Bug fixes
docs/phase-N-description      # Documentation only
test/phase-N-description      # Test additions
refactor/phase-N-description  # Code refactoring
chore/phase-N-description     # Maintenance tasks
```

**Examples**:
- `feat/phase-1-integration-tests`
- `fix/phase-4-ef-migration-bug`
- `docs/phase-2-deployment-guide`

## Commit Messages

**Format**: `type(scope): brief description`

**Types**: feat, fix, docs, test, refactor, chore, perf

**Examples**:
```bash
feat(phase-1): add shopping cart integration tests
fix(phase-3): resolve connection leak in middleware
docs(phase-2): update Azure deployment guide
test(phase-1): add checkout workflow tests
```

## Daily Workflow

```bash
# Start new work
git checkout main
git pull
git checkout -b feat/phase-N-description

# During work (commit regularly)
git add .
git commit -m "feat(scope): descriptive message"

# Push and create PR
git push origin feat/phase-N-description
# Then create PR on GitHub with template
```

## Common Git Fixes

```bash
# Forgot to create branch before starting
git stash
git checkout -b feat/phase-N-description
git stash pop

# Wrong branch name
git branch -m old-name new-name

# Update branch from main
git checkout main
git pull
git checkout feature-branch
git merge main

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Amend last commit message
git commit --amend -m "new message"
```

## Documentation Schedule

**Daily** (~10 min):
- Update PROJECT-LOG.md with work progress

**Weekly** (~30-45 min):
- Review KNOWN-LIMITATIONS.md
- Check GitHub Issues alignment
- Friday health check

**Phase End** (~2-3 hrs):
- Update README.md status
- Finalize docs/phase-NN/README.md
- Create git tag (vN.0.0)
- Update CHANGELOG.md

## When to Create...

**ADR** (Architecture Decision Record):
- Choosing test framework, deployment strategy
- Architectural pattern decisions
- Technology stack choices
- When alternatives exist and decision needs justification

**GitHub Issue**:
- Task >2 hours
- Needs discussion or tracking
- Bug reports
- Feature requests

**Branch**:
- Any work touching production code
- Even for small changes (professional practice)

**PR** (Pull Request):
- Every branch merge
- Use template in .github/pull_request_template.md
- Self-review on GitHub before merging

**TROUBLESHOOTING.md**:
- Phase has >3 complex problems
- Problem took >1 hour to solve
- Likely to recur

## PROJECT-LOG.md Top Section

Keep this current at all times:

```markdown
## Active Work
**Current Phase**: Phase N: Phase Name
**Current Branch**: type/phase-N-description
**Next Milestone**: Complete phase-N-x OR Merge PR #N
**Blocked On**: [Issue #N] OR Nothing currently

**Phase N Status**: 🚧 IN PROGRESS | ✅ COMPLETE | ⚠️ BLOCKED
```

## File Locations

```
/tests/MvcMusicStore.Tests/        # Test projects
/docs/phase-NN/                    # Phase-specific docs
/docs/adr/                         # Architecture Decision Records
/infrastructure/                   # Bicep, deployment scripts
/.github/workflows/                # CI/CD pipelines
/docs/prompts/                     # Selected prompt examples
```

## Phase Workflow Pattern

1. **Plan** → Create GitHub issue
2. **Branch** → `git checkout -b feat/phase-N-description`
3. **Work** → Commit daily with conventional commits
4. **Push** → Push and create PR using template
5. **Review** → Self-review on GitHub
6. **Merge** → Squash for features, merge for phases
7. **Document** → Update PROJECT-LOG.md
8. **Close** → Close issue, delete branch

## Merge Strategies

**Squash and Merge**:
- Feature branches (clean main history)
- Single logical change
- Result: One commit in main

**Merge Commit**:
- Phase branches to main
- Preserve feature history
- Result: All commits preserved

**Never Rebase and Merge**: Too risky for solo dev

## Version Tagging

**Format**: `vMAJOR.MINOR.PATCH`
- **MAJOR** = Phase number (v1.0.0, v2.0.0)
- **MINOR** = Feature within phase (v1.1.0)
- **PATCH** = Bug fixes (v1.0.1)

```bash
# After phase completion
git checkout main
git pull
git tag -a v1.0.0 -m "Phase 1: Foundation Complete"
git push origin v1.0.0
```

## Professional Git Practices

**Do**:
- ✅ Clear, descriptive commit messages
- ✅ Conventional commits format
- ✅ Create PRs even solo (shows process)
- ✅ Self-review on GitHub
- ✅ Tag releases at phase boundaries
- ✅ Delete merged branches
- ✅ Commit daily minimum

**Don't**:
- ❌ Commit directly to main (except initial setup)
- ❌ Vague messages ("fix", "update", "wip")
- ❌ Branches unmerged for weeks
- ❌ Skip PR process
- ❌ Force push to shared branches

## Quick Decision Trees

**Should I create an ADR?**
- Significant technical decision? → Yes
- Multiple viable alternatives? → Yes
- Future-me will wonder "why"? → Yes
→ **CREATE ADR**

**Where does this info go?**
- Daily work/decisions → PROJECT-LOG.md
- Current status → README.md
- Out of scope → KNOWN-LIMITATIONS.md
- Technical decision → docs/adr/
- Phase outcomes → docs/phase-NN/README.md
- Recurring problems → TROUBLESHOOTING.md
- Process conventions → This file

## Weekly Health Check (Friday, 10 min)

- [ ] PROJECT-LOG.md top section current?
- [ ] README.md status matches reality?
- [ ] New discoveries in KNOWN-LIMITATIONS.md?
- [ ] Any ADRs needed for this week's decisions?
- [ ] QUICK-REFERENCE.md need updates?
- [ ] GitHub Issues in sync with blockers?

## Common Lookups

**Project Purpose**: Non-tutorial learning lab + portfolio for hiring managers  
**Current Phase**: Check README.md "Current Status" section  
**Seed Project**: [github.com/steveLeVesconte/MvcMusicStore](https://github.com/steveLeVesconte/MvcMusicStore)  
**Admin Creds** (local): admin@musicstore.com / Admin123!

## Phase Quick Reference

| Phase | Focus | Duration |
|-------|-------|----------|
| 0 | Planning & Setup | 3-5 days |
| 1 | Foundation & Testing | 1-2 weeks |
| 2 | Azure Migration | 2-3 weeks |
| 3 | Azure Validation | 1 week |
| 4 | Platform Migration (.NET 9) | 3-4 weeks |
| 5 | Modern Auth | 1-2 weeks |
| 6 | Observability | 1-2 weeks |
| 7 | Scalability | 2-3 weeks |
| 8 | API-First | 2-3 weeks |
| 9 | Cloud Native | 2-3 weeks |
| 10 | DevOps Excellence | 1-2 weeks |

---

**Last Updated**: 2025-11-12  
**Keep This File Updated**: When you look something up repeatedly
