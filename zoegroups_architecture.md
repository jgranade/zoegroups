# ZoeGroups – Core Architecture Overview

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
- Immutable set of weeks and days
- Each day has composable content blocks: `reading`, `questions`, `reflection`, etc.
- Adapted for age groups: `adult`, `youth`, `kids`, `early_childhood`

#### Structure
- Study
  - Weeks (1..N)
    - Days (1–7 max)
      - Blocks (ordered)
        - Optional: variants per age group

### Program (Optional Organizer)
- Higher-level grouping of related Studies
- Example: "Through the Bible Together"
- Not required per Study, but useful for bundling and filtering

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
- `StudyWeek`
- `StudyDay`
- `DayContentBlock` (by kind)
- `DayContentVariant` (per age group)

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
- **Study**: smallest unit of structured content
- **Term**: scheduled time box for a group (formerly "Session")
- **Program**: optional umbrella for related studies

---

## Next Steps
- Scaffold domain models in ABP Suite
- Generate APIs for CRUD of Studies, Terms, and Events
- Create seed for "OT Foundations" Study from existing JSON
- Link user progress and calendar views
- Optional: define `Program` UI later but model it now

---

Let me know if you want variants of this for dev handoff, roadmap planning, or public documentation.

