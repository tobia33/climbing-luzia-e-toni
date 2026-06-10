# Competitor Tools Analysis

## Existing Apps & Web Apps

### Logbook & Basic Tracking
- **TopLogger** — Gym-integrated logbook with interactive maps, leaderboards, route notifications. Free. Only works at partner gyms.
- **8a.nu** — The classic outdoor route logbook. Huge community used by serious climbers for ticks.
- **Vertical-Life** — Indoor + outdoor with coach-made training plans. Large crag database. Premium subscription.
- **SendLog** — Voice notes via speech recognition, cloud sync, project tracking. Multi-grade system support.
- **Tickmarks** — Minimalist logbook for serious project-focused climbers. No social feed. iOS.
- **BoulderLog** — Bouldering-specific log with analytics, interval timers. 100 free entries then paid.
- **klettrack** — Free, open-source, no tracking. Kilter/Tension board sync. iOS.
- **Chalk'd** — Minimalist, visual progress tracking. Tap-to-log simplicity. Custom grading systems.
- **Bould** — Swipe-based logging (left = fail, right = send). Fast, no gym integration needed.
- **FlashNotee** — Training log with session history, attempt tracking, local data storage.
- **ClimbingNote+** — Minimalist log, V grades and YDS. Local data only.
- **BLDR BK** — Lightweight, simple gym session tracking.
- **Quopi** — Session logging + training workouts + social features + friend analytics.
- **Campus** — Moon/Kilter board integration, load monitoring, training analytics.
- **SwiftClimb** — Logbook with heatmaps, grade pyramids, skill radar charts.
- **Passion** — Beginner-focused training app with structured plans (hangboard coming soon).
- **OBSIDN** — Track & analyze all climbing styles, goal tracking.

#### Our comments about these apps
- TopLogger
- 8a.nu, log di blocchi outdoor, molto usato, noi non abbiamo accesso a database di blocchi fuori quindi non possiamo farlo, e comunque non ha senso cercare di rimpiazzarli sono troppo established
- Vertical-Life, la stessa cosa di 8a.nu
- SendLog
- Tickmarks
- BoulderLog
- klettrack
- Chalk'd
- Bould
- FlashNotee
- ClimbingNote+
- BLDR BK
- Quopi
- Campus
- SwiftClimb
- Passion
- OBSIDN

### AI-Powered & Training-Focused
- **Climbah** — AI coach with video analysis, personalized plans, voice coaching, injury tracking. iOS. *Closest competitor.*
- **Redpoint** — Apple Watch auto-detection (barometric sensor). Session stats and training suggestions. Subscription. iOS-only.
- **ClimbingCoach** — Periodized training plan generator. Structured workouts across modalities.
- **Climb Genius** — Session tracking, climbing news, tailored workouts.
- **DART Climbing** — Speed climbing focused. Session logging, performance stats, error tracking.

### Community & Structured Training
- **Climbing Notebook** (GitHub) — Open-source web app. Injury tracking, training cycles, metrics, dashboards.
- **Notion Templates** (logmyclimb.app, Gumroad, Prototion) — Multiple free and paid templates. Popular among advanced climbers.

---

## What Existing Apps Do Well

- **Grade tracking & send counting** — solved universally. Every app handles this baseline well.
- **Session frequency & calendar views** — standard across all platforms.
- **Hangboard/interval timers** — specialized apps execute this cleanly with built-in protocols.
- **Hardware sensor integration** — Redpoint's barometric altitude detection + Apple Watch motion removes manual logging friction.
- **Gym-specific UX** — TopLogger's interactive maps, leaderboards, and new route notifications create genuine stickiness for partner gyms.
- **Multiple grading systems** — most apps support V-scale, Font, YDS, British grades with conversions.
- **Performance dashboards** — graphs, grade pyramids, flash rates, attempt distributions are well-implemented.
- **Project tracking basics** — most apps track project status (project, attempted, flashed, redpointed).

---

## What Existing Apps Lack

### Critical Gaps

**1. Injury Tracking is Nearly Absent**
- Climbah mentions it but it's just checkboxes for body parts.
- No app correlates injuries to training load over time.
- No recovery timeline tracking or injury-to-session causality analysis.
- No injury pattern detection (e.g., "injuries spike 2 weeks after high-volume weeks").

**2. Qualitative Data is Underutilized**
- How a session *felt*: mental state, perceived effort, movement quality.
- Why a project isn't clicking: specific movement issues, mental barriers, environmental factors.
- Session context: indoor/outdoor, gym conditions, climbing partners, time of day.
- Recovery notes, sleep quality, nutrition notes — completely missing.
- Most apps force qualitative data into a small notes field, rarely indexed or analyzed.

**3. Fragmentation Across Tools**
- Most apps force a choice: logbook OR training generator.
- Serious climbers use 2-3 apps simultaneously (one for logging, one for training, one for hangboard).
- No cross-app data sync. Information siloed in separate ecosystems.
- Training plans don't learn from actual logging history.

**4. Generic Training Plans (No True Personalization)**
- Climbah generates plans from a one-time intake survey, not from accumulated logs.
- Plans don't adapt as you log. No learning loop.
- No feedback mechanism: did the plan work? Why or why not?
- No program periodization that accounts for your actual performance history.

### Secondary Gaps

**5. Project Management is Shallow**
- Projects are usually just status entries (attempted, project, sent).
- No rich project file: attempt history, movement notes, beta tested, sequence variations.
- No easy way to log multiple attempts on a project in a single session.
- No attempt-by-attempt reflection or progression tracking.

**6. Energy & Load Awareness Missing**
- No training load calculation across modalities (gym + hangboard + campus = total load).
- No sleep/recovery logging.
- No correlation between high-load weeks and subsequent injuries.
- No perceived exertion tracking.

**7. Offline Limitations**
- Many apps require internet at the gym.
- Gym wifi/cell signal unreliable; syncing fails silently.
- True offline-first apps are rare.

**8. Data Ownership Concerns**
- Users hesitant to trust 5+ years of data to a VC-backed app that might pivot.
- Limited data export options. Most apps don't offer CSV/JSON exports.
- No ability to port data to competitors.

**9. Mid-Session vs. Post-Session Logging Friction**
- Apps optimized for one or the other, not both.
- Chalky-hands problem: tapping forms mid-session is painful.
- Rich logging (voice notes, multiple details) happens post-session, but apps aren't built for lazy data enrichment.

**10. Limited Context Integration**
- No video logging of climbs for technique analysis (except Climbah).
- No location-based auto-detection (gym vs. outdoor).
- No integration with wearables (HR data, sleep data from Apple Health, Garmin).
- No social but not forced: optional sharing without a required feed.
