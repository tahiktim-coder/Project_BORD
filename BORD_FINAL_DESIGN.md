# BORD - Final Design Document
**Bureau of Right Decisions**
**February 28, 2026**

---

## 1. CORE PREMISE (One Sentence)

You are a night-shift case processor at BORD. You process 18 files. Halfway through, you realize you helped BORD murder 214 children.

---

## 2. BACKGROUND STORY

### What Happened
- **Facility 6** was a BORD detention center that operated for six years (2019-2025).
- 214 children were processed into Facility 6 under intake authorization codes stamped by night processing clerks — including the player.
- Children underwent unauthorized surgeries (organ harvesting). Dr. Rask signed every death certificate as "cardiac arrest."
- Director Alistair Crane ordered the program. Bodies were removed by trucks at night.
- Facility 6 was shut down last month. BORD claims "structural failure." Families say otherwise.
- The player was previously named Henrik Voss. They were reassigned to night processing under a new identity after Facility 6 closed. They do not remember — or choose not to.

### How the Story Reveals Itself

The 18 cases are structured as a **slow revelation in three acts**:

| Shift | Theme | What Player Learns |
|-------|-------|--------------------|
| **Shift 1 (Cases 1-5)** | "The Normal" — routine bureaucracy | Facility 6 existed. Something happened there. Trucks left at night. Someone wrote about it. A doctor treated a girl missing both kidneys. |
| **Shift 2 (Cases 6-11)** | "The Unraveling" — it gets personal | A janitor found a hidden door. A 16-year-old is asking WHERE ARE THE TRUCKS GOING. YOUR OWN FILE appears under a different name. A Facility 6 clerk filed intake forms for every child. Witnesses gave depositions. |
| **Shift 3 (Cases 12-18)** | "The Collapse" — you are complicit | The boy from Facility 6 is still hiding. The doctor signed 214 death certificates (youngest was four). YOUR FILE again — YOUR stamp is on 214 intake forms. The director is in this building. Staff have stopped working. A blank file arrives. The final testimony file — everything, every truck, every surgery, every child. |

**Key Principle**: Each case's horror must be understandable *on its own*, at skim speed. The player should never need to remember details from earlier cases to understand the current one. Cross-case connections are bonuses, not requirements.

---

## 3. GAME FLOW

```
TITLE SCREEN → "Begin Shift"
     ↓
INTRO TEXT (6 lines, click-to-advance)
     ↓
FORCED LOOK-UP (teaches mechanic: "The office is working. Everything is in order.")
     ↓
SHIFT 1: 5 cases
  → After each case: choice (evil=stamp ritual, mercy=paper slides off)
  → Between choices: SPACE to look up at office (eyes, events)
  → TAB to toggle BORD Manual
     ↓
NEWSPAPER (consequences of Shift 1 choices)
     ↓
SHIFT 2: 6 cases (pressure increases, personal cases)
     ↓
NEWSPAPER (Facility 6 story building)
     ↓
SHIFT 3: 7 cases (memo is blank, you are alone)
     ↓
ENDING (one of 6 paths based on choices)
```

### Per-Case Flow
```
1. Case file appears on desk (paper-place sound, typewriter detail reveal)
2. Player reads case (name, occupation, allegation, detail)
3. Player may check BORD Manual (TAB) for regulations
4. Player may spot irregularity (clickable text → loophole picker)
5. Player makes choice:
   - EVIL: Stamp ritual (hold-to-stamp, stamp sound, red text feedback)
   - MERCY: Paper slides off (mercy echo text, anticipatory sound)
   - LOOPHOLE: Reduced suspicion cost + VOID stamp + "Procedural irregularity confirmed."
6. Suspicion updates. Events queue. Office responds.
7. Player may look up (SPACE) → sees escalating horror
8. Next case arrives.
```

---

## 4. FEEDBACK SYSTEMS

### Current State
The game has feedback, but it's inconsistent and hard to read:
- Evil choices get: stamp ritual + compliance text ("Your compliance is noted") + evil line
- Mercy choices get: paper slides off + mercy echo (gray text, 2.2s) + lamp dim + typing pause
- Loophole success gets: VOID stamp + "Procedural irregularity confirmed." + lamp brighten
- Suspicion is tracked but poorly communicated — threshold messages exist but are easy to miss

### Design Philosophy (Inspired by Papers Please + Mortuary Assistant)

**Papers Please taught us**: Silence is the best positive feedback. When you comply, nothing happens — that's the reward. When you deviate, the world punishes you. The ABSENCE of consequence IS the feedback.

**Mortuary Assistant taught us**: The job is the game. Horror happens in your peripheral vision WHILE you're doing your job. You don't stop to be scared — you're scared while working. The "possession meter" (Paper and Pencil) is diegetic — it looks like part of your job.

**Applied to BORD**:

#### 4A. Evil Choice Feedback (BORD Approves)
- **Stamp ritual** (hold-to-stamp with growing delay): The physicality IS the feedback. Holding longer = feeling it more.
- **Compliance text** appears briefly: "Your compliance is noted." / "Efficiency logged." / Shift 3: silence (BORD no longer acknowledges you).
- **Stamp reverb** grows across the game: room sounds emptier.
- **Post-stamp typing silence** (500ms): the room heard the stamp. Then typing resumes.
- **Lamp flicker** on stamp impact.
- **Red corruption**: screen tint shifts red with consecutive evil choices (starting case 8+).
- **KEY INSIGHT**: Evil should feel efficient and mechanical. The game rewards compliance with *smoothness*. No friction. That's the horror.

#### 4B. Mercy Choice Feedback (BORD Disapproves)
- **Paper slides off** (no stamp required — mercy is quiet, undramatic).
- **Mercy echo** text: case-specific consequence glimpse, gray, 2.2 seconds. ("A vendor returns to his corner. His daughter is watching.")
- **Room response**: Typing stops for 800ms. Lamp dims 60%, then recovers. The office *noticed*.
- **Anticipatory sound cue**: chair scrape / footstep / breath — something moved in the office while you were reading.
- **Suspicion increases**: +5 to +50 depending on the case. Early cases have 1.5x multiplier.
- **KEY INSIGHT**: Mercy should feel dangerous. The room goes quiet. Something moved. You chose wrong (from BORD's perspective) and the environment tells you.

#### 4C. Loophole Feedback (Procedural Exploit)
- **Discovery**: Click irregular text → warm resonance sound (lock tumbler + major third chord).
- **Reason picker**: 4 options, only 1 correct. Wrong = dissonant buzz + red flash + case re-renders.
- **Success**: VOID stamp (green) + "Procedural irregularity confirmed." + lamp brightens + filing cabinet click + perfect fifth chord.
- **Reduced suspicion**: only +5 instead of normal mercy delta. Witness loophole counts as evil (-20).
- **KEY INSIGHT**: Loopholes should feel like outsmarting the system. The warm sound, the lamp brightening — BORD can't punish what its own rules authored. This is your weapon.

#### 4D. Suspicion Feedback (Environmental Escalation)

**The "lookUp" system IS the feedback meter.** Instead of a HUD number, the player reads suspicion by LOOKING UP from their desk:

| Suspicion | Watcher State | What Player Sees | What Player Hears |
|-----------|--------------|-------------------|-------------------|
| 0-5 | calm | Normal office. Everyone types. | Full ambient: typing, shuffling, murmurs, phones |
| 5-30 | noticed | A few workers stopped typing (~2% eyes) | Murmurs cut at 20, shuffles at 30 |
| 30-55 | watched | ~30% red eyes in the dark. Threshold: "The office has grown quiet." | Typing thins 2x. Paper shuffling stops. |
| 55-80 | targeted | Close red eyes + aisle figure. Threshold: "Someone is walking toward you." | Typing 4x slower. Phones stop. Pen scratches stop. |
| 80-100 | converged | ALL eyes on. Monitor flashes red. Threshold: "Every key in the building has stopped." | Typing 10x delay. Near silence. Only drone. |
| 100 | TERMINATED | Forced lookUp → heartbeat → red flash → head drops | Heartbeat accelerating → impact thud |

**This persists during the shift.** Once you hit "watched," the office STAYS quiet until next shift. The environment is a ratchet — it only gets worse within a shift. Between shifts, 40% suspicion carries over and all visual events reset (so tension can rebuild).

**DECISION: LookUp feedback persists during shift.** This is the correct design because:
1. It creates dread — once the office goes quiet, it stays quiet
2. It makes the next mercy choice scarier — you KNOW they're watching
3. Reset between shifts gives the player false hope ("maybe they forgot")
4. Mortuary Assistant uses the same pattern: haunting escalates within a shift, resets between bodies

### 4E. What Changes Between Cases vs. During Shift

**Per-choice (resets each case)**:
- Eyes re-roll probability (dirty flag)
- Pending narrative events queue
- LookUp count resets
- Mercy echo / evil compliance text

**Per-shift (persists until shift transition)**:
- Watcher state (calm → converged)
- Audio environment (typing cadence, ambient sounds gating)
- Fog density
- Monitor color
- Suspicion pulse on case file edges
- Fired narrative events (headTilt, torsoRotate, lightsDie — these are permanent within a shift)

**Per-game (permanent)**:
- Red corruption tint (partially sticky between shifts)
- Stamp reverb length
- Stamp hold delay
- Breakout path tracking

---

## 5. THE BORD MANUAL

### Design
A **tab at the top of the case file** toggling between "Case File" and "BORD Manual". Contains 8 dry bureaucratic regulations (R1-R8). Each directive shows a subset of 2-4 rules.

### Purpose
The manual makes loopholes **deducible**. Without it, the player has zero information to find irregularities. With it, each loophole maps to a specific rule:

| Case | Irregularity | Rule | How Player Deduces It |
|------|-------------|------|----------------------|
| Okonkwo (2) | Date shows 03.02, directive is 04.02 | R1: Pre-dated filings invalid | Date mismatch → filed before today |
| Kader (3) | "age 8" in allegation | R3: Under 12 covered by parent's residency | Child is under 12 → no violation |
| Brandt (4) | Case ID "7496-D" but charge is "Class A" | R2: Case ending must match charge type | -D ≠ Class A → wrong suffix |
| Wojcik (6) | "Night Janitor, BORD Annex B" | R6: Building staff access all floors | Janitor has clearance → no trespass |
| Lena Selby (7) | "Age 16" in occupation | R4: Under 18 cannot be processed | Minor → cannot process |
| Osei (9) | "no signature" in detail | R7: Unsigned orders not valid | Missing signature → invalid order |
| Witnesses (11) | "Second appearance" in detail | R7: Duplicate case files not valid | Same file twice → filing error |
| Nadia Kader (12) | "Third offense" but only 1 prior exists | R7: Mandatory sentencing needs complete chain | Missing priors → can't apply mandatory |
| Your file (14) | Case ID "7532-C" but you're Level 3 staff | R2: Staff files need -L suffix | -C ≠ -L3 → wrong format |

**Shift 3 shows ALL 8 rules** (you're on your own — the directive is blank).

### Interaction
- **TAB key** toggles between Case File and BORD Manual
- Manual content changes per directive (not per case)
- Non-loophole regulations are included so the manual doesn't scream "THE ANSWER IS HERE"

---

## 6. NARRATIVE EVENTS (The Horror)

Horror events are **one-shot scares tied to mercy choices**. They fire during the next lookUp after a mercy choice. Each can only fire ONCE per shift (reset between shifts).

| Trigger | Event | Description |
|---------|-------|-------------|
| Case 1 mercy | deskVisitor | Desk objects shift while you're looking up (scraping sound) |
| Case 2 mercy | headTilt | Workers with red eyes slowly tilt heads to the same side |
| Case 3 mercy | closeUpWatcher | Figure standing RIGHT at your desk, slit red eyes |
| Case 4 mercy | torsoRotate | ALL workers silently rotate to face you |
| Case 5 mercy | theBlink | Total blackout 1.2s → ALL eyes ON when lights return |
| Case 6 mercy | lightsDie | Lights die row by row from back to front (electrical pops) |
| Susp ≥ 40 | aisleJump | Aisle figure jumps closer |
| Susp ≥ 70 | theApproach | Eyes rush toward you, 4s, camera locked |

**Entity Precedence**: Only ONE aisle figure visible at a time. Priority: approachFigure > closeUpWatcher > aisleWatcher.

**KEY INSIGHT (from Mortuary Assistant)**: These events happen WHILE the player is doing their job. You don't stop processing to be scared. You look up from your desk, see the horror, look back down, and the next case is waiting. The mundane and the monstrous coexist. That tension is what makes bureaucratic horror work.

---

## 7. ENDINGS

### Ending Paths

| Ending | Condition | Title | Tone |
|--------|-----------|-------|------|
| **SACRIFICE** | Zero evil choices + caught at 100 suspicion | PROCESSED → UNSEALED | The "true" ending. You saved everyone but got caught. PROCESSED morphs to UNSEALED as testimony enters record. |
| **UNSEALED** | Zero evil choices + survived | UNSEALED | Mathematically very difficult. Same as sacrifice but you survive. |
| **PROCESSED** | Caught at 100 suspicion (with evil choices) | PROCESSED | Dragged away. The system ate you. |
| **EXEMPLARY** | All 18 condemned | EXEMPLARY | Perfect compliance. A nicer lamp. A larger desk. You don't think about Facility 6. |
| **ALMOST** | 11-17 saved | ALMOST | Almost everyone saved. Your replacement is already here. |
| **SHIFT COMPLETE** | 1-10 saved | SHIFT COMPLETE | You tried. The machine grinds on. |

### The Sacrifice Path (Design Intent)

This is the intended "true" ending on a second playthrough:
1. First playthrough: Player doesn't know about the manual, doesn't find loopholes, gets caught or compromises. Learns the story.
2. Second playthrough: Player uses the manual, finds loopholes (reduce suspicion cost), commits to zero evil choices. Hits 100 suspicion in Shift 3 and gets caught.
3. PROCESSED appears → 5 seconds of despair → lights return → eyes turn off → UNSEALED appears → testimony is entered.

The mathematical design ensures this path REQUIRES loopholes:
- Pure mercy without loopholes: suspicion hits 100 by mid-Shift 2 (too early)
- With loopholes: suspicion can be managed into Shift 3 (where the testimony file awaits)

---

## 8. WHAT'S WORKING WELL

1. **Stamp ritual**: The hold-to-stamp mechanic with growing delay is excellent. Making the player physically participate in condemnation is the game's best feature.
2. **Audio ecosystem**: 9 procedural sound layers that gate with suspicion create a living office that dies around you. The silence IS the horror.
3. **Story pacing**: The 18-case structure with two newspaper breaks creates natural act breaks. The Facility 6 reveal is properly horrifying.
4. **Shift 3 degradation**: Blank directive, stamp text dissolving, paper whitening — the system is breaking down.
5. **Dynamic callbacks**: Brandt→Crane and Nasir→Rask connections reward attentive players without punishing inattentive ones.
6. **Typewriter reveal**: Reading the detail text letter-by-letter forces the player to sit with the information.

---

## 9. WHAT NEEDS IMPROVEMENT

### 9A. CRITICAL: Difficulty & Win Condition Clarity

**Problem**: The player doesn't understand what "winning" means. There's no goal communicated.

**Fix**: The intro text already says "Process the cases. Follow the directive. Consult the BORD Manual." This is intentionally ambiguous — the game doesn't tell you to save people. But the ENDINGS should make the player want to replay:
- **End screen should show Loopholes Found: X / 9** (currently shows this)
- **On second playthrough**, intro should add one extra line: "You have been here before." (already handled by `_hasPlayedBefore`)
- **Hint text** on loophole hover already says "Something in this file doesn't match the regulations." (nudges toward manual)

**No further changes needed here.** The ambiguity is the design.

### 9B. MEDIUM: Suspicion Communication

**Problem**: Player doesn't know what the threshold messages mean or that they're in danger.

**Current state**: Three atmospheric messages fire at 30/55/80 suspicion. Visual indicators exist (fog, monitor color, lamp flicker, case file shadow) but player doesn't know what they mean.

**Assessment**: This is intentionally opaque — the game teaches through consequence, not UI. The threshold messages ("The office has grown quiet" → "Someone is walking toward you" → "Every key in the building has stopped") are a clear escalation. Combined with the lookUp visual feedback (more eyes, aisle figure, typing dying), the player SHOULD feel the danger.

**Possible improvement**: On the end screen after being caught, add a line: "They were watching you the whole time. Next time, check the regulations." This nudges toward the manual for the second playthrough.

### 9C. LOW: Pacing in Shift 1

**Problem**: First 5 cases can feel like a tutorial with no stakes.

**Current mitigation**: 1.5x suspicion multiplier on first 5 cases, forced lookUp after first mercy choice, deskVisitor event.

**Possible improvement**: None needed. The "boring" feeling is intentional — it makes the unraveling in Shift 2 hit harder. Papers Please has the same structure: mundane → wait is that → oh no.

### 9D. MEDIUM: Newspaper Readability

**Problem**: Newspaper headlines between shifts are dense and easy to skim past.

**Assessment**: The newspapers currently animate in with staggered delays (300ms between elements). They respond to player choices (saved vs. condemned each case). The content is good but could benefit from clearer visual hierarchy.

**Possible improvement**: Bold the most important headline. Reduce total headlines to 3-4 max (currently can show 5+). Not critical.

---

## 10. PROPOSED MAJOR CHANGES

### Change 1: End Screen "Next Time" Nudge

After a non-SACRIFICE ending, add a final line to the stats:

- If caught with evil choices: `"They were watching. Check the regulations next time."`
- If survived with mixed: `"Loopholes Found: X / 9 — Some cases had irregular paperwork."`
- If EXEMPLARY: `"Not a single deviation. Not a single thought."`

This nudges the player toward the manual on their second playthrough without being a tutorial.

### Change 2: Loophole Hint Improvement

Current hint text when hovering irregularity: "Something in this file doesn't match the regulations."

**Change to**: Make the irregularity text slightly visually different — a barely-perceptible color shift (#2a1a1a instead of #1a1a1a) so attentive players notice something is "off" even before hovering. Combined with the paper crinkle hover sound, this creates a discoverable system.

### Change 3: Stamped Archive at Ending Emotional Weight

The stamp archive (scrolling through condemned names) is excellent but currently only shows names.

**Proposed**: Show each name with their one-line consequence from the newspaper. "Arthur P. Selby — DETAINED. Property seized." This makes the player sit with what they did, name by name.

### Change 4: Second Playthrough Intro Variant

Currently `_hasPlayedBefore` adds "Again." to some case details.

**Proposed additional intro line**: After "BORD is watching. Begin." add: "You have sat at this desk before." — One line. Confirms the loop. The player knows they're replaying but the CHARACTER also seems to know.

---

## 11. INSPIRATIONS APPLIED

### From Papers Please
- **Silence as positive feedback**: Evil choices are smooth and frictionless. The game never judges you for complying.
- **Delayed consequences**: Mercy choices don't immediately punish — they queue environmental changes that manifest on the NEXT lookUp.
- **No morality meter**: The game never tells you what's "good" or "evil." The stamp says PROCESSED whether the person deserves it or not.
- **Efficiency trap**: The efficient path (evil) is the easiest path. Mastering the game means mastering compliance. The horror is that you're good at it.

### From Mortuary Assistant
- **Job-as-game**: Processing cases IS the gameplay. Horror is peripheral — it happens WHILE you work, not instead of working.
- **Diegetic possession meter**: Suspicion is readable through the environment (eyes, typing, fog), not through a UI element. Like the Paper and Pencil in Mortuary Assistant, the player must actively CHECK (look up) to read their danger level.
- **Haunt escalation within shifts**: Events escalate per shift, reset between shifts. Each shift is a fresh "body" with its own tension arc.
- **Multiple endings reward replay**: Knowing the loopholes exist (from the manual) motivates a second playthrough to find them all.

### From Obra Dinn
- **Fragment revelation**: Each case reveals one piece of the Facility 6 story. No single case tells the whole truth. But each case is self-contained enough to understand on its own.
- **The player does the detective work**: The manual gives you the RULES. The cases give you the FACTS. You connect them. The game doesn't tell you "this is a loophole" — you figure it out.

---

## 12. TECHNICAL NOTES

- **File**: `C:\Users\farha\Claude\BORD\prototype_3d.html` (~5900 lines)
- **Also**: `index.html` (copy for GitHub Pages)
- **GitHub**: `https://github.com/tahiktim-coder/Project_BORD.git`
- **GitHub Pages**: `https://tahiktim-coder.github.io/Project_BORD/`
- **Engine**: Three.js v0.162.0 + EffectComposer + custom noir GLSL shader
- **Audio**: Web Audio API, fully procedural (9 ambient layers + sound effects)
- **Target**: ~30-45 minutes per playthrough, designed for 2 playthroughs

---

## 13. IMPLEMENTATION PRIORITY

If making changes, prioritize in this order:

1. **End screen nudge text** (5 lines of code) — highest impact for replay motivation
2. **Irregularity visual hint** (2 CSS lines) — makes loopholes more discoverable
3. **Second playthrough intro line** (1 line of text) — confirms the loop
4. **Stamp archive with consequences** (~30 lines) — emotional weight at ending
5. **Newspaper trimming** (~10 lines) — reduce to 3-4 headlines max

Everything else in the current build is working as designed. The core loop (read → choose → look up → dread → next case) is solid. The manual system makes loopholes deducible. The audio ecosystem creates a living office that dies around you. The story reveals itself at the right pace.

**The game is close to done. These are polish changes, not structural ones.**
