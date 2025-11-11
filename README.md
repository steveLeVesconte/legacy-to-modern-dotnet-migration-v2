# Legacy to Modern .NET Migration - Version 2

A comprehensive migration journey from .NET Framework 4.8 to .NET 9, transforming a legacy MVC Music Store application into a cloud-native architecture on Azure.

## 🎯 Project Purpose

First and foremost, this is a learning laboratory. I am creating it because I learn better by having challenging, near-real projects than from spoon-fed tutorials. Secondarily, it is a portfolio project, and I truly hope that if you are a hiring manager or talent scout, you will find it interesting. If I am successful, this project may serve as a model for other developers who face the challenge of a migration like this, but even better if it serves as a model for learning design.

By design, it is extremely challenging, requiring me to learn many new skills simultaneously and practice them repeatedly, including innumerable practice iterations that would not be possible in a production project.

### Why This Approach?

**This project intentionally models enterprise migration practices at scale**, not a greenfield rewrite. While the MVC Music Store is small enough to rebuild from scratch in .NET 9 in a fraction of the time, **that's not the point**. The point is that even though this is a tiny amount of functionality, migrating it from MVC5 and Framework 4.8 to .NET 9 is approximately the same process as would be applied if it were a much more substantial enterprise app.

### Intentional Investment Areas

This project invests heavily in practices that would be essential for enterprise migrations:

**Baseline Measurement & Observability**

- Application Insights integration before migration begins - Learning design note: by actually recording baseline and changes throughout the phases of the project, Application Insights knowledge is grounded in real-ish experience. This applies to all of the testing and performance metrics in the project.
- Performance metrics captured at each phase boundary
- Comparative analysis to prove no degradation
- *Rationale:* Enterprises need proof that migrations don't harm production workloads

**Comprehensive Testing**

- Integration test suite established before platform changes
- Test coverage as a safety net during breaking changes
- *Rationale:* Confidence to refactor with impunity

**Professional Process & Documentation**

- Phase-by-phase planning with clear decision points
- Git workflow practicing team collaboration patterns
- Living documentation capturing challenges and solutions
- *Rationale:* Large teams need reproducible processes and knowledge transfer

**Security & Compliance Tracking**

- SAST/SCA baselines established pre-migration
- Post-migration comparison showing security improvements
- *Rationale:* Regulatory requirements demand measurable security posture

### Learning Through Realistic Constraints

This project prioritizes **learning transferable enterprise patterns** over raw development speed. The goal is not to ship the Music Store as efficiently as possible—it's to demonstrate the methodology for safely migrating **important legacy applications** when the stakes are high and the margin for error is zero.

## 📖 Project Origin and V2 Approach

### The Story Behind Version 2

This is the **second iteration** of this migration project, rebuilt with a clean intellectual property foundation:

**Phase 1 (Original)**: I began this migration using an existing MVC5 repository that adapted Microsoft's original MVC3 tutorial. After completing integration testing, I discovered licensing concerns that made it unsuitable for portfolio use. (And here you see what I mean about iterations. A significant failure requires me to drop back 2 weeks and re-start. Extravagantly expensive but rich learning potential.)

**Phase 2 (V2 - This Project)**: I rebuilt the seed project from scratch using Microsoft's original MVC Music Store tutorial (MVC3) and adapted it to MVC5 myself. The new seed project is available at [steveLeVesconte/MvcMusicStore](https://github.com/steveLeVesconte/MvcMusicStore).

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

| Phase        | Focus              | Key Deliverables                                             | Est. Duration |
| ------------ | ------------------ | ------------------------------------------------------------ | ------------- |
| **Phase 0**  | Planning           | Repository structure, branching strategy, documentation framework | 3-5 days      |
| **Phase 1**  | Foundation         | Test coverage (xUnit), Application Insights, local performance baselines, lint baseline for seed project (no remediation for seed project), manual linting for added code like integration tests | 1-2 weeks     |
| **Phase 2**  | Azure Migration    | Azure SQL Database, App Service deployment, CI/CD pipeline, IaC (Bicep), security baseline, automated linting for added code | 2-3 weeks     |
| **Phase 3**  | Azure Validation   | Smoke testing, performance benchmarking, load testing, environment analysis | 1 week        |
| **Phase 4**  | Platform Migration | .NET 9 conversion, EF Core migration, ASP.NET Core Identity, middleware pipeline, full project automated linting | 3-4 weeks     |
| **Phase 5**  | Modern Auth        | OAuth 2.0/PKCE, external identity providers, Azure Key Vault secrets | 1-2 weeks     |
| **Phase 6**  | Observability      | OpenTelemetry tracing, structured logging, APM dashboards, health checks | 1-2 weeks     |
| **Phase 7**  | Scalability        | Distributed caching, async I/O, connection pooling, resilience patterns | 2-3 weeks     |
| **Phase 8**  | API-First          | RESTful Web API, API Management, Service Bus integration, distributed tracing | 2-3 weeks     |
| **Phase 9**  | Cloud Native       | Docker containers, Azure Container Registry, Container Apps, managed identity | 2-3 weeks     |
| **Phase 10** | DevOps Excellence  | Multi-stage pipelines, automated security scanning, DORA metrics, compliance reporting | 1-2 weeks     |

**Total Estimated Timeline**: 4-6 months (part-time development)

## 📈 Current Status

**Active Phase**: Phase 0 - Planning and Setup **Progress**: Repository initialized, branching strategy defined, documentation framework established **Last Updated**: November 9, 2025 **Status**: Phase 0 approximately 70% complete

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

## 🎓 Skills Exercised

### Azure Services (AZ-204 Aligned)

- **Compute:** App Service, Azure Container Apps
- **Storage:** Azure SQL Database, Azure Cache for Redis
- **Security:** Key Vault, Managed Identity, OAuth 2.0/PKCE
- **Integration:** API Management, Service Bus
- **Monitoring:** Application Insights, OpenTelemetry

### Development Practices

- **Testing:** xUnit, integration testing, automated testing pipelines
- **CI/CD:** GitHub Actions, multi-stage deployments, environment promotion
- **IaC:** Bicep templates, resource provisioning, environment management
- **Security:** SAST/SCA scanning, secret management, compliance automation
- **Architecture:** Microservices patterns, distributed systems, cloud-native design

### Migration Expertise

- **Platform Migration:** .NET Framework to .NET 9 conversion
- **Data Migration:** EF6 to EF Core, database modernization
- **Identity Migration:** ASP.NET Identity 2.x to Core, external auth integration
- **Containerization:** Docker, container registry, orchestration
- **Observability:** Distributed tracing, structured logging, metrics

## 🛠️ Getting Started

### Prerequisites

- Visual Studio 2022 (17.8+) or VS Code
- .NET SDK 9.0
- SQL Server LocalDB or Azure SQL Database
- Azure subscription (for cloud phases)
- Git

### Local Development Setup

```bash
# Clone the repository
git clone https://github.com/steveLeVesconte/legacy-to-modern-dotnet-migration-v2.git
cd legacy-to-modern-dotnet-migration-v2

# Checkout main branch
git checkout main

# Restore dependencies
dotnet restore

# Run database migrations
dotnet ef database update

# Run the application
dotnet run --project src/MvcMusicStore
```

The application will be available at `https://localhost:5001`

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

This project maintains a systematic documentation approach designed for ~1 hour/week maintenance while providing comprehensive project context. See [DOCUMENTATION-PLAN.md](https://claude.ai/chat/DOCUMENTATION-PLAN.md) for complete documentation system details, templates, and maintenance workflows.

### Key Documents

**Core Documentation:**

- **[PROJECT-LOG.md](https://claude.ai/chat/PROJECT-LOG.md)** - Daily work journal capturing decisions, blockers, and time investment
- **[project-outline.md](https://claude.ai/chat/project-outline.md)** - Comprehensive phase-by-phase migration plan (frozen after Phase 0)
- **[KNOWN-LIMITATIONS.md](https://claude.ai/chat/KNOWN-LIMITATIONS.md)** - Transparent inventory of constraints and deferred work
- **[QUICK-REFERENCE.md](https://claude.ai/chat/QUICK-REFERENCE.md)** - Personal cheat sheet for daily commands and conventions
- **[Seed Project Repository](https://github.com/steveLeVesconte/MvcMusicStore)** - Clean-room MVC5 implementation

**Phase-Specific Documentation:**

- **docs/phase-NN/README.md** - Actual implementation approach and outcomes for each phase
- **docs/phase-NN/TROUBLESHOOTING.md** - Complex problems and solutions (created when needed)

**Architecture Decision Records:**

- **docs/adr/NNNN-decision-title.md** - Immutable records of significant technical decisions

### Documentation Philosophy

**Living Documents** (maintained regularly):

- **PROJECT-LOG.md** - Updated daily or per work session (~10-15 min)
- **README.md** - Updated at phase transitions and major milestones
- **KNOWN-LIMITATIONS.md** - Updated as issues discovered or resolved
- **QUICK-REFERENCE.md** - Updated when you look something up repeatedly

**Frozen Planning Documents** (historical reference, never updated):

- **project-outline.md** - Original phase planning from Phase 0
- **work-execution-plan.md** - Initial execution strategy
- Phase planning documents captured during Phase 0

**Semi-Frozen Documents** (updated rarely):

- **TESTING-STRATEGY.md** - Established in Phase 1, minor refinements only
- **CONTRIBUTING.md** - Created in Phase 0, minor updates as needed
- **dependency-inventory.md** - Captured in Phase 1, frozen thereafter

**Source of Truth**:

- Git commit history and tags - Detailed change tracking
- GitHub Issues and Pull Requests - Task management and discussion
- Phase-specific README files in `docs/phase-NN/` - Implementation outcomes

### Documentation System Benefits

This structured approach provides:

- **For Future Me:** Quick context recovery when returning to the project
- **For Interviewers:** Evidence of professional documentation practices and decision-making process
- **For Learning:** Clear record of what worked, what didn't, and why
- **For Portfolio:** Demonstrates ability to maintain enterprise-grade documentation standards

The complete documentation system includes templates, decision trees, maintenance checklists, and weekly health checks. See [DOCUMENTATION-PLAN.md](https://claude.ai/chat/DOCUMENTATION-PLAN.md) for full details.

## 🤖 AI-Assisted Development

This project leverages AI tools (Claude, GitHub Copilot) as a **productivity multiplier** and learning accelerator throughout the development lifecycle. AI assistance is used strategically, with clear boundaries between AI-generated content, AI-assisted work, and human-driven decisions. But seriously, since the main goal is learning (not production), stopping and iterating on questions until I understand the output is a key behavior—not just prompt-and-paste.

A key feature of my process is measurable prompt-context and prompt effectiveness through meta-prompts. See LinkedIn article [TBD] for context quality measurement process.

**"What's measured improves"** — Peter F. Drucker

### AI Usage by Development Activity

#### **Documentation & Planning** (AI-Heavy)

AI generates initial drafts, which I review, validate, and customize:

- Technical documentation and migration guides
- Architecture decision records (ADR) exploration
- Implementation strategies and phase planning
- Test case ideation and edge case discovery
- README sections and project narrative

**My Role**: Design prompts, provide curated context, validate accuracy, make final edits, ensure alignment with project goals. Fighting with the AI. The AI has its own quirks and biases. Part of my job is to notice when it drifts from my purpose and impose my will and knowledge. Also, I must be sure I am learning from every AI-generated step both to improve my own ability to perform the same task in the future and to improve my ability to create prompts and curate context for similar tasks.

#### **Implementation** (AI-Assisted)

AI suggests solutions and boilerplate, which I evaluate and adapt:

- Refactoring recommendations
- Bug investigation and debugging assistance
- Test implementation patterns
- Configuration file templates

**My Role**: Choose and generate curated context for prompts. Write final code, validate correctness, adapt to project context, ensure maintainability and security. (See "My Role" above for expanded "The AI has its quirks and biases...")

#### **Decision-Making** (Human-Driven)

I make all strategic and architectural decisions, sometimes using AI for exploration:

- Final architectural choices and technology stack selection
- Security and compliance decisions
- Business logic design and validation
- Performance optimization trade-offs
- Quality standards and acceptance criteria

**My Role**: Full ownership. AI may provide options or analysis, but I decide (or I learn nothing!)

### Transparency and Attribution

**What's in This Repository**:

- A combination of human-written and AI-assisted documentation (generated by AI, reviewed and edited by me)
- A combination of human-written and AI-suggested code patterns (evaluated and adapted by me)
- AI-influenced architecture (explored with AI, decided by me)

**What's NOT in This Repository**:

- 100% of the prompts themselves - I just cannot add that much noise to the project, but I will select some prompts I consider instructive and representative and add them to the prompts folder.
- Unedited AI outputs (all content reviewed and validated)
- AI-generated code without human review

### Naming Strategy for Prompt Files

**Format:** `phase-NN-<type>-<subject>.md`

**Types:**

- `doc` - Documentation generation
- `code` - Code/script generation
- `decision` - Decision analysis

**Location:** `/docs/prompts/phase-NN-type-subject.md`

## 🎯 Who This Is For

**Future Me:** Serves as a technical reference, keeps the project organized, and provides material for technical discussions about cloud-native transformation.

**Technical Interviewers:** Provides concrete examples of architectural decision-making, problem-solving approaches, and hands-on experience with enterprise modernization challenges.

**Developers Planning Migrations:** Offers a reusable methodology with detailed implementation guidance, troubleshooting strategies, and lessons learned for similar .NET Framework to .NET Core/9 migrations.

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

------

**Project Repository**: [legacy-to-modern-dotnet-migration-v2](https://github.com/steveLeVesconte/legacy-to-modern-dotnet-migration-v2) **Migration Tool**: Microsoft .NET Upgrade Assistant **Reference Architecture**: Microsoft Cloud Adoption Framework for Azure

*Note: This is Version 2 of the migration project, rebuilt with a clean-room seed implementation based directly on Microsoft's tutorial.*