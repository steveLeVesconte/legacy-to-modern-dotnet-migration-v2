# Git Workflow Cheat Sheet - V2 Project

## Daily Workflow (5 Minutes)

```bash
# 1. Start new feature
git checkout main && git pull
git checkout -b feat/phase-1-feature-name

# 2. Work and commit
git add .
git commit -m "feat(phase-1): descriptive message"

# 3. Push and PR
git push -u origin feat/phase-1-feature-name
# Create PR on GitHub → Review → Squash merge → Delete branch

# 4. Update docs
# Edit PROJECT-LOG.md
git add PROJECT-LOG.md
git commit -m "docs: update PROJECT-LOG with feature completion"
git push origin main
```

---

## Commit Message Format

```
<type>(<scope>): <subject>

<optional body>

<optional footer>
```

### Types (Pick One)
- `feat:` - New feature
- `fix:` - Bug fix
- `test:` - Add/update tests
- `docs:` - Documentation
- `refactor:` - Refactor code
- `perf:` - Performance
- `chore:` - Maintenance

### Examples
```bash
git commit -m "feat(phase-1): add xUnit test project"
git commit -m "test(phase-1): add ShoppingCart integration tests"
git commit -m "fix(phase-2): resolve SQL connection timeout"
git commit -m "docs(phase-1): update README with progress"
git commit -m "refactor(phase-1): extract test base class"
```

---

## Branch Naming

```
<type>/<phase>-<description>

feat/phase-1-shopping-cart-tests
fix/phase-2-connection-leak
docs/phase-1-readme-update
test/phase-3-load-testing
refactor/phase-4-ef-migration
```

---

## When to Use Phase Branches

### Skip Phase Branch (Default)
✅ 1-5 features  
✅ < 2 weeks  
✅ Independent features

→ Create feature branches directly from main

### Use Phase Branch (Only When Needed)
✅ 5+ features  
✅ > 2 weeks  
✅ Breaking changes need testing together

→ Create phase branch, then feature branches from it

---

## Pull Request Checklist

- [ ] Branch name follows convention
- [ ] Commits use conventional format
- [ ] PR template filled out
- [ ] Linked to issue (if exists)
- [ ] Linked to milestone
- [ ] Self-reviewed on GitHub
- [ ] Tests pass locally
- [ ] Ready to squash and merge

---

## Merge Strategies

**Feature branches → Main**: Squash and merge  
**Phase branches → Main**: Merge commit  
**Never**: Rebase and merge

---

## Phase Complete Checklist

```bash
# 1. Tag release
git checkout main && git pull
git tag -a v1.0.0 -m "Phase 1: Foundation Complete

- Key accomplishment 1
- Key accomplishment 2
- Key accomplishment 3"

git push origin v1.0.0

# 2. Create GitHub Release
# Go to Releases → New release → Use tag v1.0.0

# 3. Update README.md
# Edit "Current Status" section
git add README.md
git commit -m "docs: update README for Phase 2 start"
git push origin main
```

---

## Common Git Commands

```bash
# Check status
git status

# See recent commits
git log --oneline -10

# Update branch with main
git checkout main && git pull
git checkout your-branch
git merge main

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Fix last commit message
git commit --amend -m "corrected message"

# Discard all changes
git reset --hard HEAD

# Delete local branch
git branch -d branch-name

# Delete remote branch
git push origin --delete branch-name
```

---

## PROJECT-LOG.md Template

```markdown
### 2025-11-15 - Feature Name Complete

**Merged PR #5**: feat/phase-1-feature-name → main

Brief description of what was accomplished.

**Commit**: abc123d
**Duration**: 2 days
**Tests Added**: 5
**Status**: ✅ Complete
**Next**: Start next feature
```

---

## Avoid These Mistakes

❌ Committing directly to main  
❌ Vague commit messages ("update", "fix")  
❌ Branches open > 3 days  
❌ Forgetting to update PROJECT-LOG  
❌ Not self-reviewing PRs on GitHub  
❌ Skipping PR template  
❌ Large commits (> 500 lines)

---

## Professional Standards

✅ Every PR has issue linked  
✅ Every commit follows conventional format  
✅ Self-review every PR on GitHub  
✅ Update PROJECT-LOG after every merge  
✅ Tag releases at phase boundaries  
✅ Keep branches short-lived (1-3 days)  
✅ Squash feature branches  
✅ Commit at least daily

---

## Quick Decision Tree

```
New work?
  ↓
Small (<4 hrs)?
  ↓ YES → Quick commit to main (rare)
  ↓ NO
  ↓
Create issue
  ↓
Create feature branch
  ↓
Work 1-3 days
  ↓
Push + PR
  ↓
Review + merge
  ↓
Update PROJECT-LOG
  ↓
Next feature
```

---

## Time Budget

**Setup (one time)**: 30 minutes  
**Per feature overhead**: 15 minutes  
**Documentation per PR**: 5 minutes  
**Weekly total**: ~1 hour

---

## V2 Philosophy

**Optimize for:**
- ⏱️  Speed (1-3 day PRs)
- 🧠 Simplicity (easy to remember)
- 👀 Appearance (professional to viewers)
- 📝 Sustainability (minimal maintenance)

**Not optimizing for:**
- Team coordination (solo dev)
- Complex workflows (unnecessary)
- Perfect history (good enough is fine)

---

## When Stuck, Remember

1. Keep it simple
2. Merge fast (1-3 days max)
3. Update PROJECT-LOG after merge
4. Use conventional commits
5. Self-review on GitHub

**That's 90% of what you need!**

---

## Resources

- **Full Strategy**: See git-strategy-v2.md
- **Implementation Guide**: See git-workflow-quick-start.md
- **Comparison**: See v1-vs-v2-comparison.md
- **This Cheat Sheet**: Keep handy during work

---

**Print this page and keep it at your desk!**
