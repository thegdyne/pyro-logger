# Pyro Logger Backlog

## Feature Requests

### Progress tracker toward grade submission
**Status:** backlog  
**Source:** Dec 2025

**Request:**
> A personal day counter so every PDF you generate it logs the ticks (days) 
> and displays at the top of the page as you have to have done X days to 
> submit a grade so you're able to see how close you are or it tells you

**Description:**
Track cumulative pyro work days across all logged entries and display progress toward grade submission thresholds. The Joint Industry SFX Grading Scheme requires a minimum number of logged days before submitting for each grade level.

**Grade checkpoints (from Joint Industry SFX Grading Scheme):**

| Grade | Days Required |
|-------|---------------|
| Technician | 250 days |
| Senior Technician | 500 days |

**Note:** 80% of logged experience must involve varied pyrotechnics/igniters/detonators/high explosives. Max 10% can be small scale practical fires.

**Proposed behaviour:**
- Aggregate total days worked from all saved entries
- Display progress: "127 / 250 days"
- Persist in localStorage alongside entries
- Show on main dashboard

**Milestone celebrations:**
When threshold crossed, show acknowledgement below counter:
- 250 days → "🎉 Technician Grade time met, congratulations! 🎉"
- 500 days → "🎉 Senior Technician Grade time met, congratulations! 🎉"
- 750 days → "🎉 Supervisor Grade time met, congratulations! 🎉"

**Dashboard display:**
```
Total Days: 312

🎉 Technician Grade time met, congratulations! 🎉

Next: 188 days to Senior Technician
```

Message persists (they earned it). No dismiss logic needed.

**Data model:**
- `prior_days`: Single editable number for pre-app paper records (stored in localStorage)
- Logged days: **Calculated** from saved log entries (source of truth)
- Total = `prior_days` + sum of days from saved logs

Deleting a log entry → logged count decreases → total decreases.
This is a **guide** so users don't have to manually count their logs.

**Onboarding:**
Simple input box: "Enter your existing day count: [322]"
Editable later in settings.

**Dashboard display:**
```
Total Days: 345
(Prior: 322 + Logged: 23)

🎉 Technician Grade time met, congratulations! 🎉

Next: 155 days to Senior Technician
```

**Colour theming:**
- Under 250: Default
- 250+ (Technician): Red theme
- 500+ (Senior Technician): Yellow theme

**Grade checkpoints (two only):**
- 250 days → Technician
- 500 days → Senior Technician

**Stretch goals:**
- Track supervisor signatures (which supervisors signed off on entries)
- Track course completion status (manual checkboxes)

**Open questions:**
- Should the (Prior: X + Logged: Y) breakdown be visible, or just total?
- Where does the prior days input live - onboarding only, or always accessible in settings?

---

*Add new requests above this line*
