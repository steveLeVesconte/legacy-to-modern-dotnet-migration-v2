# Git Workflow Implementation Guide - Quick Start

## 🎯 Goal
Get your v2 project running with professional git practices in under 30 minutes.

---

## Part 1: Repository Setup (10 minutes)

### Step 1: Configure Main Branch Protection

**On GitHub:**
1. Go to repository **Settings** → **Branches**
2. Click **Add branch protection rule**
3. Branch name pattern: `main`
4. Enable these settings:
   - ✅ Require a pull request before merging
   - ✅ Require approvals: 1 (yourself)
   - ✅ Dismiss stale pull request approvals when new commits are pushed
   - ✅ Allow specified actors to bypass required pull requests: (add yourself)
   - ✅ Do not allow bypassing the above settings
5. Click **Create**

**Why**: Prevents accidental direct commits to main while allowing you to bypass when truly needed.

### Step 2: Create PR Template

```bash
cd legacy-to-modern-dotnet-migration-v2
mkdir -p .github
```

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

## Related Issues
Closes #

## Testing
<!-- How was this tested? -->

## Checklist
- [ ] Commit messages follow conventional commits format
- [ ] Tests pass locally
- [ ] Documentation updated if needed
- [ ] Self-review completed
```

```bash
git add .github/
git commit -m "chore: add pull request template"
git push origin main
```

### Step 3: Create Issue Labels

**On GitHub:**
1. Go to **Issues** → **Labels**
2. Create these labels:

| Label Name      | Color   | Description                                |
| --------------- | ------- | ------------------------------------------ |
| `phase-0`       | #0075ca | Phase 0: Planning                          |
| `phase-1`       | #0e8a16 | Phase 1: Foundation                        |
| `phase-2`       | #1d76db | Phase 2: Azure Migration                   |
| `phase-3`       | #5319e7 | Phase 3: Azure Validation                  |
| `phase-4`       | #e99695 | Phase 4: Platform Migration                |
| `bug`           | #d73a4a | Something isn't working                    |
| `enhancement`   | #a2eeef | New feature or request                     |
| `documentation` | #0075ca | Improvements or additions to documentation |
| `testing`       | #7057ff | Test-related changes                       |

### Step 4: Create Phase Milestones

**On GitHub:**

1. Go to **Issues** → **Milestones** → **New milestone**
2. Create:
   - **Phase 1: Foundation** (Due: ~2 weeks from now)
   - **Phase 2: Azure Migration** (Due: ~4 weeks from Phase 1)
   - **Phase 3: Azure Validation** (Due: ~2 weeks from Phase 2)

---

## Part 2: Daily Workflow (5 minutes to learn)

### Starting a New Feature

```bash
# 1. Get latest code
git checkout main
git pull origin main

# 2. Create feature branch
git checkout -b feat/phase-1-setup-xunit

# 3. Make your changes
# ... edit files ...

# 4. Commit with conventional commits
git add .
git commit -m "feat(phase-1): add xUnit test project

- Install xUnit 2.9.2
- Install Moq 4.20.72  
- Install FluentAssertions 6.12.2
- Create test project targeting .NET Framework 4.8
- Add smoke tests to verify xUnit works

All tests passing (2/2)."

# 5. Push to remote
git push -u origin feat/phase-1-setup-xunit
```

### Creating Pull Request

**On GitHub:**
1. Go to **Pull requests** → **New pull request**
2. Base: `main` ← Compare: `feat/phase-1-setup-xunit`
3. Fill out PR template:
   - **Title**: "Phase 1: Add xUnit testing framework"
   - **Description**: Fill in template sections
   - **Milestone**: Select "Phase 1: Foundation"
   - **Labels**: Add `phase-1`, `testing`, `enhancement`
4. Click **Create pull request**
5. Click **Files changed** tab → Review your code
6. Approve your own PR (yes, this is intentional for solo dev)
7. Click **Squash and merge** → Confirm
8. Delete branch when prompted

### After Merge: Update Documentation

```bash
# Update PROJECT-LOG.md
echo "### 2025-11-15 - xUnit Testing Framework Setup

**Merged PR #1**: feat/phase-1-setup-xunit → main

Established xUnit testing foundation with Moq and FluentAssertions.
Smoke tests passing.

**Commit**: abc123d  
**Duration**: 1 day  
**Status**: ✅ Complete" >> PROJECT-LOG.md

git add PROJECT-LOG.md
git commit -m "docs: update PROJECT-LOG with xUnit setup completion"
git push origin main
```

---

## Part 3: Commit Message Cheat Sheet (Keep This Handy)

### Format
```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types (Choose One)
- `feat:` - New feature
- `fix:` - Bug fix
- `test:` - Add/update tests
- `docs:` - Documentation only
- `refactor:` - Code refactor (no behavior change)
- `perf:` - Performance improvement
- `chore:` - Maintenance (dependencies, config)

### Scopes (Optional)
- `phase-1`, `phase-2`, etc.
- `tests`, `docs`, `ci`
- `shopping-cart`, `checkout`, `auth`

### Examples

**Simple commit:**
```bash
git commit -m "test(phase-1): add ShoppingCart integration tests"
```

**Detailed commit:**
```bash
git commit -m "feat(phase-1): implement DatabaseFixture for test isolation

Creates shared xUnit collection fixture with:
- DropCreateDatabaseAlways initializer
- Minimal seed data (3 albums, 2 genres, 2 artists)
- Proper cleanup between tests

Enables integration tests to share database context
while maintaining isolation through fresh DbContext pattern.

Part of Phase 1b testing infrastructure."
```

**Bug fix:**
```bash
git commit -m "fix(phase-1): add eager loading to ShoppingCart.GetTotal()

Prevents NullReferenceException in tests when accessing
Album.Price by adding .Include(\"Album\") to query.

Fixes #4"
```

---

## Part 4: When to Use Phase Branches

### Decision Tree

**Start with feature branch directly from main:**
```bash
git checkout main
git checkout -b feat/phase-1-feature-name
```

**If phase grows complex (5+ features), create phase branch:**
```bash
# Create phase branch
git checkout main  
git checkout -b phase-4-platform-migration

# Create features from phase branch
git checkout phase-4-platform-migration
git checkout -b feat/phase-4-ef-core-models

# After PR approved, merge to phase branch (not main)
# When all features done, merge phase branch to main
```

### Simple Rule
- **Phases 1, 2, 3**: No phase branch needed (3-5 features each)
- **Phase 4**: Use phase branch (10+ features, breaking changes)
- **Phases 5-8**: Probably no phase branch
- **Phase 9**: Might need phase branch (Docker/containers)
- **Phase 10**: Probably no phase branch

---

## Part 5: Common Workflows

### Scenario: Quick Documentation Update

```bash
git checkout -b docs/phase-1-readme-update
# Edit README.md
git add README.md
git commit -m "docs(phase-1): update README with current status"
git push -u origin docs/phase-1-readme-update
# Create PR → Review → Squash and merge → Delete branch
```

### Scenario: Bug Fix

```bash
git checkout -b fix/phase-2-connection-leak
# Fix the bug
git add .
git commit -m "fix(phase-2): dispose DbContext in CheckoutController

Fixes memory leak in checkout flow by wrapping DbContext
in using statement.

Fixes #12"
git push -u origin fix/phase-2-connection-leak
# Create PR → Review → Squash and merge → Delete branch
```

### Scenario: Multi-Day Feature

```bash
# Day 1
git checkout -b feat/phase-1-checkout-tests
git commit -m "test(phase-1): add checkout test infrastructure"
git push -u origin feat/phase-1-checkout-tests

# Day 2  
git commit -m "test(phase-1): add CreateOrder integration tests"
git push

# Day 3
git commit -m "test(phase-1): add order validation tests"
git push
# Create PR → Review → Squash and merge (all commits become one)
```

### Scenario: Phase Complete

```bash
git checkout main
git pull origin main

# Create annotated tag
git tag -a v1.0.0 -m "Phase 1: Foundation Complete

Accomplishments:
- xUnit testing framework established  
- 36 integration tests implemented
- Test coverage baseline: 85%
- Local performance baselines captured
- Documentation framework established

Ready for Phase 2: Azure Migration"

git push origin v1.0.0
```

**Then on GitHub:**
1. Go to **Releases** → **Create a new release**
2. Tag: `v1.0.0`
3. Title: "Phase 1: Foundation Complete"
4. Description: Copy from tag message, add more details
5. Publish release

---

## Part 6: Git Commands Quick Reference

### Daily Use
```bash
# Check status
git status

# Start new feature
git checkout main && git pull && git checkout -b feat/phase-1-feature

# Stage changes
git add .                    # Stage all
git add file.cs              # Stage specific file

# Commit
git commit -m "type(scope): message"

# Push
git push                     # After first push
git push -u origin branch    # First push sets upstream

# Update branch with main changes  
git checkout main && git pull
git checkout your-branch
git merge main

# After PR merged, cleanup
git checkout main && git pull
git branch -d feat/phase-1-feature
```

### Fixing Mistakes
```bash
# Undo last commit (keep changes)
git reset --soft HEAD~1

# Change last commit message
git commit --amend -m "new message"

# Discard all uncommitted changes
git reset --hard HEAD

# See commit history
git log --oneline -10
```

---

## Part 7: First Day Checklist

Use this checklist when starting your v2 project:

### Morning (Setup - 30 minutes)
- [ ] Repository exists on GitHub
- [ ] Main branch protection configured
- [ ] PR template created and pushed
- [ ] Issue labels created
- [ ] Phase 1 milestone created
- [ ] Clone repository locally

### Afternoon (First Feature - 2-3 hours)
- [ ] Create issue: "Set up project from seed"
- [ ] Create branch: `feat/phase-1-project-setup`
- [ ] Copy seed project code
- [ ] Verify compilation
- [ ] Run smoke test
- [ ] Commit: `feat(phase-1): initialize project from seed`
- [ ] Push branch
- [ ] Create PR with template
- [ ] Self-review on GitHub
- [ ] Merge (squash and merge)
- [ ] Delete branch
- [ ] Update PROJECT-LOG.md
- [ ] Close issue

### Repeat Daily
- [ ] Pick next feature from Phase 1 plan
- [ ] Create issue
- [ ] Create feature branch
- [ ] Work in small commits
- [ ] Push and create PR
- [ ] Self-review
- [ ] Merge and cleanup
- [ ] Update PROJECT-LOG.md

---

## Part 8: Avoiding Common Pitfalls

### ❌ Don't Do This
```bash
# NO: Committing directly to main
git checkout main
git commit -m "quick fix"
git push

# NO: Vague commit messages  
git commit -m "updates"
git commit -m "fix"
git commit -m "wip"

# NO: Huge commits
git add . 
# (after 2 weeks of work)
git commit -m "phase 1 complete"

# NO: Forgetting to update docs
# (merge PR, move to next feature, forget PROJECT-LOG)
```

### ✅ Do This Instead
```bash
# YES: Use feature branches
git checkout -b fix/quick-issue
git commit -m "fix(phase-2): resolve SQL timeout in checkout"
# Create PR, then merge

# YES: Descriptive commits
git commit -m "test(phase-1): add ShoppingCart integration tests"
git commit -m "fix(phase-3): increase connection pool size"
git commit -m "docs: update README with Phase 2 status"

# YES: Regular small commits
git commit -m "test(phase-1): add GetCart tests"
# Next day:
git commit -m "test(phase-1): add AddToCart tests"  

# YES: Update docs immediately after merge
# PR merged → immediately update PROJECT-LOG → commit → push
```

---

## Part 9: Pro Tips 

### Make Your Repository Stand Out

**1. Clean Main Branch History**
Use squash and merge so main shows:

```
feat(phase-1): add xUnit testing framework
test(phase-1): implement ShoppingCart tests  
test(phase-1): implement Checkout tests
docs(phase-1): update README with progress
feat(phase-1): add performance baseline capture
chore: tag v1.0.0 - Phase 1 Complete
```

**2. Meaningful PR Titles**
- ❌ "Update tests"
- ✅ "Phase 1: Implement ShoppingCart integration tests with DatabaseFixture"

**3. Link Everything**
- Link PRs to issues
- Link commits to issues (`Fixes #23`)
- Link issues to milestones
- Tag releases at phase boundaries

**4. Show Your Process**
- Create issues before starting work
- Self-review PRs with comments
- Use PR template consistently
- Update docs after each merge

**5. Demonstrate Consistency**
- Commit at least daily (even if small)
- Follow conventional commits always
- Keep branches short-lived (1-3 days)
- Regular progress toward milestones

---

## Part 10: Troubleshooting

### "I committed to main by accident"

```bash
# If not pushed yet
git reset --soft HEAD~1  # Undo commit, keep changes
git checkout -b feat/phase-1-fix  # Create proper branch
git commit -m "proper message"  # Commit again
git push -u origin feat/phase-1-fix

# If already pushed to main
# Don't rewrite history! Instead:
git checkout -b fix/revert-accidental-commit
git revert <commit-hash>
git push -u origin fix/revert-accidental-commit
# Create PR to fix
```

### "I need to update my branch with main"

```bash
git checkout main
git pull origin main
git checkout your-feature-branch  
git merge main  # Merge main into your branch
# Resolve conflicts if any
git push
```

### "My commit message was wrong"

```bash
# If not pushed yet
git commit --amend -m "corrected message"

# If already pushed
# Leave it - not worth the hassle. Fix the next one.
```

### "I want to split a large commit"

```bash
# Before committing
git add file1.cs file2.cs
git commit -m "feat(phase-1): add models"

git add file3.cs file4.cs  
git commit -m "feat(phase-1): add controllers"

# After committing (not pushed)
git reset --soft HEAD~1  # Undo commit
# Then add and commit in smaller chunks
```

---

## Summary: Your V2 Workflow

**Every feature follows this pattern:**

1. 📋 **Plan**: Create GitHub issue
2. 🌿 **Branch**: `git checkout -b feat/phase-X-description`
3. 💻 **Work**: Make changes, commit daily with conventional commits
4. 🚀 **Push**: `git push -u origin branch-name`
5. 📝 **PR**: Create PR using template, link to issue and milestone
6. 👀 **Review**: Self-review on GitHub
7. ✅ **Merge**: Squash and merge, delete branch
8. 📚 **Document**: Update PROJECT-LOG.md immediately
9. 🔄 **Repeat**: Move to next feature

**At phase boundaries:**
- Tag release: `git tag -a v1.0.0 -m "Phase complete"`
- Create GitHub Release with summary
- Update README with status

This simple, consistent pattern will make your repository look professional while keeping overhead minimal for solo development.

---

## Next Steps

1. ✅ Complete Part 1 (Repository Setup) - **Do this now**
2. ✅ Practice Part 2 (Daily Workflow) - **Tomorrow**
3. ✅ Reference Part 3 (Commit Messages) - **Keep handy**
4. ✅ Follow Part 8 (First Day Checklist) - **This week**

**Time investment:**
- Setup: 30 minutes (one time)
- Daily overhead: 5-10 minutes per feature
- Documentation: 15 minutes per PR merge

**Payoff:**
- Professional portfolio that stands out
- Clear project history
- Sustainable workflow you can maintain

Good luck with your v2 project! 🚀
