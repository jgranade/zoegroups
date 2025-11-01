# ZoeGroups Architecture - System Overview

## Purpose
ZoeGroups enables multi-generational discipleship through flexible, time-bound group studies. It provides:
- Structured **Studies** (with weeks and days)
- Customizable **Terms** for live group runs
- Scheduling logic with group events and shiftable weeks
- Age-adaptable **content blocks**
- Individual and group tracking

Designed for use by churches, families, and informal faith groups.

---

## Core Concepts

### Study (Content Template)
- Immutable set of `StudyWeeks` and `StudyDays`
- Each day has composable content blocks: `reading`, `questions`, `reflection`, etc.
- Adapted for age groups: `adult`, `youth`, `kids`, `early_childhood`
- May include optional audience variants: e.g., "young girls", "widows"
- Uses stable IDs: `week_id`, `day_id`, and explicit `week` and `day` numbers for internal reference and display

#### Structure
- Study
  - StudyWeeks (week number + title + `week_id`)
    - StudyDays (day number + title + `day_id`)
      - Content Blocks (by kind)
        - Age group variants
        - Optional audience variants (additive or override blocks)

### Program (Optional Organizer)
- Higher-level grouping of related Studies
- Example: "Through the Bible Together"
- Not required per Study, but useful for bundling and filtering

### Course (Future)
- Distinct from Study; more structured, instructional, and goal-based
- May include prerequisites, testing, and certification
- Targets individual learners or leader development paths
- Uses its own structure (CourseWeek, CourseDay, Assessments)

---

## Term (Live Session)
- A **Term** is a scheduled run for a group using one or more Studies
- Configurable start date, meeting day, and duration (e.g., 13 weeks)
- Studies are loaded into Terms and can be shifted dynamically

### Term Features
- Insert break weeks (e.g. "Off for July 4th")
- Add events (e.g. "Group Dinner")
- Automatically shift downstream weeks when configured
- Supports overlapping Studies in one Term

---

## Scheduling Engine
- Generated from:
  - Term start date
  - Meeting day of week
  - Number of weeks
- Produces `WeekStart` and `DayDue` entries (calendar-ready)
- Group events and skips also generate `Instance` records
- Shifts respect existing completions or exceptions

---

## Data Models (Simplified)

### Content
- `Study`
- `StudyWeek` (week_id, week number, title)
- `StudyDay` (day_id, day number, title)
- `DayContentBlock` (by kind, optionally JSON)
- `DayContentVariant` (age group or audience-specific overrides)

### Organization
- `Program` (optional)
- `StudyTag` / `Tag`

### Runtime
- `Term`
- `TermStudySegment`
- `TermWeek`
- `TermEvent`
- `GeneratedInstance`
- `Participant`
- `UserProgress`

---

## Naming Choices
- **Study**: group-based, open-ended, relational content
- **Term**: scheduled time box for a group (formerly "Session")
- **Program**: optional umbrella for related Studies
- **Course**: future learning-focused structure with testing/certification
- **StudyWeek / StudyDay**: avoids ambiguity and supports future `CourseWeek`, `CourseDay` expansion

---

## Technology Stack

### Backend
- **Framework**: ABP Framework 8.x
- **Language**: C# 12 / .NET 8
- **ORM**: Entity Framework Core 8
- **Database**: SQL Server
- **API**: RESTful with ASP.NET Core

### Frontend
- **UI Framework**: ABP Blazor UI (or MVC)
- **Component Library**: Blazorise
- **Styling**: Bootstrap-based

### Architecture
- **Pattern**: Domain-Driven Design (DDD)
- **Layers**: Domain, Application, Infrastructure, Presentation
- **Modules**: Studies, Terms, Community, Progress

---

## Development Roadmap

### Phase 1: Core Platform (Current)
- Domain model scaffolding
- Study and Term entities
- Basic CRUD operations
- Initial data seeding (TTBT OT)

### Phase 2: Community Features
- User enrollment and groups
- Progress tracking
- Basic notifications
- Group leader tools

### Phase 3: Enhanced Content
- Rich content blocks
- Media support
- Discussion tools
- Assessment features

### Phase 4: Advanced Features
- Course module
- Advanced scheduling
- Analytics and reporting
- Mobile optimization

---

## See Also

- `/docs/domain-model/` - Detailed entity definitions and relationships
- `/docs/design-decisions/platform/` - Architectural Decision Records (ADRs)
- `/AI/agents/platform/` - AI agent guides for development
