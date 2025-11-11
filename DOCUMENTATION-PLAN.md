# Documentation Plan

> **Purpose**: Your organizational guide for managing project documentation across all phases.  
> **Audience**: You (primary), future contributors  
> **Status**: Living document - update as documentation needs evolve

## 📊 Documentation Time Budget

**Daily** (~10-15 min): PROJECT-LOG.md updates  
**Weekly** (~30-45 min): GitHub Issues review, KNOWN-LIMITATIONS.md updates  
**Per Phase** (~2-3 hours): README.md, phase docs, CHANGELOG, retrospective  
**Total**: ~1 hour/week average

---

## 🔴 LIVING DOCUMENTS (Update Regularly)

### README.md
**Location**: `/README.md`  
**What It Does**: Your "elevator pitch" - first impression for hiring managers and visitors  
**Update When**: Phase transitions, major milestones, status changes  
**Inception**: Phase 0  
**Template**: Current version is good - keep status section current

**Quick Maintenance Checklist**:
- [ ] Current phase and status accurate?
- [ ] Progress percentage reflects reality?
- [ ] Skills demonstrated list current?
- [ ] Links working?

---

### PROJECT-LOG.md
**Location**: `/PROJECT-LOG.md`  
**What It Does**: Your decision journal and daily work log - captures "what and why"  
**Update When**: Daily or per work session (10-15 min)  
**Inception**: Phase 0  

**Entry Template**:
```markdown
### YYYY-MM-DD | [Brief Title of Work]

**Current Branch**: `type/phase-N-description`

**Work Completed**
- [x] Task completed with outcome
- [x] Decision made with rationale
- [ ] Task started but not finished

**Key Decisions Made**
- **Decision Topic**: Choice made and why (with alternatives considered)

**Blockers/Issues**
- [Issue #N] Description or "None"

**Time Investment**
- Estimated: X hours
- Actual: Y hours

**Next Steps**
- [ ] Immediate next task
- [ ] Following task

**Phase N Status**: 🚧 IN PROGRESS | ✅ COMPLETE | ⚠️ BLOCKED
```

**Top Section Template** (Always Keep Current):
```markdown
## Active Work
**Current Phase**: Phase N: Phase Name  
**Current Branch**: type/phase-N-description  
**Next Milestone**: Complete phase-N-x or Merge PR #N  
**Blocked On**: [Issue #N] or Nothing currently  

**Phase N Status**: 🚧 IN PROGRESS
```

---

### KNOWN-LIMITATIONS.md
**Location**: `/KNOWN-LIMITATIONS.md`  
**What It Does**: Prevents scope creep, shows professional judgment about trade-offs  
**Update When**: Discover issues, defer features, resolve limitations  
**Inception**: Phase 0 (start empty, populate as discovered)  

**Template**:
```markdown
# Known Limitations

> **Last Updated**: YYYY-MM-DD  
> **Purpose**: Transparent inventory of current constraints and deferred work

## 🚧 Current Limitations

### [Category: Technical Debt / Performance / Security / Feature Gap]

**Issue**: Brief description  
**Impact**: Who/what is affected  
**Workaround**: Current mitigation if any  
**Deferred To**: Phase 5a / Post-migration / Never (with rationale)  
**Discovered**: Phase N, YYYY-MM-DD

---

## ✅ Resolved Limitations

### [Category]
**Issue**: What was wrong  
**Resolution**: How it was fixed  
**Resolved**: Phase N, YYYY-MM-DD
```

**Categories to Use**:
- Technical Debt
- Performance Issues
- Security Concerns
- Feature Gaps
- Browser Compatibility
- Testing Gaps
- Documentation Gaps

---

### CHANGELOG.md (Auto-Generated)
**Location**: `/CHANGELOG.md`  
**What It Does**: Version history from git tags and conventional commits  
**Update When**: Automatic via tooling  
**Inception**: Phase 1 (when first tag created)  
**Tool**: Consider using `standard-version` or `semantic-release`

---

### QUICK-REFERENCE.md
**Location**: `/QUICK-REFERENCE.md`  
**What It Does**: Your personal cheat sheet for daily commands and conventions  
**Update When**: You find yourself looking something up repeatedly  
**Inception**: Phase 0  

**Template**:
```markdown
# Developer Quick Reference

> Personal cheat sheet for project conventions. See CONTRIBUTING.md for rationale.

## Branch Naming
feat/phase-N-description
fix/phase-N-description
docs/phase-N-description
test/phase-N-description
refactor/phase-N-description
chore/phase-N-description

## Commit Format
type(scope): brief description

Types: feat, fix, docs, test, refactor, chore, perf

## Daily Workflow
```bash
# Start work
git checkout main && git pull
git checkout -b feat/phase-N-description

# During work
git add . && git commit -m "feat(scope): description"

# End work
git push origin feat/phase-N-description
# Create PR on GitHub
```

## Documentation Schedule
- **Daily**: PROJECT-LOG.md (10 min)
- **Weekly**: Review KNOWN-LIMITATIONS.md
- **Phase End**: README status, phase-NN/README.md, git tag

## When to Create...
- **ADR**: Significant technical decision
- **Issue**: Task >2 hours or needs discussion
- **Branch**: Any work touching production code
- **TROUBLESHOOTING.md**: When phase has >3 complex problems

## Common Git Fixes
```bash
# Forgot branch before starting
git stash && git checkout -b feat/phase-N-name && git stash pop

# Wrong branch name
git branch -m old-name new-name

# Update branch from main
git checkout main && git pull
git checkout feature-branch && git rebase main
```

## File Locations
- Tests: `/tests/MvcMusicStore.Tests/`
- Phase Docs: `/docs/phase-NN/`
- ADRs: `/docs/adr/`
- Infrastructure: `/infrastructure/`
- Workflows: `/.github/workflows/`
```

---

## 🟡 PHASE-SPECIFIC LIVING DOCUMENTS

### docs/phase-NN/README.md
**Location**: `/docs/phase-NN/README.md` (where N = phase number)  
**What It Does**: Captures actual implementation approach and outcomes for each phase  
**Update When**: Create at phase start, update during phase, finalize at phase end  
**Inception**: Create when starting each phase (Phase 1+)  

**Template**:
```markdown
# Phase N: [Phase Name]

> **Status**: 🚧 IN PROGRESS | ✅ COMPLETE  
> **Started**: YYYY-MM-DD  
> **Completed**: YYYY-MM-DD  
> **Version**: vN.0.0

## Overview
Brief description of what this phase accomplishes.

## Goals
- [ ] Primary objective 1
- [ ] Primary objective 2
- [ ] Primary objective 3

## Acceptance Criteria
- [ ] Specific measurable outcome 1
- [ ] Specific measurable outcome 2
- [ ] All tests passing
- [ ] Documentation updated

## Implementation Approach

### What We Actually Did
(Not the plan - the reality. Fill this in as you go.)

### Key Decisions
- **Decision 1**: What we chose and why → See ADR-NNN
- **Decision 2**: What we chose and why

### Deviations from Original Plan
- **Original Plan**: What project-outline.md said
- **Actual Approach**: What we did instead
- **Rationale**: Why we changed course

## Challenges Encountered

### Challenge 1: [Title]
**Problem**: Description  
**Root Cause**: What was really wrong  
**Solution**: How we fixed it  
**Prevention**: How to avoid in future phases

## Lessons Learned

### Technical Lessons
- Lesson 1
- Lesson 2

### Process Lessons
- Lesson 1
- Lesson 2

## Metrics

### Performance (if applicable)
- Metric 1: Before → After
- Metric 2: Before → After

### Time Investment
- **Estimated**: X weeks
- **Actual**: Y weeks
- **Variance**: +/- Z days (rationale)

## Artifacts Created
- ADR-NNN: Decision title
- Tests: X unit tests, Y integration tests
- Documentation: List key docs
- Infrastructure: Bicep templates, workflows, etc.

## Next Phase Prerequisites
- [ ] Item 1 must be complete before Phase N+1
- [ ] Item 2 must be complete before Phase N+1

## Related Documentation
- ADR-NNN: [Decision Title](../adr/NNN-decision-title.md)
- [TROUBLESHOOTING.md](./TROUBLESHOOTING.md) (if exists)
- PROJECT-LOG entries: YYYY-MM-DD through YYYY-MM-DD
```

---

### docs/phase-NN/TROUBLESHOOTING.md
**Location**: `/docs/phase-NN/TROUBLESHOOTING.md`  
**What It Does**: Captures problems and solutions specific to this phase  
**Update When**: Encounter non-trivial problems (>1 hour to solve)  
**Inception**: Create as needed (especially Phases 4-5)  

**When to Create**: 
- Phase has >3 complex problems worth documenting
- Problems will likely recur or help others
- Not needed for simple phases

**Template**:
```markdown
# Phase N Troubleshooting Guide

> **Purpose**: Solutions to problems encountered during Phase N  
> **Last Updated**: YYYY-MM-DD

## Problem: [Brief Title]

**Symptom**: What you saw (error message, behavior)  
**Environment**: Where it occurred (local, Azure, specific config)  
**Root Cause**: What was actually wrong  
**Solution**: Step-by-step fix  
**Prevention**: How to avoid this in future  
**References**: Links to Stack Overflow, docs, etc.

---

## Problem: [Next Problem Title]
[Same structure...]
```

---

## 🔵 FROZEN PLANNING DOCUMENTS (Write Once)

### project-outline.md
**Location**: `/project-outline.md`  
**What It Does**: Original phase planning from Phase 0 - shows planning capability  
**Update When**: Never after Phase 0 (mark as FROZEN)  
**Inception**: Phase 0  

**Header to Add**:
```markdown
> **DOCUMENT STATUS**: ❄️ FROZEN PLANNING DOCUMENT  
> Created: Phase 0, YYYY-MM-DD  
> This document is NOT updated during execution.  
> See PROJECT-LOG.md for actual decisions and deviations.  
> See docs/phase-NN/README.md for execution details.
```

---

### work-execution-plan.md
**Location**: `/work-execution-plan.md`  
**What It Does**: Detailed Phase 0 task breakdown - more granular than project-outline  
**Update When**: Never after Phase 0 (mark as FROZEN)  
**Inception**: Phase 0  

**Use Same FROZEN Header as project-outline.md**

---

### TESTING-STRATEGY.md
**Location**: `/TESTING-STRATEGY.md`  
**What It Does**: Explains test approach philosophy and coverage decisions  
**Update When**: Only for major strategy pivots (rare)  
**Inception**: Phase 1b  

**Template**:
```markdown
# Testing Strategy

> **Status**: ❄️ SEMI-FROZEN (minor updates allowed for major pivots)  
> **Created**: Phase 1b  
> **Last Updated**: YYYY-MM-DD

## Philosophy
Why we test this way and what we optimize for.

## Test Categories

### Integration Tests
**Purpose**: Behavioral baseline, end-to-end validation  
**Characteristics**: Use real DbContext, prove current behavior  
**Coverage Target**: Critical business workflows  
**Tools**: xUnit, TestServer

### Unit Tests
**Purpose**: Fast feedback, isolated logic testing  
**Characteristics**: Mocked dependencies, survive Phase 4 migration  
**Coverage Target**: Business logic, calculations, validations  
**Tools**: xUnit, Moq

## Coverage Priorities
1. Shopping cart logic (highest business risk)
2. Checkout workflow
3. Authentication flows
4. Admin CRUD operations

## Patterns and Conventions
- Test naming: MethodName_Scenario_ExpectedBehavior
- Arrange-Act-Assert structure
- One assertion per test (where practical)

## When NOT to Test
- Simple property getters/setters
- Framework code
- UI presentation logic (until Phase 10 if needed)
```

---

### dependency-inventory.md
**Location**: `/dependency-inventory.md`  
**What It Does**: Snapshot of Framework 4.8 tech stack before migration  
**Update When**: Never after Phase 1 (mark as FROZEN)  
**Inception**: Phase 1  

**Template**:
```markdown
# Dependency Inventory

> **Status**: ❄️ FROZEN SNAPSHOT  
> **Captured**: Phase 1, YYYY-MM-DD  
> **Purpose**: Baseline for migration impact analysis

## Framework
- .NET Framework: 4.8
- ASP.NET MVC: 5.2.9
- Entity Framework: 6.5.1

## Authentication
- ASP.NET Identity: 2.2.4
- OWIN: 4.2.3

## Front-End
- Bootstrap: 5.2.3
- jQuery: 3.7.0
- Modernizr: 2.8.3

## Known Vulnerabilities
(From `dotnet list package --vulnerable`)
- Package: Version (CVE-YYYY-NNNNN) - Severity: Low/Medium/High

## Migration Impact Notes
- OWIN → ASP.NET Core middleware pipeline
- Identity 2.2.4 → Identity Core (breaking changes expected)
- EF6 → EF Core (some patterns incompatible)
```

---

## 🟢 PROCESS/STANDARDS DOCUMENTS

### CONTRIBUTING.md
**Location**: `/CONTRIBUTING.md`  
**What It Does**: External-facing guidelines for contributions and standards  
**Update When**: Process improvements discovered  
**Inception**: Phase 0  

**Keep It**: ~3-5KB, professional tone, includes rationale  
**Sections**: Goals, ways to contribute, workflow, PR guidelines, code style, scope control

---

### SECURITY.md
**Location**: `/SECURITY.md`  
**What It Does**: Security approach and vulnerability reporting  
**Update When**: Major security approach changes  
**Inception**: Phase 2  

**Template**:
```markdown
# Security Policy

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| vN.x.x  | :white_check_mark: |
| < vN.0  | :x:                |

## Security Approach

### Phase 2: Security Baseline
- Dependency scanning: `dotnet list package --vulnerable`
- SAST: SonarCloud integration
- Secrets detection: GitHub Secret Scanning

### Phase 5: Secrets Management
- Azure Key Vault for production secrets
- Managed identities for Azure resources
- No secrets in code or config files

## Reporting a Vulnerability

**Educational Project Notice**: This is a learning/portfolio project. Security issues are addressed on a best-effort basis.

**How to Report**:
1. Open a GitHub Issue with [SECURITY] prefix
2. Or contact via LinkedIn: [your-profile]

**Response Time**: Within 48-72 hours

**What to Include**:
- Description of vulnerability
- Steps to reproduce
- Potential impact
- Suggested remediation (if known)
```

---

## 📋 ARCHITECTURE DECISION RECORDS

### docs/adr/NNNN-decision-title.md
**Location**: `/docs/adr/` (numbered sequentially)  
**What It Does**: Immutable record of significant technical decisions  
**Update When**: Never (create new ADR to supersede)  
**Inception**: First significant decision (likely Phase 1)  

**Naming Convention**: `NNNN-decision-title.md` (e.g., `0001-use-xunit-over-mstest.md`)

**Template** (Using MADR format):
```markdown
# [Number]. [Title in Sentence Case]

Date: YYYY-MM-DD

## Status

[Proposed | Accepted | Deprecated | Superseded by ADR-NNNN]

## Context

What is the issue we're trying to solve? What are the constraints? What alternatives did we consider?

## Decision

What did we decide to do?

## Consequences

### Positive
- Benefit 1
- Benefit 2

### Negative
- Trade-off 1
- Trade-off 2

### Neutral
- Other impact 1

## References
- Link to relevant documentation
- Link to GitHub issue/PR
- External articles/resources
```

**When to Create an ADR**:
- Choosing test framework (xUnit vs MSTest)
- Choosing integration test approach
- Selecting deployment strategy
- Architectural pattern decisions
- Technology stack choices
- Major library/framework decisions

**When NOT to Create an ADR**:
- Routine implementation choices
- Temporary workarounds
- Simple bug fixes
- Obvious choices with no alternatives

---

## 🗂️ Directory Structure

```
/
├── README.md                           # Living - update at phase transitions
├── PROJECT-LOG.md                      # Living - daily updates
├── KNOWN-LIMITATIONS.md                # Living - as issues discovered
├── CHANGELOG.md                        # Auto-generated
├── QUICK-REFERENCE.md                  # Living - your personal cheat sheet
├── DOCUMENTATION-PLAN.md               # This file - update as needs evolve
├── CONTRIBUTING.md                     # Semi-static - Phase 0, minor updates
├── SECURITY.md                         # Semi-static - Phase 2, minor updates
├── project-outline.md                  # Frozen - Phase 0
├── work-execution-plan.md              # Frozen - Phase 0
├── TESTING-STRATEGY.md                 # Semi-frozen - Phase 1b
├── dependency-inventory.md             # Frozen - Phase 1
│
├── docs/
│   ├── phase-00/
│   │   └── README.md                   # Phase 0 outcomes
│   ├── phase-01/
│   │   ├── README.md                   # Phase 1 outcomes
│   │   └── TROUBLESHOOTING.md          # If needed
│   ├── phase-02/
│   │   ├── README.md
│   │   └── TROUBLESHOOTING.md
│   ├── [phase-03 through phase-10]/
│   │
│   └── adr/
│       ├── 0001-use-xunit-over-mstest.md
│       ├── 0002-integration-test-hybrid.md
│       └── [additional ADRs...]
│
├── src/                                # Application code
├── tests/                              # Test projects
├── infrastructure/                     # Bicep, deployment scripts
└── .github/
    └── workflows/                      # CI/CD pipelines
```

---

## 📅 Documentation Workflow by Phase

### Phase 0: Planning
**Create**:
- [ ] README.md (initial version)
- [ ] PROJECT-LOG.md (with template)
- [ ] CONTRIBUTING.md
- [ ] project-outline.md (mark FROZEN at phase end)
- [ ] work-execution-plan.md (mark FROZEN at phase end)
- [ ] KNOWN-LIMITATIONS.md (empty to start)
- [ ] QUICK-REFERENCE.md
- [ ] DOCUMENTATION-PLAN.md (this file)
- [ ] docs/phase-00/README.md (at phase end)

### Phase 1: Foundation & Testing
**Create**:
- [ ] TESTING-STRATEGY.md (Phase 1b)
- [ ] dependency-inventory.md (mark FROZEN at phase end)
- [ ] docs/phase-01/README.md
- [ ] First ADR (e.g., 0001-use-xunit-over-mstest.md)
- [ ] docs/adr/ directory

**Update Daily**:
- [ ] PROJECT-LOG.md

**Update at Phase End**:
- [ ] README.md (status, progress)
- [ ] docs/phase-01/README.md (finalize)
- [ ] CHANGELOG.md (via git tag v1.0.0)

### Phase 2: Azure Migration
**Create**:
- [ ] SECURITY.md
- [ ] docs/phase-02/README.md
- [ ] docs/phase-02/TROUBLESHOOTING.md (if complex issues)
- [ ] ADRs for deployment decisions

**Update Daily**:
- [ ] PROJECT-LOG.md

**Update Weekly**:
- [ ] KNOWN-LIMITATIONS.md (Azure-specific constraints)

**Update at Phase End**:
- [ ] README.md
- [ ] docs/phase-02/README.md
- [ ] CHANGELOG.md (via git tag v2.0.0)

### Phases 3-10: Continue Pattern
**Each Phase**:
- [ ] Create docs/phase-NN/README.md at start
- [ ] Update PROJECT-LOG.md daily
- [ ] Create ADRs for significant decisions
- [ ] Create TROUBLESHOOTING.md if >3 complex problems
- [ ] Update KNOWN-LIMITATIONS.md as issues discovered
- [ ] Finalize phase README at completion
- [ ] Update main README.md
- [ ] Create git tag (vN.0.0)

---

## 🎯 Quick Decision Trees

### "Should I create an ADR?"
```
Is this a significant technical decision? ───No──> Don't create ADR
    │
    Yes
    │
Are there multiple viable alternatives? ───No──> Consider skipping (obvious choice)
    │
    Yes
    │
Will future you/others wonder "why this way"? ───Yes──> CREATE ADR
```

### "Should I create a TROUBLESHOOTING doc?"
```
Did I spend >1 hour solving this? ───No──> Just note in PROJECT-LOG
    │
    Yes
    │
Is this problem likely to recur? ───No──> Just note in PROJECT-LOG
    │
    Yes
    │
Does this phase already have 3+ problems documented? ───Yes──> ADD TO TROUBLESHOOTING
    │                                                      │
    No                                                     │
    │                                                      │
    └──────> Create TROUBLESHOOTING.md ◄───────────────────
```

### "Where does this information go?"
```
Daily work and decisions? ──────────────────> PROJECT-LOG.md
Current project status? ────────────────────> README.md
Out of scope / Won't fix? ──────────────────> KNOWN-LIMITATIONS.md
Technical decision rationale? ──────────────> docs/adr/NNNN-title.md
Phase-specific outcomes? ───────────────────> docs/phase-NN/README.md
Problem + solution in detail? ──────────────> docs/phase-NN/TROUBLESHOOTING.md
Process convention? ─────────────────────────> QUICK-REFERENCE.md or CONTRIBUTING.md
```

---

## ✅ Weekly Documentation Health Check

**Every Friday** (10 minutes):

- [ ] PROJECT-LOG.md top section reflects current work?
- [ ] README.md status matches reality?
- [ ] KNOWN-LIMITATIONS.md has new discoveries from this week?
- [ ] Any ADRs needed for decisions made this week?
- [ ] QUICK-REFERENCE.md needs updates based on what you looked up repeatedly?
- [ ] GitHub Issues in sync with actual blockers?

---

## 🚫 Documentation Anti-Patterns to Avoid

**Don't**:
- ❌ Maintain duplicate information in multiple places
- ❌ Create docs that replicate what git history shows
- ❌ Over-document temporary decisions or throwaway code
- ❌ Copy-paste content between documents (link instead)
- ❌ Create elaborate plans that won't be maintained
- ❌ Let documents get >30 days out of date (except FROZEN docs)

**Do**:
- ✅ Single source of truth for each piece of information
- ✅ Use git history + tags for detailed change tracking
- ✅ Link between related documents
- ✅ Mark documents as FROZEN when they become historical
- ✅ Keep living documents current (set reminders if needed)

---

## 🔄 Migration from V1 to V2

If importing documentation from previous version:

1. **Review each V1 doc against this plan**
2. **Mark as FROZEN if it's historical reference**
3. **Update living docs to current reality**
4. **Discard duplicative or obsolete docs**
5. **Follow new templates going forward**

---

## 📝 Notes

- This plan optimizes for **1 hour/week maintenance** after initial setup
- **Git history + Issues + PRs** = your detailed audit trail (don't duplicate)
- **When in doubt**: Log it in PROJECT-LOG.md first, promote to dedicated doc if it becomes important
- **Templates are guides**: Adapt to your needs, but keep them consistent
- **Review this plan** after Phase 2 and adjust based on what's actually working

---

**Last Updated**: [Insert date when you finalize this]  
**Next Review**: After Phase 2 completion