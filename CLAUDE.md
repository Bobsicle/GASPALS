# GASPALS - Claude Code Guidelines

## Workflow Orchestration

### 1. Plan Mode Default
- Enter plan mode for ANY non-trivial task (3+ steps or architectural decisions)
- If something goes sideways, STOP and re-plan immediately
- Use plan mode for verification steps, not just building
- Write detailed specs upfront to reduce ambiguity

### 2. Subagent Strategy
- Use subagents liberally to keep main context window clean
- Offload research, exploration, and parallel analysis to subagents
- For complex problems, throw more compute at it via subagents
- One task per subagent for focused execution

### 3. Self-Improvement Loop
- After ANY correction from the user: update tasks/lessons.md with the pattern
- Write rules for yourself that prevent the same mistake
- Ruthlessly iterate on these lessons until mistake rate drops
- Review lessons at session start for relevant project

### 4. Verification Before Done
- Never mark a task complete without proving it works
- Diff behavior between main and your changes when relevant
- Ask yourself: "Would a staff engineer approve this?"
- Run tests, check logs, demonstrate correctness

### 5. Demand Elegance (Balanced)
- For non-trivial changes: pause and ask "is there a more elegant way?"
- If a fix feels hacky: "Knowing everything I know now, implement the elegant solution"
- Skip this for simple, obvious fixes -- don't over-engineer
- Challenge your own work before presenting it

### 6. Autonomous Bug Fixing
- When given a bug report: just fix it. Don't ask for hand-holding
- Point at logs, errors, failing tests -- then resolve them
- Zero context switching required from the user
- Go fix failing CI tests without being told how

## Task Management
- **Plan First:** Write plan to tasks/todo.md with checkable items
- **Verify Plan:** Check in before starting implementation
- **Track Progress:** Mark items complete as you go
- **Explain Changes:** High-level summary at each step
- **Document Results:** Add review section to tasks/todo.md
- **Capture Lessons:** Update tasks/lessons.md after corrections

## Core Principles
- **Simplicity First:** Make every change as simple as possible. Impact minimal code.
- **No Laziness:** Find root causes. No temporary fixes. Senior developer standards.
- **Minimal Impact:** Only touch what's necessary. No side effects with new bugs.

## Obsidian Vault Integration

### Vault Location
- **Path:** `S:\Obisidian\KillFeed\`
- **Dashboard:** `00 - Dashboard\Home.md`
- **Templates:** `Templates\`

### Session Summaries
After each significant work session, write a session summary to:
  `01 - Sessions/YYYY-MM-DD.md`
If a daily log already exists for today, append a new `## Session HH:MM` section rather than overwriting.

### Before Architectural Decisions, CHECK:
- `02 - Design/` — check existing design docs to avoid contradicting prior choices

### Bug Tracking
When fixing bugs, create or update bug reports at:
  `04 - Bugs/BUG-NNN-description.md`

### Design Decisions
When making non-trivial architectural choices:
1. Create a design doc using the `Templates/Design.md` template in `02 - Design/`

### Folder Structure
```
KillFeed/
├── 00 - Dashboard/        # Home.md (Dataview dashboard), Systems Map
├── 01 - Sessions/         # Daily session logs
├── 02 - Design/           # Design decisions and architecture docs
├── 03 - Research/         # UE5 docs, analysis, deep dives
├── 04 - Bugs/             # Bug reports
├── 05 - Assets/           # Asset pipeline docs
├── 06 - Playtest/         # Playtest notes
├── 07 - Ideas/            # Ideas backlog
└── Templates/             # Note templates (Session, Bug, Design, Research, Playtest, Idea)
```

### Tags (ALWAYS apply)
- Type: `#session` `#design` `#research` `#bug` `#asset` `#playtest` `#idea`
- Status: `#status/open` `#status/in-progress` `#status/done` `#status/blocked` `#status/parked`
- System: `#system/ai` `#system/animation` `#system/gameplay` etc.
- Priority: `#priority/critical` `#priority/high` `#priority/medium` `#priority/low`
- `#auto-generated` for Claude-written notes

### Linking Rules
- Use `[[wiki-links]]` to cross-reference related notes
- Every daily log links to its sprint, bugs found, and decisions made
- Every bug links to the session where it was found/fixed
- Every decision links to patterns it follows and blueprints that implement it
