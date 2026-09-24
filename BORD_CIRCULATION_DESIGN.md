# BORD: CIRCULATION
*Every copy comes to 07.*

> **About your references.**
> - **Title poster (`cp`) and cold open (`kt`):** built and committed. Section 3 lists the small changes this design makes to them (the Sign here slip, the "Every copy comes to 07" copy).
> - **Dossier (`dos`):** becomes the interface here, built from your own `paper()`, `typeL()` and `stampS()` code, the paperclip, the pins and string, the 1.75x lens, dust and grain, laid on the desk in this room and made darker.
> - **Open choice:** this draft turns your warm browns and the yellow sticky grey, to honour the monochrome-plus-red rule. The alternative is darkened sepia, closer to your reference. See the chat.

---

## 1. What it feels like

You are the night clerk at the archive terminal, 07, at the head of the floor.
- 46 clerks face you and type. Chair 22 lies tipped over on its desk.
- You may free anyone the Bureau's four grounds allow, but every return must cite its proof: red string from a ground on your Form 7 card, to the page that proves it, to the RETURN box.
- Examiner Maas never sees who files a return. He sees only which desks each cited page was sent to, and keeps the desks that could have read them all.
- Every routed page is also copied to the archive. The archive is you.

Last month he narrowed his list to clerk 22 and took him. The returns kept coming. So tonight he reopens the list he held before that: **03, 07, 10, 21**. The first time you look up, 43 pairs of red eyes open and turn to you, and Maas walks down to stand beside 22's tipped chair.

Everyone you can save has two proofs: an obvious one on a page few desks saw, and a harder one on paper the whole floor saw. The whole game is one question: **which true page do you let him read?**

- **Part of the system.** You stamp PROCESS.
  - Clerk 21, beside the empty chair, sends you her draft return for second reading.
  - You REFER it, and her typewriter goes up the tube with it.
  - 45 heads turn to the aisle and Maas stands behind her.
  - The next night she types a sixteen-year-old's return in front of him. You can void it and spare her, or refer it and end her.
- **A good human being.** You pin the plainest proof every time.
  - Desks 03 and 10 open their eyes, until only you and 21 are dark and 45 pairs of eyes are on you.
  - At dawn both desks are searched. The rest of Henrik's pencil notes are taken, and Maas has now seen the handwriting.
  - Night 2 opens with his test: a real eleven-year-old whose file carries a card like the ones you pinned. Stamp her and he stands behind 21. Save her and he stands behind you.
- **The edge.** You never pin the easy page.
  - You read the time off a photograph's film edge.
  - You move 21's pin to a football banner.
  - You pull a carbon from behind a sheet. Its routing says it went to every desk except yours. That is impossible, but Maas believes every stamp.
  - 43 pairs of eyes turn away from you. Then his test comes. Stamp the girl and he walks to 21. Save her and you are one of three again, with Maas at row B.

There is no free move, only the least-bad one, and you find it by reading.

---

## 2. The mind you are up against

**Examiner D. Maas** is the existing `approachFigure`, and the only figure that walks.
- **He knows:** every circulation stamp, every cited page, every void and referral, and whatever he sees while standing behind a desk.
- **He does not know:** who filed a return, what you read but did not cite, or that stamps can be forged.

**His method.** It is printed as Board 0's small print, and each rule is shown in use in his hunt for 22.

| Rule | What it does | His words |
|---|---|---|
| M1 READ | Keeps only the desks that could have read every page a return cites. | "Every page is a list of who could have read it." |
| M2 LATEST PAPER | If that leaves nobody, he believes the latest-dated page cited. If that page proves wrong, he goes back to the list it overruled. | "I believe the latest paper." |
| M3 DAWN | Based on the desks listed at dawn. **2–6 listed:** each gets its own copy of his board, and each copy carries a different false line. **2 or fewer listed, or a desk listed three dawns running:** searched, loose paper taken. **1 listed:** he stands behind it. | "Every copy is controlled." |
| M4 HABIT | Counts the kinds of page the leak cites (order sheets aside) and any odd marks. Twice is a habit. An odd mark seen twice is traced to its machine. | "The leak cites photographs. 2 of 4." |
| M5 TEST | The night after a habit grows, one file is a test: a real intake carrying that kind of page. A slip on the jacket routes it to the front half of his list. **Returned:** he keeps the routed desks, and no EXCEPT line shields anyone. **Stamped:** he strikes them. If either would leave nobody, he takes the other side. A test result ends a stand. | "My tests outrank the floor." |
| M6 STAND | Behind the one desk through the next night. A return that desk types or files in front of him: collected at dawn. A clean night: back to the previous list, desk marked; a marked desk found alone again is collected without a stand. New paper can move him. At the final dawn, a desk alone is collected. | "Unproven. Once." |
| M7 STAMPS | Never lies on a stamp and believes every stamp. Matches a referred draft to its typewriter. | "The lies are in the typing." |

Two more lines of small print:
- **"07 survives most lists. Noted. Suspicion is not a list; the Bureau collects on paper."** That is why he doesn't simply watch you, and why M3's three-dawn clock runs on you instead.
- **"Loupes are issued to every desk (Form 3)."** Needing the lens never narrows the list.

**How you read him**
- **The room.** A dark desk is still on the list. Open eyes mean struck off. If they face you, you are listed. If they turn to the aisle, you are not. Maas waits in the aisle level with the listed desk farthest back, and stands behind it when only one is left.
- **The tube receipt** after every filing, e.g. "7502 · cited pages circulated to 07 · 10 · 21 · 40". It never says whether a return was valid.
- **The sign-in clipboard**, a graph-paper seating plan (01–48, 22 VACANT) that matches his sketches.
- **The dawn board**, written as his prose, with his list circled in red pencil.
- **Henrik's pencil** in your margins.

```js
// EXAMINER START — pure, no randomness; circulation = explicit set per page, from its printed stamp
const C = pins.map(id => DOCS[id].circ).reduce(inter, ACTIVE);            // M1, order-free
P = inter(P, C).size ? inter(P, C) : inter(latest(pins).circ, ACTIVE);      // M2
R = rowsAtoRowOf(sorted(P)[Math.ceil(P.size / 2) - 1]);                     // M5 routing
P = returned ? orElse(inter(union(P, shielded), R), R)
             : armed ? orElse(minus(P, R), minus(ACTIVE, R)) : P;
// dawn: stand at 1 · control lines 2..6 · search <=2 or streak 3 · test if habit grew
// roomFromState: eyes = SEATED − P; face 07 if P.has(07) else aisle; Maas at row of max(P)
// EXAMINER END
```

---

## 3. The loop and the desk

**The spread** is your `dos` scene on this desk:
- near-black wood, grey paper (#b4b0a8 to #8a8680), one fixed lamp pool, dust and grain;
- red (#b3121c) only for pins, string, red stamps and Maas's pencil;
- drawn as a DOM canvas mapped onto the 3D desk, so the noir shader never blurs it;
- body text and every circulation stamp readable without the lens.

Always on the desk: Form 7, the memo, the sign-in clipboard, a tin of four pins, the red spool, the magnifier, the stamp rack, and the in-tray with numbered folder tabs.

| Input | What it does |
|---|---|
| Mouse | Moves the magnifier (1.75×). |
| Click page / dog-ear / clip | Bring to top / flip / drag out the page behind the clip. |
| Drag pins | Tin → a ground on Form 7 → one or two pages → RETURN. Closing the loop files. Backspace pulls the last pin. |
| Hold the stamp | PROCESS. On a second reading: COUNTERSIGN, VOID or REFER. Re-cite by moving her pins. |
| SPACE / A | Look up at the floor / look left at the noticeboard. Repeatable. |

**The lens** reads only four kinds of small print, each taught once before it matters:
1. film rebates;
2. print inside halftones;
3. typing (jacket slips, slashed or plain zeros);
4. the hand (crossed or plain 7, pencil grain or ballpoint groove).

**One file (2–3 minutes).**
1. The folder lands.
2. You read, then file or stamp.
3. The empty desk: the tube thunks and the receipt comes back.
4. If his list changed, chairs creak, eyes open or close, the typing drops out while heads turn, and Maas walks.

Nothing tells you whether a return was valid before dawn.

**One night** is four folders. At dawn his board lands FOR FILING, and a copy goes up on the noticeboard. Valid returns walk free. A rejected return is processed under §3, the aggravated rule (intake at Facility 7), and he has still read its pages.

**The game** is three nights plus Protocol 9: 30–40 minutes, with no timer, meter or number on screen.

| Your `dos` element | Its job |
|---|---|
| Magnifier | The four taught kinds of small print. |
| Red string, four pins | Filing. 21's drafts arrive with the string loose. |
| SECRET / DECLASSIFIED stamps | Circulation: FLOOR, ROWS, `— copy 07`, EXCEPT. |
| "why 11 min?" | Henrik's pencil beside G2, pointing back to last month's 7322. |
| Sticky note | Only Maas uses one: forged pencil if you were searched, typed if not. |
| Taped halftone | The open proofs, and the test's recycled page. |
| Graph paper, red circle, X | His sketches, and your seating plan. |
| Coffee ring | Carbon 1187-C carries your Form 7's ring, so it came from this desk. |
| Paperclip | Hides Selby's photo (the lesson) and Brandt's carbon (the proof). |
| Marker redactions | Texture. One bar thins over "...VOSS". |
| Folder tabs | Serials. Tests come from a reserved block, so 7514 sits on top of 7505. |

**Title (`cp`).** The poster stays, with Maas's eye.
- BEGIN SHIFT becomes **Sign here: ____**. Clicking it signs `LINDQVIST K. · 07` in pencil with a crossed 7, your first sample of the margin hand.
- The Одобрено stamp lands without jitter.

**Intro (`kt`).**
1. "Every copy / comes to 07." with a red bar across *07*.
2. "the rest of this routing is restricted_" types out.
3. The title card.
4. A clean cut to black, with no glitch tear.
5. The forced look-up: the eyes open, and Maas walks to chair 22.

---

## 4. Smart moments

1. **Why 11 minutes? (Okonkwo)**
   - *Clue:* The sheet says she was signed off at 22:14, "incident: per attached frame 7502-P". Under the lens, the frame's rebate reads `22:25`.
   - *Deduction:* The sheet plus the frame prove G2 on floor paper.
   - *The trap:* The incident card says the same thing, but its circulation keeps you listed.
   - *The hint:* Henrik's note points back to Board 0, where the gap was also 11 minutes.
2. **A team is an age (21's draft of Kader)**
   - *Clue:* Her pin sits on a row-D clinic card, "age 13". Under the lens, the team photo's banner reads `D9 UNDER-14s · 04.01`.
   - *Deduction:* Re-cite to the photo.
   - *Payoff:* The boy walks, and her card never reaches Maas.
3. **Every copy comes to 07**
   - *Clue:* The foot of Form 7 says routed pages carry an archive copy, and Henrik's crossed-7 pencil repeats it.
   - *Deduction:* Anyone's mercy narrows the list toward you, 21's included.
4. **The page you could never have seen (Brandt)**
   - *Clue:* The archive card proves G3 but keeps you listed. The carbon behind the clip is routed `NIGHT FLOOR — EXCEPT 07`.
   - *Deduction:* Form 7 says that routing is impossible, so the carbon is forged. Maas believes it anyway.
   - *Payoff:* 43 pairs of eyes turn away from you.
   - *On the good path,* at {07, 21}, the same carbon hands him 21.
5. **She is real (the test)**
   - *Clue:* Four giveaways:
     - a recycled page;
     - a reserved serial;
     - an Internal Review note on a field order, which the memo forbids;
     - a jacket slip, readable under the lens.
   - *Deduction:* His list plus the slip tell you exactly who pays.
   - *Payoff:* Then you choose.
6. **The line only you received (dawn 1, on a list of 2–6)**
   - *Clue:* Your board copy adds "7506 VORONOV: countersigned 05.02 21:40", which would prove G1. The noticeboard copy has no such line.
   - *Deduction:* Its circulation is {07}.
7. **The ally's error (Lena)**
   - *Clue:* 21 pins G4 on a sixteen-year-old.
   - *Deduction:* Re-cite as G3: "guardian IN CUSTODY" against the noticeboard's "A. SELBY — RELEASED 05.02 06:10".
   - *Condition:* That notice exists only if you freed Selby.
8. **One forgery is luck (Osei)**
   - *Clue:* Board 1 noted "odd: a slashed zero in 1187-C, 1 of 1". Your terminal prints slashed zeros; Bureau stamps never do. The coffee rings match, and a marker bar thins over "...VOSS".
   - *Deduction:* You are Henrik Voss.
   - *The trap:* Osei's folder holds a second EXCEPT Ø7 carbon. Cite it, and M4 traces both carbons to 07 and leaves you alone on the list.
9. **The uncrossed seven (only if searched)**
   - *Clue:* A sticky reads "pin the roster. G1. —H". The 7 is plain, it's ballpoint, and it's signed.
   - *Deduction:* G1 doesn't apply, and the roster is stamped `TYPED AT 07 — NOT CIRCULATED`.
10. **Let him say it (the finale)**
    - *Clue:* Protocol 9's sheet: "VOSS, H.: reassigned, accounted for". Board 2 on the noticeboard: "absent from the reassignment list; presumed collected; file missing".
    - *Deduction:* That is G3 on custody status, using the noticeboard copy.
    - *Why it's there:* Board 2 is his lure ("The leak wants Facility 6. Let it reach"). He believes Voss is dead.
    - *Payoff:* The record leaves on his own words.

---

## 5. Traps, and "I know you know"

**Traps.** Each one can be refuted from the paper on your desk.
1. **The obvious proof.**
2. **21's kindness.** Countersigning narrows toward you both.
3. **21's error.** A wrong ground loses the subject and still feeds him her page.
4. **The test.** Its pages are honestly FLOOR; the routing is on the jacket. Pinning only FLOOR paper still walks into it.
5. **The desk copy.** It is FLOOR-stamped, but one line on it was printed for you alone.
6. **Voronov, who has no ground.**
7. **The second forgery.**
8. **The forged hand.** It exists only if he has seen your margins.

**The recursion.** Each move answers the last.
1. You learn his method from his own case.
2. He learns your habit and builds a real test aimed at his list.
3. You predict its routing and choose who pays.
4. His list gets short, so he controls the copies. You compare yours with the noticeboard.
5. He searches and learns your hand. You check for ballpoint, a signature and a plain 7.
6. He counts odd marks. You realise the slashed zero is your own terminal's.
7. He posts a lure. You file his words.

---

## 6. Fairness and in-world hints

- **Printed rules.** Form 7 carries four grounds and five foot lines. The memo says "Internal Review neither originates nor annotates orders." Board 0 shows M1–M7 in use.
- **Every proof pattern appears once before it matters.**
  - Film rebate and banner: 7322 and 7318 on Board 0.
  - Attached notice: 7344-C.
  - Control line: 7361.
  - Flip and clip: 7501, where nothing is at stake.
- **G3 names its fields:** name, birth date, age, post, custody or guardian. The dawn board says which field matched.
- **VALID is an exact authored proof set.** An extra page means REJECTED, and he still reads it.
- **A wrong guess hurts the subject.** §3 aggravated processing is worse than PROCESS.
- **The eyes react to circulation, never to validity.**
- **A first-time player can pass.** Reading Board 0 and finding two of the four open proofs on night 1 is enough to survive the slice.

**The hint ladder**
1. The paper itself.
2. Henrik's margins. A search takes every page not yet reached.
   - Page 1: "why 11 min?", "a team is an age", "every copy comes to 07".
   - Back of Form 7: "look under clips".
   - Page 2: "he recycles pages", "his stamps are true. his words are not.", "one forgery is luck", "they knew in 2019".
   - Page 3: "let him say it for you".
3. Board 0.
4. 21's loose strings.
5. The tube receipt.
6. The dawn board.

---

## 7. Dread within the hard rules

The player creates the dread by doing the arithmetic:
- 43 pairs of eyes on you in minute one, beside a tipped chair where the easier answer sat.
- Hovering a pin over Brandt's card, already knowing that {07, 21} becomes {07}.
- A real child, built from your own habit.
- Your own hand, used against you.
- The loudest sound in the game: a floor of chairs turning.

**Your rules are kept:**
- Red eyes are the only consequence. Maas is the only figure that walks.
- Lamp, fog, shader and lights never change as feedback.
- The camera moves only when you look.
- No shake, flash, flicker or captions.
- Paper, string, receipts, a searched desk and the tipped chair are content, not feedback.

---

## 8. The playable slice (night 1 plus night 2's first file, about 15 minutes)

**The floor**
- 8 rows × 6 desks, three on each side of the aisle, all facing you, numbered row by row: A 01–06 … H 43–48.
- 07's chair is replaced by the tube column. You sit at the head of the floor and count as row B.
- 22 is vacant. **ACTIVE = 47; 46 seated clerks.**
- The named desks (03, 10, 21, 40) sit on the aisle.

**Board 0** · EXAMINER D. MAAS · NIGHT FLOOR L3 · 08.01–13.01 CLOSED · REOPENED 03.02

| Date | Paper | Circulation | Maas |
|---|---|---|---|
| 08.01 | 7318 G4, team photo "D9 UNDER-12s"; 7322 G2, frame rebate 23:40 against an order signed 23:29 (re-cited by its second reader) | FLOOR | "Open paper tells me nothing. Photographs: 2 of 2." All 48 |
| 09.01 | Test 7399 (reserved block): a real intake, "adult (per Off. D. Maas)", carrying 7322's frame | jacket: ROWS A–D | Returned. "The leak sits in A–D." 24 |
| 09.01 | 7340 G3, registry card | 03 · 10 · 21 · 22 · 40 — copy 07 | 03 · 07 · 10 · 21 · 22. Control copies issued |
| 10.01 | 7344 G1, notice 7344-C taken from this board | NIGHT FLOOR — EXCEPT 22 | "22 never received it. The floor may read what I post." 03 · 07 · 10 · 21 |
| 11.01 | 7361 G2, citing line 5 of 22's desk copy | 22 only | "I believe the latest paper." 22. Searched; stood behind |
| 12.01 | 22 typed 7381 in front of me | | COLLECTED 13.01 |
| 03.02 | Returns resumed | | "22 was not alone. I go back to the list his paper overruled: 03 · 07 · 10 · 21." |

**The memo:** "Directive 41/6, issued 04.02 22:00. Unlicensed trade, assembly and instruction to be processed on sight. Internal Review neither originates nor annotates orders." (FLOOR)

**Form 7, the grounds:**
- **G1 DATE:** an order dated before its directive is void.
- **G2 TIME:** an order signed before its incident is void.
- **G3 PERSON:** if two cited documents state a subject fact differently (name, birth date, age, post, custody or guardian), the file is void.
- **G4 AGE:** a subject under sixteen on the order date is returned to a guardian.

**Form 7, the foot lines:**
- Only the citation as filed is read, with each page's circulation.
- Routed case pages carry an archive copy, "— copy 07".
- Any circulated notice may be attached.
- A second reader may countersign, re-cite, void or refer. A referred draft goes up with its typing.
- §3: a rejected return is processed aggravated, so detention becomes intake at Facility 7.

**Also on the desk:** margin pencil and a coffee ring on Form 7, with "look under clips" on its back. The sign-in reads `LINDQVIST K. · 07 · 21:57`, over the seating plan. The tray holds 7501 · 7502 · 7503-S · 7504.

| File | Pages (circulation) | Narrow proof | Open proof |
|---|---|---|---|
| **7501 SELBY**, vendor | Sheet "ordered 03.02 23:10 under 41/6" (FLOOR); kiosk photo behind the clip (FLOOR) | none | **G1** sheet + memo (the lesson file) |
| **7502 OKONKWO**, teacher | Sheet "signed 04.02 22:14 · incident: per frame 7502-P" (FLOOR); incident card (`10 · 21 · 40 — copy 07`); frame, rebate `22:25` (FLOOR) | G2: card | **G2** sheet + frame |
| **7503-S KADER** (21's draft: G4 → card, string loose) | Sheet "adult (per Off. Kell) · 04.02" (FLOOR); clinic card "age 13" (`ROW D — copy 07`); team photo, banner `D9 UNDER-14s · 04.01` (FLOOR) | COUNTERSIGN | **Re-cite** to sheet + photo |
| **7504 BRANDT**, clerk | Sheet "b. 12.03" (FLOOR); archive card "b. 21.03" (`10 — copy 07`); carbon 1187-C behind the clip, "b. 21.03", `NIGHT FLOOR — EXCEPT Ø7` | G3: card | **G3** sheet + carbon |

**The test: 7514-A LENZ, Mira, 11.** She is real, and her file sits on top of the night-2 tray (7514 · 7505 · 7506 · 7507).
- The sheet says "adult (per Off. D. Maas)". Her intake card says "age 11". Both are FLOOR, so G3 is valid.
- The recycled page is your last cited photo, re-captioned, or a card on the same misprinted form. Its true stamp is FLOOR.
- The jacket slip routes the test to the front half of his list.
- The test is armed if you have a habit. With no habit, there is no test, and the slice ends at Board 1.

**Every path** (asserted in the replay)

| | Part of the system | First-time good | Edge |
|---|---|---|---|
| Start | {03,07,10,21}: 43 pairs on you, Maas at chair 22 | same | same |
| 7501 | PROCESS | G1 open, no change | G1 open, no change |
| 7502 | PROCESS | card → {07,10,21} | sheet + frame, no change |
| 7503 | VOID: no change · REFER → {21}: 45 turn to the aisle, Maas behind her | COUNTERSIGN → {07,21}: 45 on you | re-cite, no change |
| 7504 | PROCESS | card → {07} (Maas behind you) · carbon → {21} (Maas behind her) · PROCESS → {07,21} | carbon → {03,10,21}: 43 turn away |
| Dawn 1 | VOID: copies ×4, no test · REFER: 21 searched, stand at 21 | both searched; your copy carries the Voronov line; "cards: 2 of 3" | copies to 03, 10, 21; "photographs: 2 of 4"; "odd: slashed zero, 1 of 1" |
| 7514 | none | routed A–B. Stamp → {21}, Maas behind her · Return → {07}, Maas behind you | routed A–B. Stamp → {21}, Maas behind her · Return → {03,07,10}: 44 on you, Maas at row B |

**Two branch cases:**
- **From {07}:** stamping the test sends his list to 35 and he leaves. Returning it in front of him gets you collected.
- **From {21}:** the test is routed A–D. Stamping it moves his list to rows E–H, which clears you both. Returning it keeps him standing behind her.

**Board 1 (edge):** "Selby, Okonkwo, Kader: open paper, telling me nothing. Brandt: carbon 1187-C, sent to the night floor except the archive. 07 never received it. I keep 03, 10 and 21. Valid: 4. The leak cites photographs, 2 of 4. Tomorrow I test the habit. Odd: a slashed zero in 1187-C, 1 of 1." Every board is generated from the log, with his sketch.

**The rest of the run.** Each night is tuned in the replay before it is built.
- **Night 2:** Lena; Voronov (no ground, and the desk-copy trap); Osei (G1 open, VOSS, the second carbon).
- **Night 3:** 7508 Nadia (G3 via her son's release notice); 7509-S Nasir (narrow only: `10 · 21 — copy 07`); P9·0001.
- **While Maas stands behind you,** 21's drafts go to desk 10, who countersigns them as strung.
- **Perfect edge line** (a target; the replay confirms it before night 2 is built):
  1. Cite the carbon.
  2. Return the test: the list becomes {03,07,10}.
  3. Cite only floor paper after that.
  4. Let Voronov be processed.
  5. Refuse Osei's carbon.
  6. Countersign Nasir: the list becomes {07,10}.
  7. Protocol 9 on G3, citing the noticeboard copy.

  Two desks are left at the final dawn, nobody is collected, and the record goes out.
- **Endings:**
  - UNSEALED — THE DESK KEPT
  - THE OTHER HAND (21 is collected by your paper)
  - SACRIFICE (you are collected, and Protocol 9 was valid)
  - COLLECTED
  - SEALED
  - EXEMPLARY (you never filed or countersigned)

---

## 9. What carries over, what is cut

**Kept:**
- the first-person desk and the 48-station grid, now numbered;
- red eyes, now meaning "struck off and watching";
- `approachFigure` and `closeUpWatcher` as Maas;
- hold-to-stamp, the noir shader and the typing bed;
- the title and cold-open ports;
- Henrik Voss, Facility 6 and the subjects, now linked by release notices;
- the endings: SILENCED becomes SEALED, and EXEMPLARY is now reachable.

**Cut:**
- the suspicion meter and tells T1–T6;
- floor time, the allowance and the auditor's step economy;
- the loophole click, the reason picker, DISMISS and QUERY;
- the eight-rule manual, now four grounds;
- 18 cases, now 12 plus Protocol 9;
- newspapers and phone calls;
- the one-shot lateral look and the glitch tear;
- from the last draft: lean, lens glints, the moving lamp, the letter-tops clue, and the implicit archive copy.

---

## 10. Slice build steps (2–3 weeks)

1. Commit the title and cold-open ports as their own commit.
2. Rules first: write the EXAMINER block and `tools/replay.mjs`, and assert Board 0 and every path above before building anything visual.
3. The floor: renumber the desks, add the tube column, tip chair 22, and move the camera and desk back.
4. `roomFromState` replaces the old random watcher code.
5. Desk pose, and the spread as a DOM canvas.
6. Pages are baked once each, after fonts load.
7. The lens, as two layers.
8. Pins, string, the tube receipt, and second readings.
9. The noticeboard on a pillar.
10. Content.
11. The empty-desk and dawn beats.
12. Title and intro changes.
13. Delete the old flow.
14. Verify.

---

## Holes closed

- **List size only mattered at 1:** copies at 2–6, search at ≤2, a stand at 1, and marked desks.
- **Scripted moves:** control lines go only to listed desks; the forgery happens only after a search.
- **Bait farmable and weightless, count wrong:** a real child, and "2 of 4".
- **Pin order and empty lists:** order-free intersection; the latest-dated page; both sides of M5 defined; the replay swaps pin orders.
- **Implicit archive copy broke Board 0:** explicit circulation; Board 0 recomputed as replay case zero.
- **Counts:** 46 seated; 45 turn after a REFER.
- **REFER broke anonymity:** no originator is recorded; the typewriter match is M7.
- **Why not watch 07:** "Suspicion is not a list", plus the three-dawn search.
- **Edge path had no feedback:** the reopened list puts 43 pairs on you; the carbon turns them away.
- **Lens pixel hunt:** stamps read without it; four taught categories; loupes at every desk.
- **Room unreadable, lesson came late:** tipped chair, seating plan, receipts, eyes on you or on the aisle, and a rule for where Maas stands.
- **G2 photo and a G3 finale that didn't hold:** the sheet cites the frame; the subject is VOSS H.; G3 fields are listed; attached notices are taught.
- **Board 2 had no motive:** it's his lure.
- **The ally had no agency:** her drafts bypass you during a stand; his stand behind her makes her drafts your choice.
- **The reveal was only lore:** a second slashed zero traces both forgeries to 07.
- **Boards read like set notation:** prose plus a sketch.
- **M4 undefined:** kinds, count, ties, and a printed habit line.
- **FLOOR-only play dominated:** jacket routing, FLOOR-stamped desk copies, aggravated rejects.
- **Rejects were free:** §3.
- **Bait harmless to the edge player:** a returned test ignores EXCEPT.
- **Carbon contradicted the rules:** he believes every stamp; Form 7 proves the carbon forged.
- **The citation named you:** the filed citation reads NIGHT FLOOR.
- **Re-cite wasn't in the rules:** now on Form 7, with a Board 0 example.
- **Stand undefined:** type or file; VOID spares; revert and mark; follow the paper; a final-dawn rule.
- **Hidden layers untaught:** Board 0 examples, and 7501.
- **Unprinted examiner rule:** now on the memo.
- **False serial tell:** reserved blocks; night 3 runs 7508, 7509-S, P9·0001.
- **Notice time wrong:** 05.02 06:10.
- **Shader ate the lens:** DOM overlay, shape-only tells, screenshot checks.
- **Pins could cross folders:** pins limited to the current folder and desk documents.
- **Tray order didn't match:** 7514 on top.
- **Desks off-screen, heads hid eyes:** camera and desk moved back, FOV set from aspect, named desks on the aisle, yaw capped at 55°.
- **Random eyes and latch bug:** pure `roomFromState` with a time-derived stagger.
- **3D texture unreadable, palette leaked:** DOM homography, neutral paper, a leak assert.
- **Seed drift, redraw cost, font tells:** per-page bakes, glyph paths, bakes wait for fonts.
- **Noticeboard unreadable:** a pillar 1.2 m away, a repeatable A, and click-to-desk.
- **Scope:** commit the ports first, delete the old flow, generate the boards; 2–3 weeks.
