# Worked Example — Product Feature Ideation

**Prompt**: "Improve user retention for a language-learning app."

---

## Phase 1 — Frame

```
## Problem Statement
A language-learning app has 70% Day-1 retention but 12% Day-30 retention. Most churned
users report "lost motivation" or "got too busy." Find product feature ideas that
intervene before churn rather than reactivating after.

## Domain
product
```

## Phase 2 — Reframe

```
## Reframes
1. (False Faces) "Users want to learn the language" reversed → users want to FEEL like
   someone who's learning the language; the identity, not the skill.
2. (True/False) The premise "we should reduce friction" is assumed; reduced friction may
   correlate with reduced commitment. What if PRODUCTIVE friction is the goal?
3. (Slice and Dice / role) The user isn't the only stakeholder — partners, parents,
   employers, language-community members all have stake in the user's progress.

**Selected reframe(s):** #2 (productive friction) — strongest divergence from
"reduce churn = reduce friction" baseline.
```

## Phase 3 — Diverge

```
**Seed:** 3319 (mod 5 = 4; favorites_value = 3; favorites = EXCLUDED)
**Selected frameworks:** analogous-domain [semantic], think-bubbles [structural],
brutethink [random-stimulus, word: "monastery"], false-faces [inversion],
phase-separation [structural — wildcard]
```

### Analogous Domain (map to: physical-therapy adherence)
PT patients also face long-horizon habit programs with high drop-off. Borrowed mechanisms:
1. Prescription model — a clinician writes the language regimen; the app enforces it (asymmetry of authority)
2. Re-injury fear — explicit "your previous progress will degrade" warnings before extended absences
3. Home-exercise logbook — analog journal companion that lives off-screen; daily one-line entries
4. Discharge ceremony — explicit graduation moment at 12 weeks; alumni status conferred
5. Insurance-coverage framing — app subsidized by employer wellness budget; opt-out has a cost

### Think-Bubbles (cross-branch jumps)
First-order branches: motivation, time, social, identity, memory, environment.
Cross-jumps:
1. (motivation × environment) lessons that physically alter the user's environment — sticky notes auto-printed, room lighting changes
2. (identity × social) progressing earns the right to ADD A LANGUAGE ARTIFACT to a public personal page
3. (memory × time) pre-sleep micro-lessons during the 5 min before lights out, hijacking dream rehearsal
4. (social × motivation) a "language buddy" auto-assigned by failure pattern overlap; both sides motivated to stay

### Brutethink (monastery)
Properties: silence, ritual, hours, vows, communal meals, copying-as-learning, illuminated manuscripts.
1. Vows of silence in target language for designated hours
2. Daily ritual scheduled at fixed time (matins-style); missing it is counted publicly within the cohort
3. Copying-as-learning: users handwrite a daily passage on paper; app verifies via photo
4. Illuminated manuscripts: each completed week generates a beautiful artifact-page the user keeps

### False Faces (assumption reversal)
1. Reverse "users should be motivated" — users should be DEMOTIVATED at the right times so the rebound creates commitment
2. Reverse "lessons should fit any time" — lessons must happen at fixed inconvenient times; absence has cost
3. Reverse "users want progress" — users want PLATEAUS where mastery deepens
4. Reverse "the app should be available always" — app is unavailable except 1hr/day; scarcity drives ritual

### Phase Separation (wildcard)
Pool A: better streaks, smarter notifications, gamified XP — typical retention features.
Pool B (asymmetric):
1. Tuition-style commitment: pay $50 upfront, refunded only if Day-30 retention earned
2. Cohort-locking: 12-week fixed cohort; you cannot leave without dropping all friends; social cost of churn
3. Pre-commitment to a public language-output event 90 days hence; the app drives toward that event
4. App requires the user to teach a beginner once a week as the price of access

## Phase 4 — Cross-pollinate

Hybrids:
1. **Monastic Cohort** — Brutethink's ritual hours + Phase Separation's cohort-lock = a 90-day cohort that meets daily at fixed hours for 30 min; missing it ejects you publicly.
2. **Manuscript Portfolio** — Think-Bubbles' identity-artifact + Brutethink's illuminated manuscripts = each week produces a printed/digital page the user can show; portfolio is the retention loop.
3. **Sleep-Buddy Pair** — Think-Bubbles' pre-sleep + Phase Separation's buddy = paired users do 5-min pre-sleep lesson via voice; both fall asleep on the call. Trust + adherence loop.
4. **Productive Demotivation** — False Faces #1 + Phase Separation's pre-commitment = app DELIBERATELY interrupts streaks to test motivation; rebounds count more than streaks.
5. **Inverse Availability** — False Faces #4 + Brutethink's matins = app open only 5am-6am AND 9pm-10pm. The constraint becomes the ritual.
6. **Discharge Graduation** — Analogous-Domain's PT discharge ceremony + Think-Bubbles' identity-artifact = explicit 12-week graduation moment with alumni status; identity transition is the retention loop, not the lessons themselves.

Worst Possible Idea pass: "App that aggressively shames users for missing days." Insight: shame fails but ACCOUNTABILITY-AS-CARE works. Legitimate form: someone in the app's community visibly notices when you go quiet and reaches out.

## Phase 5 — Surface

```
## Curated Ideas

### Direction A — Productive Friction
1. **Monastic Cohort** — fixed 30-min daily ritual within 90-day cohort; public absence
   tracking. [hybrid #1]
2. **Inverse Availability** — app open only at 2 fixed daily windows. [hybrid #5]

### Direction B — Identity & Output
3. **Manuscript Portfolio** — weekly beautiful artifact-page; user-shareable.
   [hybrid #2]
4. **Public Language-Output Commitment** — pre-committed 90-day-out language event;
   app drives toward it. [Phase Separation Pool B #3]

### Direction C — Social Mechanics
5. **Sleep-Buddy Pair** — paired 5-min pre-sleep voice sessions. [hybrid #3]
6. **Teach-To-Earn-Access** — weekly teaching of a beginner gates the user's access.
   [Phase Separation Pool B #4]

### Loonshot Candidates
1. **Productive Demotivation** — App actively breaks streaks to test commitment;
   rebounds reward harder than uninterrupted streaks.
   Looks fragile: counterintuitive; users may rage-quit |
   Asymmetric upside: turns the "lost motivation" failure mode into the engine of
   retention; if it works, it's a category-defining mechanic. [hybrid #4]
2. **Vows of Silence** — Designated hours where you may only speak/think in target
   language; broken vows tracked.
   Looks fragile: can't be enforced; users may cheat |
   Asymmetric upside: produces fluency 2-3× faster than passive practice; positions
   app as serious-learner tier. [Brutethink #1]

### Notes
- Reframe most generative: #2 (productive friction). Almost all curated ideas trace to it.
- Frameworks contributing most: Brutethink (monastery), Phase Separation Pool B,
  Analogous Domain (PT adherence).
- Dropped on devil's advocate: "tuition refund if retained" (creates wrong incentive
  for app to make false claims of completion); "auto-language-buddy" (hard to
  algorithmically match well; fails silently).
- Caveats: none from Phase 1.
```
