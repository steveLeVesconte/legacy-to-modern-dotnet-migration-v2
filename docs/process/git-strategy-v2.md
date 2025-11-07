# Git Branch and Workflow Strategy - V2 Project

## Executive Summary

This strategy streamlines the v1 git workflow while maintaining professional standards for a solo developer creating a portfolio project. It balances pragmatic efficiency with the appearance of enterprise-grade practices.

**Key Improvements from V1:**
- Reduced branch complexity (fewer long-lived branches)
- Faster PR cycles (less overhead for solo work)
- Clearer commit messages using conventional commits
- Better use of GitHub features (milestones, releases, project boards)
- Maintained professional appearance with cleaner history

---

## Branch Strategy: Simplified Trunk-Based Development

### Core Principles

1. **Main branch protection**: Always stable, deployable code
2. **Short-lived feature branches**: Merge quickly (1-3 days max)
3. **Phase branches as milestones**: Only when needed for major work
4. **No sub-sub-branches**: Maximum two levels of branching

### Branch Structure

```
main (protected)
  ├── phase-1-foundation (milestone branch, optional)
  │   ├── feat/phase-1-setup-environment
  │   ├── feat/phase-1-shopping-cart-tests
  │   ├── feat/phase-1-checkout-tests
  │   └── feat/phase-1-baseline-metrics
  ├── feat/phase-2-azure-sql-migration
  ├── feat/phase-2-app-service-deployment
  └── fix/phase-3-performance-regression
```

### Branch Naming Convention

**Format**: `<type>/<phase>-<short-description>`

**Types:**
- `feat/` - New features or capabilities
- `fix/` - Bug fixes
- `docs/` - Documentation only
- `refactor/` - Code refactoring without behavior change
- `test/` - Adding or updating tests
- `chore/` - Maintenance tasks (dependencies, config)

**Examples:**
- `feat/phase-1-integration-tests`
- `fix/phase-4-ef-migration-bug`
- `docs/phase-2-deployment-guide`
- `refactor/phase-1-test-base-class`

---

## When to Use Phase Branches vs Direct Feature Branches

### Use Phase Branches When:
✅ Phase has 5+ feature branches  
✅ Phase duration > 2 weeks  
✅ Need to show incremental progress before merging to main  
✅ Phase has interdependent features that must merge together

**Example:** Phase 4 (Platform Migration) - multiple breaking changes that need integration testing together

### Skip Phase Branches When:
✅ Phase has 1-3 simple features  
✅ Phase duration < 1 week  
✅ Features are independent  
✅ Quick wins that can go directly to main

**Example:** Phase 7 (Scalability) - independent performance improvements

---

## Commit Message Convention

Use **Conventional Commits** format for professional appearance and automated changelog generation.

### Format
```
<type>(<scope>): <short summary>

<optional body>

<optional footer>
```

### Types
- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation changes
- `test:` - Adding or updating tests
- `refactor:` - Code refactoring
- `perf:` - Performance improvements
- `chore:` - Maintenance tasks

### Scopes (Optional but Recommended)
- `phase-1`, `phase-2`, etc.
- `tests`, `docs`, `ci`
- `shopping-cart`, `checkout`, `auth`

### Examples

**Good commits:**
```
feat(phase-1): add ShoppingCart integration tests

Implements 12 integration tests covering:
- Cart retrieval with session/user ID
- Add/remove item operations
- Cart totals and counts
- Empty cart functionality

Tests use DatabaseFixture for shared test context.
All tests passing (12/12).

Closes #15
```

```
fix(phase-4): resolve EF lazy loading in ShoppingCart.GetTotal()

Added eager loading with .Include("Album") to prevent 
NullReferenceException when accessing Album.Price in tests.

Fixes #23
```

```
docs(phase-1): update README with current Phase 1b status
```

**Avoid vague commits:**
```
❌ update code
❌ fix bug
❌ work in progress
❌ more changes
```

---

## Pull Request Workflow

### For Solo Development with Professional Appearance

#### 1. Create Feature Branch
```bash
git checkout main
git pull origin main
git checkout -b feat/phase-1-shopping-cart-tests
```

#### 2. Work and Commit Regularly
```bash
# Make changes
git add .
git commit -m "test(phase-1): add GetCart integration tests"

# Continue working
git add .
git commit -m "test(phase-1): add AddToCart integration tests"
```

#### 3. Push and Create PR
```bash
git push -u origin feat/phase-1-shopping-cart-tests
```

**On GitHub:**
- Create Pull Request with descriptive title
- Add description template (see below)
- Link to GitHub Issue if applicable
- Assign yourself as reviewer
- Add labels: `phase-1`, `tests`, etc.

#### 4. Self-Review Process
As a solo developer, still do self-review:
- Review the diff on GitHub (catches issues you miss locally)
- Check commit messages are clear
- Verify tests pass (GitHub Actions if configured)
- Add comments for future reference
- Approve your own PR

#### 5. Merge
- Use **Squash and Merge** for feature branches (clean history)
- Use **Merge Commit** for phase branches (preserve feature history)
- Delete branch after merge

---

## Pull Request Template

Create `.github/pull_request_template.md`:

```markdown
## Description
<!-- Brief summary of changes -->

## Type of Change
- [ ] New feature
- [ ] Bug fix
- [ ] Documentation update
- [ ] Refactoring
- [ ] Performance improvement

## Phase
<!-- e.g., Phase 1b - Testing Framework -->

## Testing
<!-- How was this tested? -->

## Related Issues
Closes #

## Checklist
- [ ] Code follows project conventions
- [ ] Tests added/updated and passing
- [ ] Documentation updated if needed
- [ ] Commit messages follow conventional commits
- [ ] Self-review completed


```

---

## GitHub Project Organization

### Issues
Use GitHub Issues for:
- Feature tracking
- Bug reports
- Technical debt
- Questions/investigations

**Issue Labels:**
- `phase-0` through `phase-10`
- `bug`, `enhancement`, `documentation`
- `testing`, `azure`, `performance`
- `good-first-issue` (for resume talking points)

### Milestones
Create milestones for each phase:
- **Phase 0: Planning** (Due: Oct 1, 2025)
- **Phase 1: Foundation** (Due: Oct 31, 2025)
- **Phase 2: Azure Migration** (Due: Nov 30, 2025)

Link PRs and issues to milestones for progress tracking.

### Project Boards (Optional)
For longer phases, use project board with columns:
- To Do
- In Progress
- In Review
- Done

---

## Typical Workflows

### Scenario 1: Small Feature (1-2 days)
```bash
# Create branch directly from main
git checkout -b feat/phase-1-catalog-tests

# Work and commit
git commit -m "test(phase-1): add catalog integration tests"

# Push and create PR
git push -u origin feat/phase-1-catalog-tests

# Merge directly to main via PR
# Delete branch
```

### Scenario 2: Complex Phase (2+ weeks, multiple features)
```bash
# Create phase branch
git checkout -b phase-4-platform-migration

# Create feature branches from phase branch
git checkout -b feat/phase-4-ef-core-migration

# Work and commit
git commit -m "feat(phase-4): migrate models to EF Core"

# Push and create PR targeting phase-4-platform-migration
git push -u origin feat/phase-4-ef-core-migration

# After PR approved, merge to phase branch
# Repeat for other features

# When phase complete, create final PR: phase-4-platform-migration -> main
# Tag release: v4.0.0
```

### Scenario 3: Quick Bug Fix
```bash
git checkout -b fix/phase-3-connection-leak

git commit -m "fix(phase-3): properly dispose DbContext in middleware"

git push -u origin fix/phase-3-connection-leak

# Create PR, merge directly to main
```

---

## Version Tagging Strategy

### Semantic Versioning
Follow SemVer: `vMAJOR.MINOR.PATCH`

**For this project:**
- **MAJOR** = Phase number (v1.0.0, v2.0.0, v3.0.0)
- **MINOR** = Significant feature within phase (v1.1.0, v1.2.0)
- **PATCH** = Bug fixes (v1.0.1, v1.0.2)

### Tagging Process
```bash
# After merging phase completion to main
git checkout main
git pull origin main

# Create annotated tag
git tag -a v1.0.0 -m "Phase 1: Foundation Complete

- xUnit testing framework configured
- 36 integration tests implemented
- Test coverage baseline established
- Local performance metrics captured"

git push origin v1.0.0
```

### GitHub Releases
Create GitHub Release for each major version:
- Title: "Phase 1: Foundation Complete"
- Tag: v1.0.0
- Description: Summary of accomplishments, metrics, next steps
- Attach artifacts if relevant (test reports, performance baselines)

---

## Merge Strategies

### Use Squash and Merge When:
✅ Feature branches with multiple WIP commits  
✅ Want clean, linear main branch history  
✅ Single logical change that was built incrementally

**Result:** One commit in main per feature branch

### Use Merge Commit When:
✅ Phase branches merging to main  
✅ Want to preserve feature branch history  
✅ Multiple independent features in one branch

**Result:** Preserves all commits with merge commit

### Never Use Rebase and Merge
❌ Too easy to mess up for solo developer  
❌ Loses branch context  
❌ Not worth the complexity

---

## Git Commands Quick Reference

### Daily Workflow
```bash
# Start new feature
git checkout main
git pull origin main
git checkout -b feat/phase-1-new-feature

# Regular commits
git status
git add .
git commit -m "feat(phase-1): descriptive message"

# Push to remote
git push -u origin feat/phase-1-new-feature

# Update branch with main changes
git checkout main
git pull origin main
git checkout feat/phase-1-new-feature
git merge main

# After PR merged
git checkout main
git pull origin main
git branch -d feat/phase-1-new-feature
```

### Fixing Mistakes
```bash
# Undo last commit (keep changes)
git reset --soft HEAD~1

# Amend last commit message
git commit --amend -m "new message"

# Discard all local changes
git reset --hard HEAD

# Revert a merged commit
git revert <commit-hash>
```

---

## Integration with Documentation

### Update After Each PR Merge
**PROJECT-LOG.md:**
```markdown
### 2025-11-15 - Shopping Cart Tests Complete

**Merged PR #15**: feat/phase-1-shopping-cart-tests → phase-1-foundation

Implemented 12 integration tests for ShoppingCart business logic...

**Commit**: a1b2c3d
**Duration**: 2 days
**Tests Added**: 12
**Status**: ✅ All passing
```

**README.md:**
Update "Current Status" section after each phase completion.

**KNOWN-LIMITATIONS.md:**
Document any issues discovered during feature work.

---

## Professional Git Practices for Solo Developer

### Do:
✅ Write clear, descriptive commit messages  
✅ Use conventional commits format  
✅ Create PRs even for solo work (shows process)  
✅ Link PRs to issues  
✅ Self-review your PRs on GitHub  
✅ Tag releases at phase boundaries  
✅ Keep main branch stable  
✅ Delete merged branches  
✅ Use consistent branch naming  
✅ Commit regularly (daily at minimum)

### Don't:
❌ Commit directly to main (except initial setup)  
❌ Use vague commit messages  
❌ Leave branches unmerged for weeks  
❌ Skip PR process to "save time"  
❌ Force push to shared branches  
❌ Rewrite public history  
❌ Forget to update documentation  
❌ Create overly complex branch hierarchies

---

## Comparison: V1 vs V2 Strategy

| Aspect | V1 Approach | V2 Approach | Rationale |
|--------|-------------|-------------|-----------|
| **Branch Depth** | 3 levels (main → phase → work/phase-X/steve/feature) | 2 levels max (main → feat/phase-X-feature) | Simpler for solo dev |
| **Phase Branches** | Always used | Only for complex phases (Phase 4, 9) | Reduce overhead |
| **Merge Speed** | 3-5 days per feature | 1-3 days per feature | Faster iteration |
| **Commit Messages** | Inconsistent | Conventional commits | Professional standard |
| **PRs** | Detailed (2-4 paragraphs) | Concise template | Balanced detail |
| **Branch Naming** | work/phase-X/steve/feature-name | feat/phase-X-feature-name | Cleaner, no redundancy |
| **Merge Strategy** | Merge commits everywhere | Squash for features, merge for phases | Clean main history |
| **Documentation** | High maintenance (3-4 hrs/week) | Streamlined (1 hr/week) | Sustainable |

---

## Step-by-Step Implementation for V2 Project

### Phase 0 Setup (NOW)

1. **Initialize Repository**
```bash
git clone <v2-repo-url>
cd legacy-to-modern-dotnet-migration-v2

# Configure main branch protection (on GitHub)
# - Require PR before merging
# - Require approval (yourself)
# - Delete branches after merge
```

2. **Create PR Template**
```bash
mkdir -p .github
# Create pull_request_template.md with template above
git add .github/
git commit -m "chore: add PR template for professional workflow"
git push origin main
```

3. **Create Issue Labels**
On GitHub:
- `phase-0` through `phase-10`
- `bug`, `enhancement`, `documentation`, `testing`
- `azure`, `performance`, `security`

4. **Create Milestones**
- Phase 0: Planning (current)
- Phase 1: Foundation
- Phase 2: Azure Migration
- (Create others as needed)

### Phase 1 First Feature Example

```bash
# Start Phase 1
git checkout -b feat/phase-1-project-setup

# Copy seed project, update dependencies
# ... work ...

git add .
git commit -m "feat(phase-1): initialize project from clean seed

- Copy MvcMusicStore seed project (v1.0.0)
- Update to .NET Framework 4.8
- Verify compilation and smoke test
- Add initial xUnit test project

Baseline established for Phase 1 testing work."

git push -u origin feat/phase-1-project-setup

# Create PR on GitHub
# Title: "Phase 1: Initialize project from clean seed"
# Description: Use PR template
# Link to Milestone: Phase 1
# Self-review and merge
```

### Ongoing Pattern

1. **Plan feature** (create GitHub issue)
2. **Create branch** (`feat/phase-X-description`)
3. **Work in small commits** (commit daily)
4. **Push and PR** (use template)
5. **Self-review** (on GitHub UI)
6. **Merge and delete** (squash for features)
7. **Update docs** (PROJECT-LOG.md)
8. **Close issue**

Repeat for each feature until phase complete, then tag release.

---

## Professional Portfolio Appearance

✅ **Clean commit history** - They'll review main branch commits  
✅ **Descriptive PR titles** - Shows thought process  
✅ **Linked issues and PRs** - Shows project management skills  
✅ **Regular commits** - Shows consistent work ethic  
✅ **Tagged releases** - Shows milestone discipline  
✅ **Self-review process** - Shows quality standards  
✅ **Clear documentation** - Shows communication skills

### What to Avoid

❌ Messy commit history ("fix", "update", "wip")  
❌ Stale branches (merged months ago, not deleted)  
❌ Direct commits to main  
❌ Inconsistent patterns  
❌ Abandoned features (unmerged branches)  
❌ Huge commits (1000+ lines)

---

## Conclusion

This strategy provides:

1. **Efficiency**: Faster iteration for solo developer (1-3 day PRs)
2. **Professionalism**: Clean history 
3. **Flexibility**: Use phase branches when needed, skip when not
4. **Maintainability**: Sustainable documentation practices
5. **Clear process**: Easy to follow, hard to mess up

The key improvement from v1 is **reducing unnecessary complexity** while maintaining the professional appearance. You'll spend less time managing git overhead and more time building features that demonstrate your skills.

**Next Steps:**
1. Set up repository with branch protection
2. Create PR template and issue labels
3. Create first feature branch for Phase 1
4. Follow the workflow for each feature
5. Review this document weekly as you work

