# Core Logging Features

## 1. Structured Data from Unstructured Text (Primary Feature)

This is the foundation of your app's differentiation. The ability to extract structured climbing data from natural language input.

### How It Works

**Input:** User speaks or types a session description.
- "Did 30 min volume work, started with warm-up reds, sent 4 blues, worked the green project for maybe 20 mins, left ring finger felt a bit tweaky, climbed with Tom"

**AI Processing:** Claude parses and extracts:
- Session date & time
- Session type (volume, limit, technique, etc.)
- Problems climbed: grade, color, result (send/attempt/flash)
- Project work: which project, time spent, notes
- Injury flag: location (left ring finger/A4), severity (mild tweak), context
- Social context: climbing partners
- Perceived exertion, movement quality if mentioned

**Output:** Structured database entries automatically created. User can:
- Review extracted data and correct errors with follow-up natural language
- Edit any field manually if AI missed or misunderstood
- Add detail later without re-entering baseline data

### Why This Matters

- **Mid-session friction disappears** — users log quickly in voice or short text, AI fills in structure.
- **Post-session enrichment** — after session, ask clarifying questions: "You mentioned feeling tweaky — did that affect your climbing? Should we flag this as injury risk?"
- **No form spam** — vs. traditional apps with 10 dropdown menus per entry.
- **Flexible language** — works across gym naming schemes, user jargon, climbing subcultures (boulderers vs. sport climbers).

### Implementation Considerations

- **Ambiguity handling:** When AI isn't sure (e.g., "red" problem — is it a grade or a color?), ask user for clarification.
- **Multi-language support:** Climbers use English, German, French, Spanish (especially outdoors). Design to expand.
- **Grading system translation:** AI recognizes V5, 5.11b, Font 6a+, Hueco, British grades in free text and maps to user's preferred system.
- **Fallback:** If parsing fails, save the raw text and let user manually assign structure later without losing data.

---

## 2. Multiple Logging Modes (Fast / Medium / Precise)

Logging needs change based on context. Provide three pathways, all feeding the same data structure.

### Fast Mode (Mid-Session)
**When:** At the gym, between problems, hands chalky.
**Input:** Minimal friction.
- Single button: "I sent" / "I attempted" / "I flashed"
- Problem: voice selection ("Blue V4") or pre-saved favorites (quick tap)
- That's it. No more fields required.
- Optional: one quick word for feeling ("solid" / "close" / "pumped")

**Output:** Basic entry. Grade + result + time.

**UX:** Swipe-based (à la Bould) or single-tap buttons. Design assumes 2–5 seconds per interaction.

---

### Medium Mode (Session Log)
**When:** End of session, still at the gym or in the car.
**Input:** Moderate detail, 2–3 minutes of input.
- Session type: volume / limit / technique / endurance / hangboard / campus / other
- Grade range climbed (lowest to highest)
- Total problems attempted / sent
- Project work: yes/no, which project, time spent, progress made
- Perceived effort: 1–10 scale
- Condition: how felt today (strong, tired, sore, good movement, etc.)
- Partners: who climbed with (optional)
- Notes: 1–2 sentences if anything stood out

**Output:** Structured session entry with context. AI infers details from previous entries (gym location, usual grade range, etc.).

**UX:** Guided form with context-aware defaults. Smart defaults save time (e.g., if you always climb at Gym A, auto-select it).

---

### Precise Mode (Post-Session Enrichment)
**When:** Evening, at home, reflecting on the session.
**Input:** Rich narrative (voice or typed).
- Voice dump: "Okay so today was mostly volume. I warmed up on the reds, climbed through all the blues, sent 4 new V4s which felt great. Spent maybe 25 minutes on the green slab project — I keep getting stuck at the top because I'm not using my feet right. Need to work on that. My left shoulder was a bit sore from the hangboard work on Monday, not painful but I'm being careful. Climbed with Tom and Sarah, both doing well. I felt pretty strong today, maybe a 7 or 8 out of 10 energy-wise."
- AI extracts all structured data as described above.
- User reviews suggested entries, edits, adds corrections.
- Conversational follow-up: AI asks clarifying Qs as needed.

**Output:** Richest entry type. Full context captured. Future training plans and injury insights drawn from this layer.

**UX:** Free-form text/voice input field. No fields to fill. AI does the schema mapping. Show extracted data for review & edit inline.

---

### Cross-Mode Data Flow

- **Fast mode → Medium mode:** If user logged 5 problems in Fast mode, Medium mode pre-populates them. User just adds context.
- **Any mode → Precise mode:** After session, email or push reminder: "Want to add more detail to today's session?" One tap goes to Precise mode with prior data loaded.
- **Information can be added anytime:** Logged 3 problems fast at the gym? Add detail at home. Add injury observation the next morning. Add project progress notes a week later when reflecting. No timestamp lock-in.

---

## 3. Projects Tab

Each climbing project is a rich file, not a one-line status entry.

### What Lives in a Project

**Basic Info:**
- Name (e.g., "Blue slab V5")
- Location (gym, outdoor crag, or home gym)
- Grade
- Date first encountered / Date started working it

**Attempt Log:**
- Date, attempt number, high point reached, how close you felt (1–10), movement focus of the session, any progress made
- Can add multiple attempts from a single session
- Timeline visualization: calendar heatmap showing attempt frequency, gaps, clusters

**Session Notes:**
- Specific moves you've tried: heel hook, drop knee, mantel, etc.
- Sequences tested: "try crimp, side pull, jugs" or "dynos to slopers"
- Feeling notes: "crimp is too small for my hands" vs. "movement feels close but I'm not committing"
- Video snippets (optional): link to phone video of attempts

**Recovery & Injury Context:**
- If you logged injury/pain around the time you were projecting, auto-link it
- "Worked this problem when my finger was sore — don't repeat that"

**Meta:**
- User-defined tags: "slab", "endurance", "technical", "power", "outdoor", etc.
- Goal deadline (optional): "Want to send by June"
- Public/private toggle (share with climbing partners or keep private)

**Success Entry:**
- Date sent (onsight, flash, redpoint, or repeated)
- How it felt when sent
- How many sessions invested
- What finally worked

### UX for Projects

- **One-tap add:** At the gym, tap "Start project" on any problem, take a photo, done. Details added later.
- **Attempt quick-log:** "3 attempts today, V5 slab, 5 minutes work" → text field or voice, AI parses into 3 separate entries.
- **Project view:** Timeline of all attempts + notes. Visualization of progression (high point increasing over weeks).
- **Reflection prompts:** "You've been working this for 8 sessions. What's holding you back?" Helps user articulate what they need to focus on.

---

## 4. Injuries Tab

Climbing-specific injury logging with recovery tracking and load correlation.

### What Gets Logged

**Injury Event:**
- Date started (or suspected)
- Body part (climbing-specific: finger pulley A2–A5, crimp pad, palm, thumb, wrist, elbow, shoulder, back, knee, ankle)
- Type: strain, tendon tweak, bruise, blister, general soreness
- Severity: 1–10 pain scale
- How it happened (if known): "Crimp climbing", "Hangboard max hangs", "Off-climbing fall/contact"
- Affected movements: which grips, which positions aggravate it

**Timeline & Recovery:**
- Days off climbing (rest period)
- Return-to-climbing date
- Modifications made: taping, reduced intensity, avoided certain moves
- Progression: "Day 3: still sore but less sharp" → "Day 7: felt okay on jugs, avoided crimps"
- Final status: resolved, ongoing, recurrent

**Correlation Data:**
- Training load in the 2 weeks prior (auto-calculated from logs)
- Session type before injury: volume day, limit day, high intensity, endurance work
- Sleep/recovery notes: "Had bad sleep that week", "Was traveling"

**Notes:**
- What did and didn't help: ice, rest, specific stretches, rehab exercises
- Lessons learned: "Don't do max hangs two days in a row"

### Analysis Features

- **Pattern detection:** "You've had finger injuries 3 times; they follow high-volume weeks. Consider deload."
- **Injury heat map:** Visual chart of which body parts are most affected, when, under what conditions
- **Load awareness:** Auto-flag when weekly training load spikes above your rolling average (injury risk alert)
- **Injury-to-session causality:** When you log injury, app asks: "What were you doing before this started?" Learns associations.

### UX for Injuries

- **Quick log:** "Something tweaked my elbow today" → short form, date, severity. Rich details optional.
- **Injury timeline:** Visual calendar showing injury start, duration, return date. Color-coded by body part.
- **Correlation view:** Overlay injuries on training logs. See visually: high volume → injury gap → return.
- **Recovery checklist (optional):** User-defined: ice, stretching, specific rehab, modified climbing plan. Track completion.

---

## 5. Plans Tab

Training plans structured for maximum flexibility, not rigid prescriptions.

### Plan Structure

**High-Level:**
- Plan name (e.g., "Spring 2025 Power Block")
- Duration: flexible length (4 weeks, 8 weeks, open-ended)
- Primary goal: power, endurance, volume, technique, strength endurance, balanced, or custom
- Notes: any macro strategy (e.g., "Deload week 4, peak week 6")

**Micro-Level (Flexible):**
- Each week/session can have:
  - **Intended focus:** climbing type (limit, volume, technique, endurance) + specific training emphasis (crimps, slopers, power, footwork)
  - **Workouts:** hangboard protocol, campus routine, pull-up sets, stretching, cardio — or leave blank and improvise
  - **Load target (optional):** "Aim for 20–25 problems today"
  - **Notes:** "Deload week, go easy" or "Push hard this week"

**Flexibility Levers:**
- User can modify any week on the fly ("I'm tired, skip hangboard this week")
- Can add/remove sessions mid-plan
- Can extend or shorten plan based on progress
- No rigid day-by-day prescription; room for life

### Integration with Logging

- **Plan adherence tracking:** After each session, app asks: "Did you follow the plan? Why or why not?"
- **Plan effectiveness metrics:** Over time, which plan structures led to progress? Which led to injuries?
- **Adaptive suggestions (Phase 2):** Once you have 2–3 months of data, Claude can suggest: "A power + volume mix worked best for you last year. Try that again."

### UX for Plans

- **Plan templates (optional):** Popular structures (8-week hangboard cycle, 4-week volume block, periodized mix) available as starting points. User can customize.
- **Plan builder:** Lightweight form. Week 1 = "Limit focus, 2 hangboard sessions"; Week 2 = "Volume + technique" — done.
- **Plan view:** Calendar-style display. See at a glance what each week's intended focus is.
- **Plan vs. reality:** Overlay actual logs on top of plan to see adherence and outcomes.
- **Plan reflection:** "How did this plan work for you?" Capture user feedback to improve plan design over time.

---

## 6. Weekly Summary (Auto-Generated Sunday Evening)

Every Sunday, the app generates a summary of the past week and asks reflection questions.

### Auto-Generated Summary Includes

- **Session count & volume:** X sessions, Y total problems climbed, Z hours invested
- **Grades climbed:** range and distribution (how many V3s, V4s, V5s, etc.)
- **Projects:** status updates on projects worked
- **Injuries:** any new tweaks or ongoing issues
- **Training load:** comparative to previous weeks (peak week? recovery week?)
- **Consistency:** "You climbed 5 of 7 planned sessions"
- **Highlights:** "Sent 2 new V5s" or "Best volume day all month"

### Reflection Prompts (AI-Generated)

- "You had a big jump in volume this week. How did your body feel?" (Load awareness)
- "You logged a finger tweak midweek. How's it feeling now?" (Injury follow-up)
- "Your project work was short this week. Was it intentional or time-constrained?" (Context capture)
- "Which session this week felt the best? What was different?" (Performance introspection)
- "You're averaging 3 rest days/week. Good balance or wanting to climb more?" (Training philosophy)

**User answers freely in text.** AI uses responses to understand:
- What motivates them
- What sustainable load looks like for them
- What their actual climbing goals are (vs. stated goals)

### Why Weekly Summaries Matter

- **Habit formation:** Sunday ritual. Climbers check in, reflect, plan the week ahead.
- **Data enrichment:** Qualitative feedback from users feeds future training plan generation.
- **Pattern detection (Phase 2):** After 3–4 months of summaries, Claude spots patterns ("You always feel best on Wednesday sessions after a rest day") and can use this in recommendations.

### UX for Summaries

- **Push notification:** Sunday 6 PM: "Your weekly summary is ready. Review it?"
- **Lightweight UI:** Summary displays automatically. Reflection questions are just text fields.
- **Archive:** Summaries stored and searchable. User can look back at any week.
- **Sentiment tracking (optional):** Simple mood score (1–10 how satisfied with week) tracked over time for motivation spikes/dips.

---

## 7. Optional Summary Reports

Beyond the weekly auto-summary, user can request custom summaries.

### Available Report Types

- **Monthly review:** Full month overview, trends, what went well, what to adjust
- **Project retrospective:** "Show me all attempts on Project X from start to finish with a timeline"
- **Injury review:** "All my finger issues from the past year — patterns and prevention"
- **Training cycle analysis:** "How did my last 8-week plan perform? What should I change?"
- **Grade progression:** "Show my V-grade distribution over time — am I progressing?"
- **Comparison periods:** "How was October vs. July? What was different?"
- **Custom (free-form):** "What have I learned about my body this year?" — Claude generates a narrative

---

## 8. Data Export to CSV

Core feature. Non-negotiable.

### What Can Be Exported

- **Full session log:** Every session with all fields (date, time, grade, send/attempt, project, injury, notes, mood, load, etc.)
- **Projects:** All projects with attempt history, high points, dates, notes
- **Injuries:** All injury logs with timelines and outcomes
- **Plans:** All training plans and their adherence data
- **Weekly summaries:** All reflection prompts and user responses

### Export Formats

- **CSV:** One table per data type (sessions, projects, injuries, plans). Standard columns, easy to pivot in Excel.
- **JSON (Phase 2):** Full nested data structure for power users or developers.

### UX for Export

- **One-click export:** Settings → "Download my data" → select what to export → get file immediately.
- **Scheduled exports (Phase 2):** Monthly automated backup to email.
- **Time-range filters:** Export last 3 months, last year, all time.
- **Transparency:** Clear privacy statement: "Your data is yours. Export anytime, no restrictions."

---

## Implementation Priority

### Must-Have (Launch)
1. Structured data from unstructured text (core feature)
2. Fast + Medium logging modes
3. Basic project tracking
4. Basic injury logging
5. CSV export

### Should-Have (Phase 1)
6. Precise mode
7. Plans tab (simple, flexible structure)
8. Weekly summaries
9. Weekly reflection prompts

### Nice-to-Have (Phase 2+)
10. Injury pattern detection
11. Training plan generation from historical data
12. Sentiment tracking
13. Custom report generation
14. JSON export
15. Mobile app (after PWA is stable)
