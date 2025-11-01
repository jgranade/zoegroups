# ZoeGroups - Multi-Generational Discipleship Platform

ZoeGroups enables churches, families, and faith communities to study Scripture and grow together through flexible, age-adapted group studies.

## Project Overview

**Mission:** Facilitate multi-generational discipleship through structured Bible studies and group learning.

**Approach:** One curriculum designed for multiple age groups studying together, supporting family and community discipleship.

**Technology:** Built with ABP Framework (.NET 8), SQL Server, and Blazor UI.

---

## Repository Structure

### `/AI` - AI Agents for Development
Specialized AI agents for platform development and curriculum creation.

**Platform Agents:**
- `zoegroups-architect.md` - Domain modeling and architecture
- `zoegroups-developer.md` - ABP implementation
- `zoegroups-database.md` - SQL Server and EF Core

**Curriculum Agents:**
- `curriculum-designer.md` - Educational design principles
- `ttbt-specialist.md` - Through the Bible Together content

See [AI/README.md](AI/README.md) for usage guide.

### `/docs` - Documentation
Project documentation for developers and content creators.

**Architecture:**
- System overview and design
- ABP layer organization
- Integration patterns

**Domain Model:**
- Entity definitions
- Relationships and aggregates
- Module boundaries

**Design Decisions:**
- Architectural Decision Records (ADRs)
- Rationale for major choices

### `/Courses` - Curriculum Content
Course and study content in structured formats.

**TTBT (Through the Bible Together):**
- 20-week Old Testament journey
- 4 age groups: Adult, Youth, Kids, Early Childhood
- JSON structure for platform integration

---

## Key Concepts

### Study
Group-based, open-ended content with:
- Weekly themes
- Daily readings
- Discussion questions
- Age-appropriate adaptations

### Term
A scheduled run of one or more Studies:
- Configurable start date and duration
- Meeting day preferences
- Break weeks and events
- Progress tracking

### Program
Optional grouping of related Studies (e.g., "Through the Bible Together")

---

## Getting Started

### For Developers

1. **Review Architecture:** Start with `/docs/architecture/system-overview.md`
2. **Understand Domain:** Read `/docs/domain-model/` (when populated)
3. **Use AI Agents:** Reference `/AI/agents/platform/` for implementation guidance
4. **Build with ABP:** See [app.zoegroups.net](https://github.com/jgranade/app.zoegroups.net) repository

### For Content Creators

1. **Study Design Principles:** Review `/AI/agents/curriculum/curriculum-designer.md`
2. **TTBT Structure:** See `/AI/agents/curriculum/ttbt-specialist.md`
3. **Course Content:** Check `/Courses/TTBT/` for examples
4. **Educational Approach:** Reference age-group guidelines in agents

### For AI-Assisted Development

1. **Claude Code Workspace:** Use [zoegroups-claude-code](https://github.com/jgranade/zoegroups-claude-code)
2. **Agent Configuration:** Agents auto-load from this repository
3. **Coordination:** See `zoegroups-claude-code/CLAUDE.md` for workflow guidance

---

## Project Repositories

**App:** [jgranade/app.zoegroups.net](https://github.com/jgranade/app.zoegroups.net)
- ABP Framework application
- Frontend and backend implementation
- Database migrations

**Ecosystem:** [jgranade/zoegroups](https://github.com/jgranade/zoegroups) (this repo)
- AI agents
- Documentation
- Course content
- Design decisions

**Workspace:** [jgranade/zoegroups-claude-code](https://github.com/jgranade/zoegroups-claude-code)
- Claude Code environment
- Agent coordination
- Development workflows

---

## Technology Stack

**Backend:**
- ABP Framework 8.x
- .NET 8 / C# 12
- Entity Framework Core 8
- SQL Server

**Frontend:**
- ABP Blazor UI
- Blazorise components
- Bootstrap styling

**Development:**
- Claude Code (AI-assisted)
- GitHub
- Visual Studio / VS Code

---

## Current Status

**Platform:** Domain modeling and architecture phase  
**Content:** TTBT Old Testament (20 weeks) available  
**Development:** Core entities and ABP scaffolding in progress

---

## Contributing

### Platform Development
1. Consult appropriate AI agent for guidance
2. Follow ABP Framework patterns
3. Document design decisions in `/docs/design-decisions/platform/`
4. Submit PRs to [app.zoegroups.net](https://github.com/jgranade/app.zoegroups.net)

### Content Development
1. Work with Curriculum Designer and course specialists
2. Follow age-group guidelines
3. Document decisions in `/docs/design-decisions/curriculum/`
4. Add content to `/Courses/` with proper structure

---

## Learn More

- **Architecture:** [docs/architecture/system-overview.md](docs/architecture/system-overview.md)
- **AI Agents:** [AI/README.md](AI/README.md)
- **Domain Model:** Coming soon in `/docs/domain-model/`
- **Design Decisions:** Coming soon in `/docs/design-decisions/`

---

## Contact

For questions or collaboration opportunities, please open an issue in the appropriate repository.

---

*Building tools that help families and churches study God's Word together across generations.*
