# Legacy to Modern .NET Migration - Version 2

A comprehensive migration journey from .NET Framework 4.8 to .NET 9, transforming a legacy MVC Music Store application into a cloud-native architecture on Azure.

## 🎯 Project Purpose

This project serves as both a practical learning exercise for Azure development (AZ-204) and a portfolio demonstration of enterprise-grade application modernization. It documents the complete migration path from a traditional ASP.NET MVC application to a modern, containerized, cloud-native solution—preserving full functionality while progressively enhancing architecture, performance, and scalability.

**Why this matters:** Organizations worldwide face similar challenges migrating legacy .NET Framework applications. This project provides a reusable methodology, real-world problem-solving, and quantifiable outcomes that transfer directly to production modernization efforts.

## 📖 Project Origin and V2 Approach

### The Story Behind Version 2

This is the **second iteration** of this migration project, rebuilt with a clean intellectual property foundation:

**Phase 1 (Original)**: I began this migration using an existing MVC5 repository that adapted Microsoft's original MVC3 tutorial. After completing integration testing, I discovered licensing concerns that made it unsuitable for portfolio use.

**Phase 2 (V2 - This Project)**: I rebuilt the seed project from scratch using Microsoft's original MVC Music Store tutorial (MVC3) and adapted it to MVC5 myself. The new seed project is available at [steveLeVesconte/MvcMusicStore](https://github.com/steveLeVesconte/MvcMusicStore).

### Why Version 2 Will Be Faster

The first iteration wasn't wasted effort—it provided invaluable learning that accelerates V2:

- ✅ **Testing strategy proven**: Integration + unit test hybrid approach validated
- ✅ **Documentation patterns established**: Living docs vs. frozen planning docs
- ✅ **Technical challenges solved**: OWIN/Identity/EF migration paths understood
- ✅ **Azure patterns identified**: IaC templates, CI/CD patterns, deployment strategies
- ✅ **Risk areas mapped**: Known pitfalls in Phases 4-5 documented

**Expected timeline compression**: Phase 1 (Foundation) will compress from 3-4 weeks to ~1-2 weeks since testing patterns and tooling choices are already proven. Subsequent phases should similarly accelerate with established architectural patterns.

## 🗃️ Technical Evolution

### Starting Point (Seed Project)

- .NET Framework 4.8 + ASP.NET MVC 5
- Entity Framework 6.5.1 with LocalDB
- ASP.NET Identity 2.2.4 (with role-based authorization)
- OWIN middleware pipeline
- Single-instance in-memory session state
- jQuery 3.7.0, Bootstrap 5.2.3, Modernizr 2.8.3
- Manual deployment

### Target Architecture (Modern)

- .NET 9 + ASP.NET Core MVC
- Entity Framework Core with Azure SQL Database
- ASP.NET Core Identity + External OAuth (Microsoft, Google)
- Azure Container Apps with auto-scaling
- Distributed session state (Azure Cache for Redis)
- Azure Service Bus for async processing
- Azure API Management for RESTful APIs
- OpenTelemetry + Application Insights observability
- Infrastructure as Code (Bicep)
- Multi-stage CI/CD (GitHub Actions)

## 📊 Migration Phases

| Phase | Focus | Key Deliverables | Est. Duration |
|---|---|---|---|
| **Phase 0** | Planning | Repository structure, branching strategy, documentation framework | 3-5 days |
| **Phase 1** | Foundation | Test coverage (xUnit), Application Insights, local performance baselines | 1-2 weeks |
| **Phase 2** | Azure Migration | Azure SQL Database, App Service deployment, CI/CD pipeline, IaC (Bicep), security baseline | 2-3 weeks |
| **Phase 3** | Azure Validation | Smoke testing, performance benchmarking, load testing, environment analysis | 1 week |
| **Phase 4** | Platform Migration | .NET 9 conversion, EF Core migration, ASP.NET Core Identity, middleware pipeline | 3-4 weeks |
| **Phase 5** | Modern Auth | OAuth 2.0/PKCE, external identity providers, Azure Key Vault secrets | 1-2 weeks |
| **Phase 6** | Observability | OpenTelemetry tracing, structured logging, APM dashboards, health checks | 1-2 weeks |
| **Phase 7** | Scalability | Distributed caching, async I/O, connection pooling, resilience patterns | 2-3 weeks |
| **Phase 8** | API-First | RESTful Web API, API Management, Service Bus integration, distributed tracing | 2-3 weeks |
| **Phase 9** | Cloud Native | Docker containers, Azure Container Registry, Container Apps, managed identity | 2-3 weeks |
| **Phase 10** | DevOps Excellence | Multi-stage pipelines, automated security scanning, DORA metrics, compliance reporting | 1-2 weeks |

**Total Estimated Timeline**: 4-6 months (part-time development)

## 📈 Current Status

**Active Phase**: Phase 0 - Planning and Setup  
**Progress**: Repository initialized, branching strategy defined, documentation framework established  
**Last Updated**: November 7, 2025  
**Status**: Phase 0 approximately 70% complete

### Seed Project Technical Stack

The new seed project ([steveLeVesconte/MvcMusicStore](https://github.com/steveLeVesconte/MvcMusicStore)) is a clean-room implementation with:

**Core Framework:**
- .NET Framework 4.8
- ASP.NET MVC 5.2.9
- Entity Framework 6.5.1

**Authentication & Security:**
- ASP.NET Identity 2.2.4 (Core, EntityFramework, Owin)
- OWIN 4.2.3 middleware pipeline
- Cookie-based authentication

**Front-End:**
- Bootstrap 5.2.3
- jQuery 3.7.0
- jQuery Validation 1.19.5
- Modernizr 2.8.3

**Key Features:**
- Role-based authorization (Admin/User)
- Shopping cart with session state
- E-commerce checkout workflow
- Album catalog management (CRUD operations)
- Seeded with test data

**Default Admin Credentials** (for local testing):
- Email: `admin@musicstore.com`
- Password: `Admin123!`

See the [seed project repository](https://github.com/steveLeVesconte/MvcMusicStore) for complete setup instructions and technical details.

## 🎓 Skills Demonstrated

### Azure Services (AZ-204 Aligned)

- **Compute:** App Service, Azure Container Apps
- **Storage:** Azure SQL Database, Azure Cache for Redis
- **Security:** Key Vault, Managed Identity, OAuth 2.0/PKCE
- **Integration:** API Management, Service Bus
- **Monitoring:** Application Insights, Azure Monitor, OpenTelemetry
- **DevOps:** Azure DevOps, GitHub Actions, Infrastructure as Code (Bicep)

### Software Engineering Practices

- **Migration Methodology:** Incremental platform upgrades with continuous validation
- **Testing Strategy:** Unit testing, integration testing, load testing
- **Observability:** Distributed tracing, structured logging, business metrics
- **Security:** Secrets management, dependency scanning, SAST integration, baseline establishment
- **Performance:** Baseline capture, comparative analysis, optimization validation
- **Documentation:** Decision rationale, troubleshooting guides, runbooks
- **Version Control:** Trunk-based development, conventional commits, branch protection

### New Skills Acquired Through This Project

Coming into this project, I had no prior experience with:
- **Security Scanning:** SAST/SCA tools, vulnerability management workflows
- **Secrets Management:** Azure Key Vault, managed identities, production secret handling
- **Modern Git Workflows:** Professional branching strategies, PR templates, commit conventions
- **Infrastructure as Code:** Bicep templates, declarative infrastructure
- **Container Orchestration:** Docker multi-stage builds, Azure Container Apps
- **Distributed Systems:** Service Bus patterns, distributed tracing, cache-aside patterns

These areas represent net-new learning captured and documented throughout the migration phases.

## 🔐 Security Approach

This project demonstrates security-conscious development practices throughout the migration journey, using freely available tools to establish baselines and track improvements.

**Important Context:** This is an educational baseline approach suitable for learning and portfolio demonstration—not a comprehensive enterprise security program. The goal is to demonstrate the value of establishing measurable security baselines before major migrations and tracking improvements afterward.

### Phase 2: Security Baseline (Framework 4.8 + Azure)

At the end of Phase 2, before platform migration begins, a security baseline is established:

- **Dependency Vulnerability Scanning:** Using `dotnet list package --vulnerable` and GitHub Dependabot to identify known CVEs in NuGet packages
- **SAST Analysis:** SonarCloud integration to detect code-level security hotspots (SQL injection risks, XSS vulnerabilities, weak cryptography)
- **Secrets Detection:** GitHub Secret Scanning to prevent credential exposure
- **Documentation:** Baseline report capturing all findings for comparison post-migration

**Rationale:** Establishing a security baseline before the .NET 9 migration allows us to quantify security improvements and catch issues before they're obscured by the complexity of platform changes. This "before snapshot" becomes valuable evidence of migration benefits.

### Phase 5: Secrets Management (Production)

- **Azure Key Vault:** Connection strings, API keys, OAuth client secrets
- **Managed Identity:** Password-less authentication between Azure services
- **Environment Separation:** Dev/staging/production secret isolation

### Phase 10: Security Validation & Metrics

After completing the .NET 9 migration and cloud-native transformation:

- **Re-scan:** Run the same security tools against the modernized codebase
- **Comparison:** Document vulnerability reduction (Framework 4.8 → .NET 9)
- **CI/CD Integration:** Automated security scans as quality gates
- **Compliance:** Security scan results archived for audit purposes

**Expected Outcome:** Measurable security posture improvement demonstrated through before/after vulnerability counts, with all high/critical issues resolved.

### Tools & Budget

All security tooling uses free tiers suitable for public repositories:

- **GitHub Dependabot:** FREE (automatic)
- **.NET CLI Vulnerability Scanning:** FREE (built-in)
- **SonarCloud:** FREE (public repositories)
- **GitHub Secret Scanning:** FREE (public repositories)
- **Azure Key Vault:** ~$1-5/month (only actual cost)

**Time Investment:** ~1 day for Phase 2 baseline, ~2-3 days for Phase 10 comprehensive security implementation.

## 📈 Success Metrics

Each phase captures quantifiable outcomes:

- **Performance:** Response times, throughput, cache hit ratios (local → Azure → Container Apps)
- **Quality:** Test coverage %, uptime %, migration success rate
- **Security:** Vulnerability trends (baseline → post-migration), security scan pass rate, secrets management compliance
- **Scalability:** Auto-scaling validation, load testing results
- **DevOps:** DORA metrics (deployment frequency, lead time, MTTR)

**Overall Success Criteria:**
- ✅ Complete functional parity maintained throughout
- ✅ Zero data loss across all migrations
- ✅ Measurable performance improvements documented
- ✅ Security posture improvement demonstrated (Framework 4.8 baseline → .NET 9)
- ✅ All security scans passed (no high/critical vulnerabilities in final state)
- ✅ Comprehensive migration playbook for reusability

## 🚀 Getting Started

### Prerequisites

- Visual Studio 2022 or later
- .NET Framework 4.8 SDK (for seed project)
- .NET 9 SDK (for modern version - Phase 4+)
- SQL Server LocalDB
- Azure subscription (for Phases 2+)
- Docker Desktop (for Phase 9+)

### Quick Start with Seed Project

For a complete setup guide, see the [seed project repository](https://github.com/steveLeVesconte/MvcMusicStore).

**Abbreviated steps:**

```bash
git clone https://github.com/steveLeVesconte/MvcMusicStore.git
cd MvcMusicStore
# Open MvcMusicStore.sln in Visual Studio
# Press F5 to run
# Login with admin@musicstore.com / Admin123!
```

### Working with This Migration Project

This repository contains:

```
├── docs/                    # Phase documentation and migration guides
├── src/                     # Application source code
├── tests/                   # Test projects
├── infrastructure/          # Bicep templates and deployment scripts
├── .github/workflows/       # CI/CD pipeline definitions
├── PROJECT-LOG.md          # Development log and decisions
├── project-outline.md      # Detailed phase breakdown
└── README.md               # This file
```

### Branch Strategy: Simplified Trunk-Based Development

**Core Principles:**
1. **Main branch protection**: Always stable, deployable code
2. **Short-lived feature branches**: Merge quickly (1-3 days max)
3. **Phase branches as milestones**: Only when needed for major work
4. **No sub-sub-branches**: Maximum two levels of branching

**Branch Naming Convention:**

Format: `<type>/<phase>-<short-description>`

Types:
- `feat/` - New features or capabilities
- `fix/` - Bug fixes
- `docs/` - Documentation only
- `refactor/` - Code refactoring without behavior change
- `test/` - Adding or updating tests
- `chore/` - Maintenance tasks (dependencies, config)

Examples:
- `feat/phase-1-integration-tests`
- `fix/phase-4-ef-migration-bug`
- `docs/phase-2-deployment-guide`

## 📚 Documentation

- **PROJECT-LOG.md** - [need link here] - Chronological development log with decisions and challenges
- **project-outline.md** - [need link here] - Comprehensive phase-by-phase migration plan
- **[Seed Project Repository](https://github.com/steveLeVesconte/MvcMusicStore)** - Clean-room MVC5 implementation

### Documentation Philosophy

**Living Documents** (always current):
- PROJECT-LOG.md - Daily progress and decision journal
- README.md - Project overview and current status
- KNOWN-LIMITATIONS.md - [need link here] - Known issues and scope boundaries

**Frozen Planning Documents** (historical reference):
- Phase planning documents - Captured during Phase 0, preserved as historical context
- Initial estimates and approaches - Shows evolution of thinking during implementation

**Source of Truth**:
- Git commit history and tags
- GitHub Issues and Pull Requests
- Phase-specific README files in `docs/phase-N/`

## 🤖 AI-Assisted Development

This project extensively leverages AI tooling and prompt engineering throughout the development lifecycle:

- **Project Planning:** Architecture decisions, technology stack selection, phase breakdown
- **Documentation:** Generation and review of technical documentation, migration guides
- **Test Development:** Test case identification, edge case discovery, test data generation
- **Problem Solving:** Debugging assistance, error analysis, solution research
- **Learning Acceleration:** Real-time answers to knowledge gaps, concept clarification
- **Code Review:** Best practice validation, security review, performance analysis

This AI-assisted approach is a core part of my modern development workflow and represents a practical skill in prompt engineering for technical work. The prompts themselves are not included in this repository, but the outcomes—comprehensive documentation, thorough test coverage, and well-architected solutions—demonstrate the effectiveness of this methodology.

## 🎯 Who This Is For

**Hiring Managers:** Demonstrates practical Azure development skills, modern DevOps practices, and the ability to navigate complex technical migrations while maintaining production stability.

**Technical Interviewers:** Provides concrete examples of architectural decision-making, problem-solving approaches, and hands-on experience with enterprise modernization challenges.

**Developers Planning Migrations:** Offers a reusable methodology with detailed implementation guidance, troubleshooting strategies, and lessons learned for similar .NET Framework to .NET Core/9 migrations.

**Future Me:** Serves as a technical reference, keeps the project organized, and provides material for technical discussions about cloud-native transformation.

## 📄 Version 2 Improvements

This second iteration incorporates lessons learned:

1. **Clean IP Foundation**: Built on Microsoft's tutorial with explicit license
2. **Proven Testing Strategy**: Integration + unit test hybrid from day one
3. **Sustainable Documentation**: Clear living vs. frozen document tiers
4. **Risk Mitigation**: Known pitfalls documented before Phase 1
5. **Accelerated Timeline**: Established patterns and tooling choices
6. **Professional Standards**: Repository structure follows enterprise best practices
7. **AI-Accelerated Development**: Leveraging prompt engineering for efficiency

## 🤝 Contributing

This is primarily a learning and portfolio project, but suggestions and feedback are welcome! For major changes, please open an issue first to discuss what you would like to change.

## 📝 License

MIT License - See LICENSE file for details.

This project is built upon Microsoft's MVC Music Store tutorial, reimplemented as a clean-room MVC5 application. The seed project source is available at [steveLeVesconte/MvcMusicStore](https://github.com/steveLeVesconte/MvcMusicStore).

**Original Tutorial**: [Microsoft - MVC Music Store Tutorial](https://learn.microsoft.com/en-us/aspnet/mvc/overview/older-versions/mvc-music-store/)

## 🙏 Acknowledgments

- Microsoft's MVC Music Store tutorial (MVC3 original)
- Microsoft's .NET migration documentation and tooling
- Azure Developer community for best practices and patterns

---

**Project Repository**: [legacy-to-modern-dotnet-migration-v2](https://github.com/steveLeVesconte/legacy-to-modern-dotnet-migration-v2)  
**Migration Tool**: Microsoft .NET Upgrade Assistant  
**Reference Architecture**: Microsoft Cloud Adoption Framework for Azure

_Note: This is Version 2 of the migration project, rebuilt with a clean-room seed implementation based directly on Microsoft's tutorial._