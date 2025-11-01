# ZoeGroups AI Agents

This folder contains AI agent definitions for the ZoeGroups ecosystem. These agents are designed to work with Claude Code, ChatGPT, Cursor, and other AI coding assistants.

## Purpose

Agents provide specialized expertise for:
- **Platform Development** - Building the ZoeGroups ABP application
- **Curriculum Development** - Creating educational course content

## Available Agents

### Platform Development (`platform/`)

**zoegroups-architect.md**
- Domain modeling and entity design
- ABP architecture decisions
- System design and integration patterns
- Use for: "What should the app do?" and "How should entities relate?"

**zoegroups-developer.md**
- ABP Framework implementation patterns
- Application Services, Domain Services, Repositories
- DTOs, AutoMapper, API development
- Use for: "How do I implement this in ABP?"

**zoegroups-database.md**
- SQL Server schema design
- EF Core configuration and migrations
- Data seeding and optimization
- Use for: "How should we store this data?"

### Curriculum Development (`curriculum/`)

**curriculum-designer.md**
- Educational design principles
- Age-appropriate learning strategies
- Assessment and engagement techniques
- Use for: "How should we teach this?"

**ttbt-specialist.md**
- Through the Bible Together content expert
- Biblical content structure and age adaptations
- Reading plan design
- Use for: "What content goes in TTBT?"

## Using These Agents

### With Claude Code

Agents in this folder are automatically loaded by Claude Code when configured in the workspace. See `jgranade/zoegroups-claude-code` for workspace setup.

### With Other Tools

These markdown files can be:
- Referenced in prompts: "Act as the zoegroups-architect agent..."
- Copied into custom instructions
- Used as context in any AI conversation

## Agent Coordination

Some tasks require multiple agents:
- **Platform + Curriculum**: "Add assessment tracking for courses"
  - Architect designs the domain model
  - Curriculum Designer defines pedagogical requirements
  - Developer implements in ABP
  - Database handles storage

## Documentation References

Agents reference documentation in `/docs`:
- `/docs/domain-model/` - Entity definitions and relationships
- `/docs/design-decisions/` - Architectural Decision Records (ADRs)
- `/docs/architecture/` - System design documentation

## Adding New Agents

When adding course-specific specialists:
1. Create agent file in `curriculum/[course]-specialist.md`
2. Define expertise scope and content knowledge
3. Update this README
4. Reference relevant course files in `/Courses`

## Project Repositories

- **App**: [jgranade/app.zoegroups.net](https://github.com/jgranade/app.zoegroups.net) - ABP application
- **Ecosystem**: [jgranade/zoegroups](https://github.com/jgranade/zoegroups) - This repo (agents, docs, courses)
- **Workspace**: [jgranade/zoegroups-claude-code](https://github.com/jgranade/zoegroups-claude-code) - Claude Code environment

---

*These agents provide deep expertise in their domains and can be coordinated for complex, cross-cutting work.*
