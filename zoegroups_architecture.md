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

## Next Steps
- Scaffold domain models in ABP Suite
- Generate APIs for CRUD of Studies, Terms, and Events
- Create seed for "OT Foundations" Study from existing JSON
- Link user progress and calendar views
- Optional: define `Program` UI later but model it now

---

Let me know if you want variants of this for dev handoff, roadmap planning, or public documentation.

