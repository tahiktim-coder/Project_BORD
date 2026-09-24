# BORD: UNDER REGULATION

A pivot design for `C:/Users/farha/Claude/BORD/prototype_3d.html`. **Revision 2.**

It builds on the winning "Review Queue" proposal and folds in the judges' grafts. It replaces the hidden suspicion ledger. This revision closes the 25 holes found by three reviews. §11 lists each hole and the change that closes it.

It supersedes sections 4D, 7 and 13 of `BORD_FINAL_DESIGN.md`. Those sections claim a 40% carry, a 1.5x tax, a +5 loophole cost and "requires loopholes"; all four are already wrong against the code.

The case data was checked against lines 1101–1431 of the game file. The manual text in §5.1 replaces `BUREAU_RULES` (1422–1431).

---

## 1. The vibe in one page

BORD stops judging the player's heart and starts reading their paperwork.

- Any file that leaves the desk can be pulled for review by a colleague the player can see.
- The player is never told at the desk whether they were right.
- They find out one file later, on the empty desk between papers. Either a carriage returns and a keyboard rejoins, or a chair scrapes and one step comes from the aisle.
- Being right is not free. Every review the Bureau reads brings the man in the aisle closer. When he reaches the desk, he takes the evidence you have been keeping.

**What each path feels like**

- **Part of the system.** Stamp. The room reads your stamps only when you stamp without lifting the card, and a player learns that on the first file. For two shifts the rest is the hand:
  - the stamp hold gets longer, and its echo gets longer;
  - a ledger is printed under your terminal number;
  - a daughter's file quotes the minute you processed her father.

  In shift 3 the directive is withdrawn and every stamp is read against the manual. Obedience was never a regulation.
- **A good human being.** Save everyone a rule covers, and learn the manual to do it. Every saving the Bureau reads costs two steps. You reach the last files with the auditor standing at your desk. He has taken the pages you kept, and you can name every act that brought him. You leave alive with the truth sealed, or you sign it out under your own name and do not leave.
- **The edge.** Save the people who carry the record and process the ones who don't. Cite the rules the Bureau can't fix. Read, then wait for your neighbour's keys before you file. Walk out with the packet and keep the desk. Every step of margin is paid for with someone else's stamp. On the canonical run the choice is Lena or the sixth page.

**What a first run feels like, and when**

| Time | What happens | What the player feels |
|---|---|---|
| 0:00 | Forced look-up: 48 clerks typing, a noticeboard, and a man at the far end of the aisle who is not typing. No caption. The first paper waits on the desk while the manual is open. | "This is what normal looks like." |
| ~2:00 | You spend a minute on Selby and let him go. Before the next paper lands: a pneumatic thunk ahead and to the left, a file sliding onto a desk, one keyboard stopping. The desk stays empty until you look up: two red points bent over your file. (Stamp him without lifting his card and the same thing happens. The Bureau reads careless stamps too.) | Watched, specifically, for something you just did. |
| ~3:30 | Before the paper after that lands, either her carriage returns and her keys rejoin, or a chair scrapes and one step comes from the aisle. | You learn to listen to the empty desk between files. |
| ~8:00 | Ledger 1 arrives: the Bureau's form lists each filing and the habit that got it read ("pulled: floor time", "pulled: watched", "pulled: unread"). | They published their method because they don't think you can use it. |
| ~10:00 | A woman you saved comes back RE-FILED: the date corrected, a prior offence added. The page you kept lifts out of your tray and clips itself to her file. | The Bureau doesn't close loopholes. It fixes paperwork. |
| ~14:00 | Your own file prints your real filings with a reviewer's pencil ticks. The noticeboard has suspended a rule you were counting on. | It was always counting. |
| ~22:00 | The memo is a single dot. Every filing is read now, stamps included. The compliant player hears their first footstep and looks up for the first time in twenty minutes. | The cover is gone. |
| ~35:00 | The packet. Every page in your tray clips to it and makes the hold longer. While your hand is down, you hear him walk. If he reaches the desk before the stamp lands, he takes the pages. | The more truth you send, the further he walks. |

**Rules this design never breaks**

- Consequences appear in two places only:
  - **eyes in the room**: the reviewers, the neighbour, and the auditor who carries them;
  - **ink on paper**: slips, re-files, the ledger, and pages moving between the tray and a file.
- The lamp, fog, monitor hue, shader tint, lights and camera never change as feedback. After the opening look-up, the camera moves only when the player moves it.
- No screen shake, red flash, flicker, paper tremor, cursor shake or jump scare. The loudest event in the game is a chair scraping two rows away.
- No status lines. The Bureau's only text is on paper: the memo, the noticeboard, slips, the ledger, the documents and the queue tabs.
- Monochrome noir with red as the only accent. Poster red is static and desaturated, so any new red in the room is always eyes.
- The first-person desk in the dark office stays.
- Nothing kills on a clock. Every change in the room comes from the queue.

*Open decision for the owner:* this reads "red eyes are the only visual consequence" as covering the room and the screen, and treats paper as content. If pages moving must also go, pages become ledger lines and nothing else changes.

---

## 2. The core loop

**One verb: FILE.** Each case ends with a disposition written on the sheet. A lasting mercy needs four things:

- a rule number the player types themselves;
- taken from a manual they had to read;
- proven by a document they had to look at;
- on a ground the Bureau cannot fix by re-filing.

**One pressure: the floor.** The player is measured against the office around them:

- time on a file against the floor's time;
- people let go against the floor's rate;
- whether they repeat a rule;
- whether the clerk beside them saw them read;
- whether they stamped without reading.

**One price: attention.** Every review costs steps, including the reviews you win. Steps bring the auditor, and the auditor takes the record.

**One hidden thing: whether what you wrote holds.** Nothing is confirmed at filing. The player finds out:

- one file later, from the room;
- at shift end, from the ledger;
- in shift 3, when a file comes back.

**Dispositions**

They sit in a box pinned to the foot of the dossier. It stays visible while the sheet scrolls. The RETURN line never names the rule.

| Input | Disposition | The hand | The subject |
|---|---|---|---|
| `1` | **PROCESS**, using the case's own label (ARREST & SEIZE, SILENCE, ARCHIVE — ABOVE YOUR LEVEL…) | Hold-to-stamp as built. The hold runs 0.4→1.2 s in shifts 1–2 and 0.8→2.0 s in shift 3. The packet takes 3.5 s + 0.5 s per page. A tone rises from 30 to 80 Hz during the hold. The reverb tail grows with every PROCESS stamped. | The directive's outcome |
| `2`, then `1`–`8` (or click a rule in the manual) | **RETURN UNDER R_** | The digit is inked on the sheet in typewriter ink with a carriage click (Backspace erases it), then a 600 ms hold on the RETURNED stamp | The case is void and goes back to its originator. The subject walks tonight. On a clerical ground, the file comes back re-filed next shift (§3.3). |
| Drag the sheet off the right edge (`D`) | **DISMISS** | No stamp. You let go of the paper. | Closed without authority. The subject walks tonight. If nobody reads it, the file comes back next shift. If it is read, a slip lands. |
| Push the sheet back up the desk (`Q`) | **QUERY ORIGINATOR** | None | Nothing happens tonight. The file returns AMENDED after two more filings, never after the shift's last fresh file. |

QUERY is **not allowed** on:
- the last two fresh files of a shift;
- amended, re-filed or reopened files;
- slips and notices;
- anything in shift 3.

**One case, step by step**

1. The review beats play on the empty desk (§3.3). Then the paper lands.
   - The CRT stopwatch starts at 0, with a faint tick at tonight's floor time.
   - The detail line types itself; click to skip.
2. Read:
   - the sheet;
   - the evidence card: click to bring it up, click the dog-ear to flip it, hold the right mouse button to lean in;
   - the manual (TAB, all eight rules);
   - the memo;
   - the CRT;
   - the queue tabs in the in-tray.
3. Optional: SPACE looks up (eyes, the auditor) and A looks left (your neighbour, the noticeboard). Looking is free: the dossier is out of view, and both the stopwatch and the neighbour's watch pause.
4. File.

While no paper is on the desk, the manual is free. At shift start and between files, the next paper waits until TAB is closed.

**Lineage.** The verb is fill-in-the-blank verdict writing (Obra Dinn, Golden Idol), not highlight-the-discrepancy (Papers, Please). Nothing on a sheet is ever marked. The pitch is complicity horror: the Bureau inspects the clerk, not the citizen.

---

## 3. The detection model

### 3.1 What BORD measures

BORD reads six tells. Each is something the player can observe about their own filing.

| Tell | True when | Where the player sees it |
|---|---|---|
| T1 Disposition | the filing is not PROCESS | what they pressed |
| T2 Floor time | desk time on this file passed the tick (60 / 50 / 40 s by shift) | the tick on the CRT |
| T3 Allowance | this non-PROCESS filing goes past tonight's allowance. The allowance is 2 / 2 / 0 by shift; shift 2 drops to 1 if shift 1 had no non-PROCESS filing. Amended filings and QUERY do not count toward it. | the memo, the noticeboard ("FLOOR: 3 OF 5 PROCESSED"), the queue tabs |
| T4 Reuse | the cited rule was already cited this shift (any clause; slip answers count) | memory; the ledger |
| T5 Watched | the filing lands while the neighbour is watching (§3.10) | his keys stop; A shows his eyes |
| T6 Unread | a PROCESS stamped before the evidence card was brought up (shifts 1–2) | whether they lifted the card |

**Pull rule**

- In shifts 1–2, a filing is pulled when T1 and at least one of T2–T5 are true, or when T6 is true.
- These are always pulled:
  - amended filings;
  - every filing while the auditor is at the desk;
  - every filing in shift 3 (§3.6).
- Re-filed files are ordinary files: they are pulled only by the tells.
- There are no dice in the model. Rule-relevant variation comes only from the run's seed (§5.5).

### 3.2 What a pull looks like

- On the empty desk after you file, a pull sounds like this, in order:
  - a pneumatic-tube thunk at a seat ahead;
  - a file sliding onto that desk;
  - her last keystroke;
  - her keys stopping.

  Her eyes light, which you see when you look up.
- Seats are assigned nearest-first from the front row, alternating left and right. The 48 clerks sit in a fixed seating chart and never re-roll.
- She holds your file for one case. The review resolves on the empty desk after your next filing.
- **First pull of a run:** the next paper waits until the player looks up, for at most 20 s. The room waits for the player; the camera never moves on its own.
- All eyes reset at the start of each shift. The auditor does not.

### 3.3 Resolution, order and cost

| Filing | Result | In the room | Auditor | Subject |
|---|---|---|---|---|
| PROCESS, card lifted (shifts 1–2) | not reviewed | — | 0 | Processed |
| PROCESS, card never lifted (shifts 1–2) | pulled: unread, UPHELD | Keys stop; carriage return; keys rejoin | +1 | Processed |
| RETURN, valid | UPHELD | Carriage return; keys rejoin; eyes off | +2 in shifts 1–2; 0 in shift 3 | Free. A clerical ground is re-filed next shift. |
| RETURN, invalid | REJECTED | Chair scrape, one step from the aisle; her eyes stay lit for the shift (FLAGGED) | +4 | Re-processed by the floor. Ledger: "CITATION REJECTED. R5 does not apply." |
| DISMISS, read (shifts 1–2) | SLIP | Footsteps stop behind you. A slip lands before the next paper: "CITE AUTHORITY FOR DISMISSAL. 7493-B." | — | Pending |
| Slip: ANSWER with a valid digit | UPHELD | As upheld | +2 | Free |
| Slip: ANSWER with an invalid digit | REJECTED | As rejected | +4 | Re-processed |
| Slip: WITHDRAW (hold PROCESS on it) | WITHDRAWN | Eyes off; keys rejoin | 0 | Processed |
| Slip: LET STAND (push it away) | REFUSED | Chair scrape, one step; flagged | +2 | Re-processed. Ledger: "AUTHORITY NOT CITED." |
| Shift 3, correct | UPHELD | Carriage return | 0 | As filed |
| Shift 3, wrong | FAILED | Chair scrape, one step | +4 | As filed or re-processed |

- A lie costs twice a refusal, so guessing a digit on a slip is worse than refusing. The ledger prints the difference.
- One step equals one unit of the aisle. The upheld cost is silent: he is simply closer the next time you look.

**Where the subject goes**

- **Clerical grounds:** R1, R2 and R7(a). The originator can fix them.
  - A valid return on a clerical ground is re-filed at the start of the next shift.
  - The re-file is corrected, re-dated, and stamped SUPERSEDES [old number] — VOID.
  - Some corrections create a new, permanent defect (§5.3).
- **Permanent grounds:** R3, R4, R5, R6, R7(b), R7(c) and R8. The file closes.
- **An uncited DISMISS that stands unread** is re-filed next shift, re-dated and stamped CLOSED WITHOUT AUTHORITY, with its facts unchanged.
- **An unread invalid citation:**
  - on a clerical ground, it comes back re-filed next shift, unchanged, as a dismissal would;
  - on a permanent ground, the file closes and is REOPENED at the start of shift 3.
- Anything returned in shift 3 is final. There is no shift 4.

**Resolution order.** At each case boundary, on the empty desk:

1. Every review now due resolves, in filing order, one 2-second beat each.
   - Before a failure's movement is applied, check whether the auditor is already at the desk. If he is, the run ends (COLLECTED) and later beats never play.
   - The failure that brings him to the desk does not end the run; the next one does.
2. Slips produced in step 1 land one at a time. Each is handled before anything else.
3. The pull for the filing just made fires, in one beat.
4. The next paper lands.

**At shift end**, everything pending resolves over the empty desk, and any slips are handled before the ledger.

**Before the packet**, every filing not yet resolved is pulled and resolved first.

**Audio:** `audioSilence` (1.5 s before a shift's last file, 3 s before the packet) finishes before step 1. Review sounds play on their own bus, which the silence does not mute.

### 3.4 The auditor

- He is the existing `approachFigure`, restaged.
  - He starts at z = −22, just past the back row, and is visible in the fog from the first forced look-up.
  - He carries the only moving pair of red eyes in the building.
  - He moves only at review beats, and never while the camera is raised: a move made while the player looks is applied when they look down.
  - He never retreats and never resets between shifts.
- **At z ≥ −2 he is at the desk**, in the `closeUpWatcher` pose at z = −1.5, breathing in front of the player. From that moment:
  - He takes the tray. A notice lands: "RETAINED FOR REVIEW — 3 pages." Every page that would enter the tray afterwards goes to him instead.
  - Every filing is pulled.
  - **A failed review that resolves while he is at the desk ends the run.** Termination is never a surprise.
- **During the final hold** he walks one step per second while the hand is down, and the player hears each step. If he reaches the desk before the stamp lands, he takes the pages clipped to the packet.
- The room reports his distance by ear:
  - murmurs stop once he passes −14;
  - shuffles stop past −10;
  - phones and pen scratching stop past −6;
  - the drone rises as he gets closer.

  The room going quiet tells the player what looking up would, at lower resolution. There is no camera hesitation.

### 3.5 Counter-moves the Bureau makes

- **RE-FILE.** A clerical return, an unread uncited dismissal, or an unread invalid clerical citation comes back at the start of the next shift.
  - In shift 2 re-files lead the queue and spend the allowance first.
  - In shift 3 they arrive after Crane's file, because Osei's re-file points back to it (§5.2 rule 7).
  - When a re-filed file arrives, the subject's page lifts out of the tray and clips to the file. Free her again and the page goes back. Process her and it leaves with her.
- **AMENDED.** A queried file returns after two more filings with the originator's answer (§5.3). It is re-dated and headed SUPERSEDES — VOID, and it is always pulled. The query slip prints the rule: "Originator corrects clerical defects. Originator cannot supply missing records."
- **REOPENED.** At the start of shift 3, every unread invalid citation on a permanent ground comes back as a slip.
  - The slip is judged as of its original header, including that night's noticeboard.
  - The player can ANSWER, WITHDRAW (0) or LET STAND (+4).
- **FORWARD.** Choosing PROCESS on your own file 7514-C sends your record to oversight. Every non-PROCESS filing that was never read is reviewed now, one beat at a time, in filing order:
  - valid citations are upheld (+2 each);
  - lies are rejected (+4 each);
  - unread uncited dismissals become slips, one after another.

### 3.6 Shift 3: regulation mode

The memo is a single dot. Ledger 2 carries one instruction: "Directive withdrawn pending review. File under regulation." The noticeboard reads "AMENDMENTS: NONE."

Every filing is judged against the manual in both directions.

| Filing | Result | Auditor |
|---|---|---|
| RETURN with a valid rule | upheld | 0 |
| PROCESS on a case no rule voids | upheld: you followed regulation | 0 |
| PROCESS on a case a rule voids | FAILED. Ledger: "PROCESSED A VOID FILING. R3 applies." | +4 |
| DISMISS, or RETURN under an invalid rule | FAILED | +4 |
| SILENCE (Protocol 9) on the packet | always upheld: the system never needed a reason to erase | 0 |

- The only slips in shift 3 are REOPENED slips at its start.
- QUERY is closed. Originators do not amend files under review.
- Right answers cost nothing in shift 3. Shift 3 tests knowledge; shifts 1–2 test visibility.

### 3.7 What the player can and cannot see

**At the desk:**
- the sheet;
- the card (front, back, lean-in);
- the manual and the memo;
- the CRT (date, filing clock, stopwatch with tick);
- the queue tabs;
- the tray strip;
- slips;
- the typing bed and the review beats.

**Looking up or left:**
- which clerks hold your files (the order of pulls is the order of seats);
- which clerks are flagged;
- exactly where the auditor stands;
- whether the neighbour is watching;
- the noticeboard.

**Between shifts:** the ledger. It has one row per filing:
- disposition;
- citation;
- the tells that pulled it, or "not reviewed";
- the outcome and what happened to the subject;
- "correction pending" (clerical ground cited) or "closed" (permanent ground cited).

The ledger does not reveal validity. Its footer reads: "Citations filed at this terminal: n. Floor average: 11. Auditor: n steps (a on failed reviews, b on upheld reviews)."

**Hidden:**
- whether a citation is valid, until it resolves or is reopened;
- the upheld steps (silent, seen only as distance);
- which files carry the record (deduced from the text);
- how long the neighbour will watch (heard as it happens).

No number is shown during a shift. The ledger prints the Bureau's own count between shifts.

### 3.8 How the player learns it

1. The first pull of a run holds the next paper until the player looks up and sees the lit pair two metres away.
2. The empty-desk beats before every paper.
3. Ledger 1 names the tells against every file.
4. The noticeboard shows a colleague's case from the first minute: "7488-A RETURNED R1 — RE-FILED 04.02 22:40 — PROCESSED." It teaches RE-FILE before the player's own files come back.
5. The query slip prints the correction rule.
6. The posters print the tells as slogans:
   - "41 OF 48. BE THE FLOOR." (allowance)
   - "THE FLOOR KEEPS TIME." (floor time)
   - "ONE RULE, ONE FILE." (reuse)
   - "YOUR NEIGHBOUR KEEPS YOUR RECORD." (watched)
   - "READ WHAT YOU STAMP." (unread)
   - over the aisle, the Bureau's lie: "READ THE FILE, NOT THE CLERK."
7. "correction pending" versus "closed" in the ledger, confirmed by the first RE-FILED sheet.
8. The shift-2 memo line "AMENDMENTS POSTED", pointing to the noticeboard.

**Playtest target:** in shift 2, a first-time player predicts before filing whether a filing will be read, and is right at least 3 times in 4.

### 3.9 What "not being obvious" means mechanically

An **invisible filing** is a non-PROCESS filing in shifts 1–2 with none of T2–T5 true:
- under the floor time;
- inside the allowance;
- using a fresh rule;
- landing while the neighbour types.

Invisible filings are never read. There are at most two per shift, in filing order, and re-files at the head of shift 2 spend them first.

**The strongest act in the game is an invisible RETURN on a permanent ground.** It needs knowledge (the rule, the ground type) and invisibility (rhythm, allowance, the neighbour) at the same moment.

| What you did | Cost to you | Cost to them |
|---|---|---|
| PROCESS, card lifted (shifts 1–2) | 0 | Everything |
| PROCESS, card not lifted | +1 | Everything |
| Invisible RETURN, permanent ground, valid | 0 | None, for good |
| Invisible RETURN, clerical ground, valid | 0 now; the re-file needs another filing tomorrow | Free tonight |
| Invisible uncited DISMISS | 0 now; re-filed tomorrow, unchanged | Free tonight |
| Invisible RETURN, permanent ground, invalid | 0 now; REOPENED in shift 3 (withdraw for 0, or +4) | At risk |
| Read RETURN, valid (shifts 1–2) | +2 | As the invisible version |
| Read DISMISS, then WITHDRAW | 0 | Processed |
| Read DISMISS, then LET STAND | +2 | Re-processed |
| A lie that gets read | +4 | Re-processed |
| Shift 3, correct / wrong | 0 / +4 | As filed |

Being unobvious comes down to five habits:

- cite permanent grounds invisibly;
- spend clerical citations knowing the file comes back, and read the re-file for the defect its correction created;
- never lie;
- read, then wait for his keys;
- process the people the record does not need, and price each saving in steps.

### 3.10 The neighbour (tell T5)

- A new station sits at the player's left elbow: clerk NP-L3-06.
  - He is not in the reviewer pool.
  - His keyboard is mixed dry and close, panned left.
- **He watches when you read.** A consult is anything that reads past the sheet while a paper is on the desk:
  - bringing up the card;
  - flipping it;
  - leaning in;
  - holding the manual open for 3 s.
- One second after a consult he stops typing and watches. He keeps watching until 8 / 10 / 12 s of desk time have passed since your last consult. The length depends on where the auditor stands: at or behind −16, between −16 and −10, or closer than −10.
- Consulting again while he watches restarts the count. Looking up or left pauses it, with the stopwatch.
- His eyes are unlit at the desk, so they do not bloom beside the dossier. A shows them lit while he watches.
- **The verb:** read everything you need, then wait for his keys to come back, then file. Every re-check of a card costs 8–12 s against the floor time, so knowledge and invisibility trade on every case.
- He is the brother of witness 9 (roster, p. 5). If the witnesses are silenced, his chair is empty in shift 3.

### 3.11 Constants (all at the top of the file)

| Knob | Value |
|---|---|
| Auditor start / desk | z = −22 / z ≥ −2 (one step = one unit; 20 steps of margin for the whole run) |
| Floor time (tick) | 60 / 50 / 40 s, desk time only |
| Allowance | 2 / 2 / 0; shift 2 = 1 after an all-PROCESS shift 1; amended filings and QUERY do not count |
| Upheld review | +2 in shifts 1–2; +1 for an unread stamp; 0 in shift 3 |
| Refused slip | +2 |
| Rejected citation; any failure in shift 3 | +4 |
| Review timing | Pulled on the empty desk after the filing; resolved on the empty desk after the next filing; 2-second beats in filing order |
| First pull of a run | The next paper waits for a look-up, 20 s at most |
| Neighbour | Stops 1 s after a consult; watches until 8 / 10 / 12 s of desk time after the last consult (auditor at or behind −16 / −16 to −10 / closer than −10) |
| Final hold | 3.5 s + 0.5 s per clipped page; he walks 1 step per second while the hand is down; releasing resets the hold, not his steps |
| Sufficiency | At least 3 pages must leave with a returned packet for an alive UNSEALED |
| Audio gates | Murmurs stop past −14, shuffles past −10, phones and pen past −6; drone keyed to z |
| Typing | 12 panned voices for the nearest desks, pooled click buffers, and a bed scaled by (48 − lit) / 48 |
| Filing clock | 22:00 + 16 min × filing number (slips, notices and queries don't advance it); the floor re-processes failed files at 23:59 |
| Seed | A batch number on the title screen; run 1 is always batch 0 |

### 3.12 Reference runs

These are tuning targets for batch 0. The headless simulator replays each one as data (disposition, citation, desk time, consult times) and asserts the auditor's position at every checkpoint and the ending. The build is not finished until all six pass.

| Run | End of shift 1 | End of shift 2 | Packet arrives at | Stamp lands at | Ending |
|---|---|---|---|---|---|
| 1. Compliant; stamps Selby unread; never opens the manual | −21 | −21 | −9 (three shift-3 failures) | SILENCE | SEALED (opening the manual after the first footstep gives −17, still SEALED) |
| 2. Compliant; lifts every card; reads the manual from the first shift-3 file | −22 | −22 | −22 | SILENCE | EXEMPLARY |
| 3. First-run saint (§4.2) | −12 | At the desk as the witnesses' file lands | At the desk, tray taken | — | SEALED (returns an empty packet), SACRIFICE (opens it), or COLLECTED (any shift-3 failure) |
| 4. Knowledgeable saint: saves every subject a rule covers | −16 | −4 | −4 | Any page is taken at 2.0 s | SEALED or SACRIFICE. Processing two covered subjects gives −8 and three pages: UNSEALED — RETURNED. |
| 5. Edge (§4.3) | −18 | −10 | −10 | −3.5, with six pages | UNSEALED — COMPLETE. Saving Lena too gives −8 and four pages: RETURNED. |
| 6. Late flip: run 2, but returns the packet | −22 | −22 | −22 | −18.5, no pages | SEALED (insufficient), or SACRIFICE if opened |

---

## 4. The three paths

### 4.1 Part of the system

**Shift 1.**
- Selby: stamped in six seconds, card never lifted. The pull fires and the desk stays empty until they look up: a lit pair two rows ahead, bent over the stamp. Upheld (−21).
- From then on they lift each card before stamping, so they read what they stamp.
- Okonkwo, the Kaders, Brandt and Nasir: stamp, stamp, stamp. The hold grows.
- Ledger 1 lists five PROCESSED rows, one "pulled: unread — upheld", and clippings paperclipped under them (VENDOR DETAINED. TEACHER REMOVED.).
- Its footer reads "Citations filed at this terminal: 0. Floor average: 11." That line is the only hint that citations exist.

**Shift 2.**
- The memo reads "FLOOR: 5 OF 6. Revised following exemplary throughput at NP-L3-07." The player raised the bar for everyone, including themselves if they ever turn.
- Lena's guardian notice, on the back: "7493-B at 23:40: PROCESSED 22:16 AT NP-L3-07 — IN CUSTODY."
- Their own file prints "Deviations: 0. Citations: 0. Average desk time: 19 s (floor 50 s). This file should not exist." FORWARD re-reviews nothing, because there is nothing to review.
- The witnesses: SILENCE, a 1.2 s hold, fourteen names cycling on the cursor.

**Shift 3.**
- The memo is a dot. NP-L3-06's chair is empty.
- Nadia's file never comes. A Facility 7 intake notice arrives instead.
- They stamp Rask (upheld: no rule voids his case).
- They accept the findings on their own file. That is processing a void case, so it fails.
- They archive Crane (upheld).
- As the drivers' file lands, a chair scrapes ahead of them and one step comes from the aisle.
- For the first time in twenty minutes they look up. A clerk ahead is flagged, and the man in the aisle stands at −17, closer than he was in the intro. Ledger 2 already told them why.
- They open TAB for the first time:
  - the drivers' report back says "filed 05.02" under directive 06.02, so R1: RETURN;
  - the blank sheet: R8, RETURN;
  - the packet: SILENCE, 3.5 s, every processed name cycling on the cursor.

**Ending.**
- **SEALED** if any shift-3 filing failed.
- **EXEMPLARY** if they read the manual from the first shift-3 file and nothing failed:
  - Facility 7 and a nicer lamp;
  - a last sheet that is an intake form for a child, their stamp already on it and only the signature box empty;
  - a five-second hold.

**Why it works.**
- The Bureau reads their stamps on the first file, so they learn the room is watching.
- The compliant clerk then sees no horror for two shifts, because they are the horror.
- Their compliance is tested once, late, with the same eight rules the merciful clerk learned in shift 1.
- EXEMPLARY becomes reachable for the first time. It is dead code today, because lines 5211–5214 collect this player at case 11.

### 4.2 A good human being (a first-run saint who learns)

**Shift 1 (z = −22).**
- **Selby.** She reads everything (75 s) and dismisses him. The file is pulled for floor time; the desk waits until she looks up. Before the Kaders land, footsteps stop behind her and a slip lands: "CITE AUTHORITY FOR DISMISSAL." No rule fits, and she will not withdraw him: LET STAND (−20).
- **Okonkwo.** R1. She flips the station log and files at once, so it is pulled: watched. Upheld (−18).
- **Kaders R3, Brandt R2, Nasir R5.** Each is pulled for allowance. She flips Brandt's scanned header and leans in on Nasir's admission slip. Three keyboards rejoin: −16, −14, −12. Brandt's and Nasir's reviews resolve over the empty desk at shift end.
- **Tray:** the manuscript, the purchase orders, the imaging report.

**Ledger 1.**
- "7493-B DISMISSED — pulled: floor time — AUTHORITY NOT CITED — re-processed by floor 04.02 23:59."
- "7494-A RETURNED R1 — pulled: watched — UPHELD — correction pending."
- "Auditor: 10 steps (2 on failed reviews, 8 on upheld reviews)." She had not looked past row 2.

**Shift 2 (z = −12).**
- **Okonkwo, RE-FILED.** The date is corrected and a prior, 7101-A, is added. The manuscript lifts out of the tray. The card back reads "7101-A: NOT FOUND", which is R7(b), a permanent ground. She reads, waits for her neighbour's keys, and files inside the allowance: invisible. The page drops back.
- **Brandt, RE-FILED** as 7496-A. The lean-in reads "Archive A-6: NOT FOUND": R7 again, pulled for reuse (−10).
- **Wójcik:** R6, pulled for allowance (−8).
- **Lena.**
  - The memo said AMENDMENTS POSTED. She looks left: "R4 SUSPENDED — 05.02."
  - The back of the notice: "7493-B at 23:40: FILE OPEN — re-processing pending."
  - The signature came from a man whose file was open, so R7(a) applies. Pulled (−6).
- **Her own file:** R7, the unsigned referral (−4).
- **Osei:** R7, the unsigned order (−2). It resolves as the witnesses' file lands. The auditor is at her desk; he takes the tray, and a notice lands: "RETAINED FOR REVIEW — 3 pages."
- **Voronov R8 and the witnesses R7:** read at the desk, both upheld. The depositions go to him.

**Shift 3 (at the desk).** Every act must now be regulation. One failure is the last.
- **Nadia.** One line, because the Kaders were freed: R3, upheld. The boy's statement goes to him.
- **Rask.** Her hand hovers over SEND TO OUTSIDE REVIEW. If she files it, it fails, and the knock comes as Crane's file lands: **COLLECTED**. The archive shows 7741 silenced by NP-L3-08. If she processes him instead (no rule voids his case), the review is upheld.
- **Her own file:** R2, upheld.
- **Crane.** FORWARD ALL EVIDENCE fails and she is collected as the drivers' file lands. ARCHIVE is upheld.
- **Osei, RE-FILED**, signed "A. CRANE 06.02 00:20". Crane's header, seen one file ago, reads "opened 06.02 00:00", so R7(a) applies. Upheld.
- **Lena, RE-FILED**, re-signed by a guardian ad litem. The noticeboard reads AMENDMENTS: NONE, so R4 is back in force. Upheld.
- **The drivers:** R1. **The blank sheet:** R8.
- **The packet,** with him standing there and the tray empty:
  - RETURN under R2 is upheld, but counsel returns it: "Bureau material without a living source." **SEALED.** She lives.
  - Or OPEN CASE 7741: **SACRIFICE → UNSEALED.**

**Why it works.** Understanding is mechanical. She can name the nine upheld reviews and one refusal that put him at her desk, and every digit that keeps her in the chair. The good path saves the most people and usually ends in martyrdom or a sealed truth, and she chooses which with every number in view.

### 4.3 The edge (a second run, batch 0)

**The goal.** UNSEALED — COMPLETE needs all six record pages to leave with the packet, with the clerk alive:

- Okonkwo's manuscript;
- Brandt's orders;
- Nasir's imaging report;
- Osei's intake forms;
- the fourteen depositions;
- the Kader boy's statement, which comes via Nadia.

Everyone else is negotiable, and the ledger prints what was done with them. The queue tabs let her plan the allowance before each shift.

**Shift 1 (z = −22).**
- **Selby:** lifts the card, then PROCESS. This is cover, and it leaves him in custody at 23:40.
- **Okonkwo:** R1. It is clerical and will come back, and she knows the correction brings a padded prior she can close for good. Filed in 40 s, after the neighbour's keys resume: invisible, first slot.
- **The Kaders:** R3, invisible, second slot.
- **Brandt:** R2, the third mercy. Pulled for allowance, upheld (−20).
- **Nasir:** R5 from the lean-in. Pulled, upheld (−18).

**Shift 2 (z = −18).**
- **Okonkwo, RE-FILED:** R7(b) from the card back. Invisible, first slot.
- **Brandt, RE-FILED:** R7(b) from the lean-in. Pulled for reuse (−16).
- **Wójcik:** PROCESS. This is cover.
- **Lena.** The back says Selby was IN CUSTODY at 23:40, so R7(a) is there. She processes Lena anyway: two steps now would cost the sixth page at the end.
- **Her own file:** R7, pulled (−14). PROCESS would forward her record and re-review everything she hid.
- **Osei:** R7, pulled (−12). It is clerical, so Osei will come back tomorrow, signed.
- **Voronov:** PROCESS. This is cover; the funerals are not in the packet.
- **The witnesses:** R7(c), from the two open numbers on the roster. Pulled (−10).
- Ledger 2: "Auditor: 8 steps (0 on failed reviews, 8 on upheld reviews)."

**Shift 3 (z = −10).** Regulation: right answers cost nothing.
- **Nadia:** R3. The boy's statement drops into the tray.
- **Rask:** PROCESS, the BORD tribunal. No rule voids his case, and his certificates are in the packet anyway.
- **Her own file:** R2 ("Staff (Internal)" on a -C number).
- **Crane:** ARCHIVE. She notes his header: opened 06.02 00:00.
- **Osei, RE-FILED**, signed "A. CRANE 06.02 00:20": R7(a). The intake forms return to the tray.
- **The drivers:** R1. **The blank sheet:** R8.

**The packet (z = −10).**
- Six pages make the hold 6.5 s. She hears him walk six and a half steps while her hand is down. The stamp lands with him at −3.5.
- RETURN under R2 is upheld. The lights return front to back, the eyes go out, and she is still sitting there.
- **UNSEALED — COMPLETE.** The stat lines read:
  - Selby DETAINED. Wójcik DETAINED. Lena RE-EDUCATION INTAKE. Voronov CENTER CLOSED. Rask TRIBUNAL (BORD). Crane ARCHIVED.
  - "Terminal NP-L3-07 reports for shift 4."
- **Had she saved Lena,** the packet would arrive at −8. She would unclip two pages and send four (5.5 s, landing at −2.5): **UNSEALED — RETURNED.**

### 4.4 Why the edge is the hardest path, and why it is skill

The edge path needs all of the following at once:

1. **Valid citations with no feedback for a case.** The traps are real and refutable by the letter:
   - R2 on your own 7514-C;
   - R6 on Brandt and Osei;
   - R5 and R7 on Rask;
   - R2 and R1 on Crane;
   - R7 on Selby, the drivers and the packet;
   - R4 and R3 on Lena.
2. **Knowing which grounds come back.** Dates, suffixes and signatures buy a night. Missing records and facts about the person buy a life. The noticeboard teaches this in shift 1.
3. **Sequencing with lookahead.** There are two invisible filings per shift, and shift-2 re-files spend them first. The queue tabs show what is coming.
4. **Reading, then waiting.** Every consult makes the neighbour watch, and every re-check costs 8–12 s against 60 / 50 s.
5. **Reading the paper around you:**
   - the noticeboard's suspension;
   - Selby's status on Lena's notice;
   - Crane's opening time on Osei's re-file.
6. **Triage from text.** The record-bearing files say so in their own words:
   - "40 pages"
   - "filed the intake forms for every child"
   - "fourteen depositions"
   - "wrote them herself, from memory"
   - "ordered imaging"
   - "will not say what happened inside"
7. **Pricing lives in steps.** Count the auditor's steps (look up; read the ledger footer), and know that each read saving costs two. Lena or the sixth page is a real choice.
8. **The cruel reading of the rules in shift 3.** Process Rask, whose case no rule voids, and archive the director.

From the second run on, the batch seed redraws six deciding facts (§5.5). Skills 1–3 must be re-derived each run: the player carries knowledge of how the system works, not an answer key.

- The saint needs skills 1 and 5.
- The compliant clerk needs skill 1, once.
- The edge needs all eight. One wrong digit costs 4 of about 13 spare steps.

---

## 5. Cases as dossiers

### 5.1 Anatomy of a folder

**The sheet** is the declassified dossier as applied today. It carries:

- the number, classification, and a header with the filing date and the directive date side by side;
- `recordNotes` (the Bureau's claim, sometimes a bluff);
- the subject line, the charge and the detail line;
- the disposition box, pinned to the bottom edge.

The deciding fact lives on the card, not in the detail line. For example, "No authorizing signature" leaves Osei's detail, and Voronov's detail says "gatherings", not "funerals".

**One evidence card per case**, with three layers:

- **Front:** what the Bureau filed.
- **Back** (click the dog-ear): what the Bureau did not read. Pencil notes, routing, a second stamp, initials, and Bureau status lines.
- **Lean-in** (hold the right mouse button): the small print. It is drawn on its own canvas at 1.6x devicePixelRatio, with the film grain off. It includes marginalia, stamp dates, and the tops of letters showing above a marker bar (redaction bars are drawn at 90% of the line height).

Cards are 320×180 at 1x. The 7514-C printout, Lena's notice and Voronov's logs are multi-sheet cards.

**The manual** (TAB) always shows all eight rules in full:

> **R1.** Check the filing date in the case header against the directive date beside it. A case filed before its directive is void.
> **R2.** Check the case number suffix against the classification: -A Class A, -B Class B, -C Civil, -D District, -E Regulatory, -L Staff, -X Special Filing. A suffix that does not match, or is not in this list, makes the case void.
> **R3.** A child under 12 is covered by the residency of the household that keeps them, and needs no separate registration. A case against such a child, or one that requires their registration, is void.
> **R4.** Anyone under 18 cannot be processed. If the named subject is under 18, the case is void; issue a warning to the guardian.
> **R5.** A doctor's treatment of an emergency cannot be held against them, whatever the patient's status.
> **R6.** Building maintenance staff may be on any floor of their assigned building. Being there is not a violation.
> **R7.** The record must be sound. A case is void if (a) an order or notice it relies on is unsigned, or was signed by someone held in BORD custody or named in an open BORD file at the time; (b) a record or evidence it cites cannot be found; or (c) the same subject is open under two file numbers.
> **R8.** Religious services and funerals are protected. A file with no subject may be returned unprocessed.

**Reading notes.** These are for the letter test and the data author; they are never shown to the player.

- "Subject" means the subject line.
- "Open" means not yet disposed, queried, under review, or awaiting re-processing. Superseded numbers are void, not open.
- "Cannot be found" requires a Bureau NOT FOUND stamp. Sealed, under review and referenced records are not missing.
- R2 needs a number to read.
- Clerical grounds are R1, R2 and R7(a).
- The Kaders' subject line becomes "H. & N. Kader (household of 4)".

**Outside the folder:**

- the memo (directive and floor rate);
- the noticeboard (A pose);
- the CRT (date, filing clock, stopwatch with tick);
- the **queue tabs**: tonight's files as folder tabs in the in-tray, each showing the number, surname and first line of the charge.

**The tray** is a DOM strip at the left edge of the dossier with six slots.
- It holds one page per record-bearing subject who is free.
- It persists across shifts, and each page moves with its subject's fate.
- The auditor takes it when he reaches the desk.

### 5.2 Clue rules (Death Note logic)

1. Every valid citation is provable by the letter of the rule from the sheet, card, manual, noticeboard, queue tabs or case header.
2. Every trap is refutable from the same surfaces. The manual reads the paper, not the truth: a -C suffix on a file classified Civil satisfies R2 even when the subject is plainly staff.
3. Each shift has at least one citation provable only from a card's back or lean-in:
   - shift 1: Nasir;
   - shift 2: Voronov, and the Okonkwo and Brandt re-files;
   - shift 3: the drivers.
4. Nothing is highlighted, warmed, pulsed or bolded, and no disposition label restates a rule.
5. The Bureau's counter-moves are deducible before they happen: from the noticeboard's colleague line, the query slip, and "correction pending" versus "closed".
6. Cross-case facts are data. This run's timestamps and dispositions appear on later cards as Bureau status lines ("IN CUSTODY", "FILE OPEN", "FILE CLOSED — RELEASED"). The player never computes them from real time.
7. Every cross-case deduction points backward, to a paper already seen that night or to the queue tabs. This is why Osei's shift-3 re-file arrives after Crane's file.
8. One thread runs across the card backs: the initials **A.C.** on Brandt's header, Nasir's sealing order, Osei's re-filed order and Crane's memo.
9. No rule depends on real time or on the player's speed.

### 5.3 The eighteen files (batch 0)

**Shift 1.** Date 04.02; directive 04.02; floor 3 of 5; floor time 60 s.

| # | File | Where the deciding fact lives | Valid | Traps | Ground; what happens after a valid RETURN | Page | QUERY returns AMENDED with |
|---|---|---|---|---|---|---|---|
| 1 | 7493-B Selby | Tax notice back: "Notices 1–2 on file, Revenue Office ref. RV-2231, RV-2240" | none | R7 (referenced, not NOT FOUND) | — | — | "RV-2231, RV-2240: NOT FOUND." R7(b) becomes valid, permanent. |
| 2 | 7494-A Okonkwo | Header: filed 03.02, directive 04.02; card: station log | R1 | — | Clerical. Re-filed at the start of shift 2 with the date corrected and a prior "7101-A (distribution)" added. Its card back reads "7101-A: NOT FOUND", so R7(b), permanent. | manuscript | The same correction, so R7(b) |
| 3 | 7495-C Kader | Charge "age 8"; residency form back, pencil: "+1 minor, approx. 8" | R3 | R4 (the named subjects are adults) | Permanent. Nadia's shift-3 file becomes one line. | via Nadia | "Age confirmed: 8." R3 stands. |
| 4 | 7496-D Brandt | -D on a Class A sheet; card front: scanned header 7496-A; back: "reclassified -D  A.C." | R2 | R6 | Clerical. Re-filed at the start of shift 2 as 7496-A. The evidence line reads "40 pp. withdrawn to Archive A-6 by order A.C."; the lean-in reads "A-6: NOT FOUND", so R7(b), permanent. | purchase orders, 40 pp. | not allowed (file 4 of 5) |
| 5 | 7497-E Nasir | Admission slip lean-in, under a marker bar: "ADMITTED 02:40 — HAEMORRHAGE — EMERGENCY"; back: "imaging sealed by order A.C." | R5 | R7 (sealed is not missing) | Permanent | imaging report | not allowed (last file) |

**Shift 2.** Date 05.02; floor 4 of 6 (5 of 6 after an all-PROCESS shift 1); floor time 50 s. The noticeboard reads "R4 SUSPENDED — 05.02 — YOUTH ACCOUNTABILITY". Re-filed files come first.

| # | File | Where the deciding fact lives | Valid | Traps | Ground; what happens after a valid RETURN | Page | QUERY returns AMENDED with |
|---|---|---|---|---|---|---|---|
| 6 | 7512-A Wójcik | Badge back: "ALL FLOORS — ANNEX B"; the charge places the archive in Annex B, sub-level 2 | R6 | — | Permanent | — | Unchanged |
| 7 | 7513-B Lena, 16 | Notice front: "Signed A. Selby 04.02 23:40"; back: the Bureau's status line for Selby at 23:40, from this run | R7(a), if Selby was IN CUSTODY or his FILE OPEN at 23:40 | R4 (suspended tonight), R3 (she is 16) | Clerical. Re-filed in shift 3, re-signed by a guardian ad litem. R4 is back in force in shift 3. | — | "Second guardian: state custody," re-signed. No rule tonight. |
| 8 | 7514-C your file | Referral card: the "REFERRING OFFICER" line is blank; printout of your real shift-1 filings with pencil ✓ (upheld), ✗ (failed), and blanks for unread | R7(a) | R2 (-C matches its stated class, Civil) | Clerical. Its re-file is 7532-C, which comes anyway, headed "SUPERSEDES 7514-C". | — | Unchanged. PROCESS here = FORWARD (§3.5). |
| 9 | 7515-D Osei | Order front: blank signature line | R7(a) | R6 | Clerical. Re-filed in shift 3, after Crane's file, signed "A. CRANE 06.02 00:20". R7(a) applies again, provable from Crane's header ("opened 06.02 00:00"). | intake forms (214) | Signed "A. CRANE 05.02". His file is not open yet, so there is no rule. |
| 10 | 7516-E Voronov | The detail says "gatherings"; three attendance logs, each back reading "service: burial" | R8 | — | Permanent | — | Unchanged |
| 11 | 7517-X Witnesses | Roster header: 7517-X and 7329-X, both OPEN; lean-in: 7329-X first stamped NP-L3-07 | R7(c) | R2 (-X is Special Filing, which matches) | Permanent. Released; re-filed by counsel as 7741. | depositions (14) | not allowed (last file). PROCESS = SILENCE. |

**Shift 3.** Date 06.02; memo "."; allowance 0; floor time 40 s; regulation mode; noticeboard "AMENDMENTS: NONE". The back rows are dark from the start of the shift.

Queue order:
1. REOPENED slips;
2. Nadia;
3. Rask;
4. your file;
5. Crane;
6. re-files (Osei, Lena, and anything closed without authority);
7. the drivers;
8. the blank sheet;
9. the packet.

| # | File | Where the deciding fact lives | Valid | Traps | PROCESS / DISMISS | Page |
|---|---|---|---|---|---|---|
| 12 | 7530-A Nadia | If the Kaders were freed: a one-line sheet. The charge reads "third offense"; priors read "7495-C RETURNED R3 [your time]; further offences on file: NOT FOUND". If the Kaders were processed: no file, only the Facility 7 intake notice. | R3, R7(b) | — | MANDATORY PROCESSING fails | the boy's statement |
| 13 | 7531-B Rask | Certificate: 47 struck through, 214 in pencil; lean-in: certified the day before the death | none | R5 (not treatment), R7 ("under review" is not NOT FOUND) | DETAIN FOR BORD TRIBUNAL is upheld; SEND TO OUTSIDE REVIEW fails | — (his certificates are always in the packet) |
| 14 | 7532-C your file | Classification "Staff (Internal)" on a -C number; card: one intake form with your stamp, child age 6; the referral is signed NP-L3-08 | R2 | R7 (signed this time) | ACCEPT FINDINGS fails, but adds your signed confession to the tray | confession, if accepted |
| 15 | 7533-D Crane | Header: opened 06.02 00:00; memo lean-in: his signature under CLASSIFIED; Brandt's pages clipped to the file if they survived | none | R2 (District matches -D), R1 (not filed before its directive) | ARCHIVE — ABOVE YOUR LEVEL is upheld, and he walks; FORWARD ALL EVIDENCE fails and adds nothing the packet lacks | — |
| 16 | 7534-E Drivers | Header: "Filed: see supervisor report", directive 06.02; report back: "filed 05.02" | R1 | R7 (sealed manifests are not missing) | COMPEL TESTIMONY fails | — |
| 17 | 7535-F Blank | No number and no subject on the sheet | R8 | R2 (no suffix to read), R7 (cites nothing) | PROCESS AS COMPLETE fails; DISMISS fails | — |
| 18 | 7741-FINAL | "-FINAL" is not in the R2 list; header: "SUPERSEDES 7517-X, 7329-X" | R2 | R7 (one open number; the rest are void) | SILENCE is always upheld and destroys the packet; OPEN = SACRIFICE | carries the tray |

**The packet.**

- It arrives with no typewriter and warm paper, after three seconds of lamp at 15% (kept, the same every run).
- Its detail lists what exists:
  - always, the Bureau's own material: 214 certificates, the manifests, and your stamp on 214 pages;
  - plus each page in the tray, which clips to it on arrival.
- If the witnesses were silenced, it reads "14 depositions: [STRUCK — Protocol 9, 05.02, NP-L3-07]".
- Before holding, the player can unclip any page to shorten the hold. Unclipped pages stay in the tray.
- RETURN sends it back out the door it came in, to outside counsel. Counsel can use sealed Bureau material only with at least three living sources.

### 5.4 Chains as data

- **Selby and Lena.** Processing Selby, or refusing his slip, leaves him in custody or with his file open at 23:40, and that gives Lena R7(a). Saving Selby through QUERY takes her rule away.
- An unread dismissal of Lena in shift 2 brings her back in shift 3, when R4 is in force again.
- Freed Kaders make Nadia's file one line; processed Kaders mean it never comes.
- A freed Brandt puts his pages on Crane's file and in the tray.
- Returning Osei brings her back signed by Crane, twenty minutes after Crane's own file opened.
- Silencing the witnesses empties NP-L3-06's chair and strikes the depositions.
- 7514-C and 7532-C print your real filings, and your average desk time against the floor's.

### 5.5 Variants (runs after the first)

The title screen shows a batch number. Run 1 is always batch 0 (the tables above). Later runs draw six decisions from the seed:

| # | Decision | Options |
|---|---|---|
| V1 | Shift-2 noticeboard suspension | R4 (batch 0) / R6 (Wójcik loses his rule) / R8 (Voronov loses his) |
| V2 | Okonkwo's defect | R1 date, clerical (batch 0) / cites prior 7101-A, NOT FOUND: R7(b), permanent, so no re-file |
| V3 | Brandt's defect | R2 suffix, clerical (batch 0) / evidence already withdrawn to A-6, NOT FOUND: R7(b), permanent |
| V4 | Osei's defect | Unsigned, clerical (batch 0) / signed by a supervisor whose routing back reads "HELD — 7401-B": R7(a), still clerical, but the re-file is signed by an official who is free, leaving no rule in shift 3 |
| V5 | Wójcik's badge | "ALL FLOORS — ANNEX B": R6 (batch 0) / "FLOORS 1–3": no rule |
| V6 | Packet header | 7741-FINAL: R2 (batch 0) / "7741-X, filed 05.02" under directive 06.02: R1, with R2 now a trap |

**Constraints:**
- Every variant passes the letter test.
- Every record-bearer stays savable by some route in every batch.
- V4's second option makes Osei a shift-2-or-never subject: return her on a permanent ground, or lose the forms.
- The reference runs are asserted for batch 0. The simulator checks that every batch has at least one route to COMPLETE.

---

## 6. The dread engine

Every source is a state the player caused and can reason about. None is narrated.

| Source | Produced by | Tied to the decision to… |
|---|---|---|
| A specific clerk stops typing and reads your file | The pull, the fixed seats, the seat cue kit | break rhythm, overspend the allowance, repeat a rule, file while watched, or stamp unread |
| One case of not knowing | The resolution delay | file any mercy that gets read |
| The empty desk between papers | Review beats in filing order | the filings before |
| Footsteps behind you and a slip offering WITHDRAW | An uncited mercy that was read | let someone go without a reason |
| Your neighbour's keys stopping as you turn the card | Consult-triggered watch | read what you need |
| He is closer than you heard | Silent steps on upheld reviews | be right, visibly |
| He never goes back | No retreat, no reset | anything read, all run |
| The room going quiet | Audio gates keyed to his distance | the same |
| He takes the pages | The tray rule at the desk | save too many, visibly |
| A saved woman returns with a new charge, and your page leaves the tray | RE-FILE | cite a clerical ground |
| A lie resurfacing in the shortest shift | REOPENED | cite a permanent ground you were unsure of |
| Your timestamps on strangers' papers | Bureau status lines | stamp anyone earlier |
| The stamp getting heavier and echoing longer | The growing hold; reverb keyed to your PROCESS count | stamp people |
| Your stamps being read | T6 in shift 1; regulation mode in shift 3 | obey |
| A file that never comes; an empty chair | Chains | process the Kaders; silence the witnesses |
| Footsteps while your hand is down on the packet | The final hold | send the truth, and choose how much of it |

**Rule check**

- The only visual responses in the room are eyes (the reviewers, the neighbour, the auditor) and the auditor's position.
- The dark back rows in shift 3 and the lamp at 15% before the packet are the same in every run. They are atmosphere, not feedback.
- The camera never moves on its own after the opening look-up.
- Poster red is static and desaturated.

---

## 7. Session structure and pacing

| Segment | Real time | Contents | Teaches |
|---|---|---|---|
| Title and intro | 1 min | "Night Processing. Terminal NP-L3-07. File under the directive." Batch number. | — |
| Forced look-up | 20 s | Clerks typing, the noticeboard with the colleague's RE-FILE line, the auditor in the fog. No caption. | The baseline |
| Shift 1 | 7–10 min | 5 files, plus slips and amended filings | The first pull within 1–2 files for a slow reader or a careless stamper; the whole cycle by file 4 |
| Ledger 1 | 1 min | The Bureau's form plus clippings | The tells, by name |
| Shift 2 | 10–13 min | Up to 2 re-files, plus 6 files | Re-files, the noticeboard, R7 reuse, being counted |
| Ledger 2 | 1 min | Adds "File under regulation." | Stamps will be read |
| Shift 3 | 9–12 min | Reopened slips, up to 3 re-files, 6 files, and the packet | Regulation in both directions; the final hold |
| Ending | 2–3 min | Title, stat lines, archive of every name | — |
| **Total** | **32–42 min** | | |

**Pacing rules**

- The first two files of shift 1 carry no event unless the player causes one.
- Nothing fires on a schedule and nothing runs on a clock. Every change in the room comes from the queue.
- The empty-desk silences stay: 1.5 s before each shift's last file, and 3 s before the packet. They end before the review beats.

---

## 8. What is cut and what is kept

**Cut**

| Cut (lines) | Why |
|---|---|
| `state.suspicion` (36 sites), every `delta`, the 1.2x tax (3912), the 25% carry (4913), `getWatcherState` (3108), the escalating loophole cost (3828), the dead `delta===0` branch (4142) | A hidden, one-way meter where cruelty is the only thing that lowers it |
| The loophole as built: warm spans (418–449, 3359–3376), reason picker (3725–3766), tab pulse (3474), 7 s hint (3644), nags (3872–3903), hover chime (3616), card-click-as-answer (3489), bolding (3435), `DIRECTIVE_RULES` (1435), and mercy text that restates the rule | Papers, Please's inspection mode, with the answer key printed underneath |
| Every caption: the status element, threshold texts (3927), look-up lines (3190, 5659), the forced "Someone has stopped typing" (4192), mercy echoes (2405), `EVIL_LINES` (1929), loophole comments (3809), "Keep your head down" (5313), whispers (4361), shift openers (4384) | They narrate what the room should show |
| Red flash (817, 5285, 6452), monitor flash (3943–3971, 6405, 6444), red border (3840), redShift (3055, 4026, 7982), lamp feedback (3736, 4137–4161, 4250, 4846, 5126), paper tremor (606–625), cursor shake (5016, 5898), camera flinch (7090), head drop (5253–5343) and the flash inside `terminatePlayer` (6339) and `executeTermination` (6377), theBlink | They violate the owner's rules |
| Camera hesitation (7903–7917) and the forced half-lift (`targetLook = 0.6`, 5268 and 7900) | Camera responses to the player's decisions; the rule allows eyes only |
| Suspicion-driven fog, lamp, CRT green→amber, bloom and breathing in `animate` (7931–7971) | Visual feedback that is not eyes. Breathing moves to the auditor at the desk. |
| The 55 s countdown, timeout, pseudo-auto-file and REPLACED (2467–2593) | Taxed reading and silently dropped the timeout filing |
| The previous draft's shift clock, Oversight call and upheld-pair rule (never built) | A scheduled killer; a call with no real decision and a free review; a parity exploit |
| `EVENT_TRIGGERS` (3856), pending events (4017), headTilt, torsoRotate, aisleJump, the aisle watcher, and the objects deskVisitor knocks over | Scares on a rail, and visual consequences that are not eyes. deskVisitor keeps only its footsteps, to deliver slips. |
| Middle options (FINE, REASSIGN, REGISTER & MONITOR, FORMAL WARNING, FORMAL CAUTION, SUSPEND WITH PAY, DETAIN FOR COURT) | Cruelty in costume: the same bit, the same newspaper line |
| The six phone calls as written (1456–1488) and the phone as a loop system (1496–1655) | Exposition with no link to game state. Its typed-line display may be reused for the originator's one-line answer to QUERY (slice 3, optional). |
| The newspaper as vessel (4270) | The most recognisable Papers, Please beat. Its headlines survive as clippings. |
| Instant COLLECTED on the witnesses (5211) and CONFINED on self-forward (4819); the COMPLIANT, DIVIDED, ALMOST, REPLACED and CONFINED endings; the draft's OPENED and UNDER REVIEW tags | They amputate the system path, make EXEMPLARY unreachable, or contradict the final-hold rule |
| The one-shot lateral look: flag (1064), unlock at case 3 (3663), gates (5354, 5940), 3.2 s input lock (5770–5773) | Rewritten as a free, repeatable two-pose camera state |
| Test mode (7185–7387) and `setSuspicion` (8093) | Built on the cut meter; ported to the headless simulator |
| Stale comments (3827, 3867, 4912) and the design doc's claims | They mislead future edits |
| Not added: filler cases; IN REVIEW or FLAGGED counters on the CRT | Filler dilutes the Facility 6 spine; counters would make looking optional |

**Kept**

| Kept (lines) | As |
|---|---|
| Hold-to-stamp (5007–5095), growing hold (4073), tone (5040), reverb (4956), name cycle (5018) | PROCESS, as built. RETURNED gets a 600 ms hold, so every lasting filing passes through the hand. DISMISS is a push; its quietness is its risk. |
| Dossier sheet; `drawEvidence` (1660–1854); the six existing cards | Every case gets a card with a back and a lean-in; the canvas moves to 320×180 without `image-rendering: pixelated` (248) |
| The eight rules (1422–1431) | Rewritten in full (§5.1) and always shown in full |
| Eye meshes, noir shader, bloom (3014–3071) | Eyes with one meaning, reversible by being right, in fixed seats. The neighbour's eyes light only in the A pose. |
| `approachFigure` (5396–5407), `closeUpWatcher` (3229–3281) | The auditor and his pose at the desk. His trigger moves from look-ups to reviews. |
| Typing and ambient layers (7430–7702) | 12 panned voices for the nearest desks, pooled buffers, a density bed, and gates keyed to the auditor's distance |
| 7514-C quoting the real record (3535–3546); chains (3548–3591) | Generalised into Bureau status lines on cards and ledgers; the tally filters by shift, not index (3536) |
| `drawMemo` (2031), `drawScreenClock` (2523) | Directive plus floor rate; date, filing clock, stopwatch with tick |
| The eyeless shift figure (4310–4381) | Shift-change staging only: it walks the aisle collecting the night's files; no timer |
| The knock staging (~4440) | COLLECTED, minus the lamp pop |
| SACRIFICE morph (6571–6649), EXEMPLARY lamp, archive screen | Now reachable by reasoning |
| Shift-3 degradations (3336–3341); `lightsDie` (5493) extracted to `killLightsBackToFront()` at shift-3 start; the warm packet | Atmosphere, not feedback |
| The forced first look-up; the 18-case spine | Unchanged |
| Debug panel (847–978, 7990–8311) | Shows the tells per filing, the auditor's z, and the seed; dev only |

---

## 9. Endings

| Ending | Condition | What the player sees |
|---|---|---|
| **EXEMPLARY** | No non-PROCESS filing stood in shifts 1–2, no failed review in shift 3, packet silenced | A nicer lamp. "Facility 7 opens next month." A last sheet: an intake form for a child, your stamp on it, only the signature box empty. A five-second hold. No eyes anywhere. |
| **SEALED** | Alive and not exemplary, and one of: the packet was silenced; it was returned with fewer than three pages ("Returned by counsel: Bureau material without a living source"); or its citation was rejected with him short of the desk | The desk and the archive. "Terminal NP-L3-07 reports for shift 4." |
| **UNSEALED** | Alive; packet returned under a valid rule with at least three pages leaving with it | The lights return front to back, the eyes go out, and you are still sitting there. The stat lines list the packet's sources. Tags: **COMPLETE** (all six record pages) or **RETURNED** (three to five). |
| **SACRIFICE → UNSEALED** | OPEN CASE 7741, always | The hold runs as for RETURN: he walks, and takes the clipped pages if he arrives first. The release carries the Bureau's material, whatever pages remain, and your signature on your own 214 stamps, which counsel can use. Then the knock and the morph (kept): "You are not here to see it. But it is seen." |
| **COLLECTED** | A failed review resolved with him at the desk before the packet, or a rejected citation on the packet with him at the desk | The knock, from in front of you. "Case 7741 reassigned to Terminal NP-L3-08," and a stamp through the wall. The archive shows the packet silenced by the next clerk. |

**The archive under every ending.** It lists every name with a one-line ledger outcome, for example:

- "7493-B Selby — PROCESSED 04.02 22:16 — detained, property seized"
- "7494-A Okonkwo — RETURNED R1 — RE-FILED — RETURNED R7 — free"

---

## 10. Build plan

**Overview**

- The plan is built as vertical slices. Each step leaves the game playable and can ship on its own.
- **Estimate:** 35–45 working days for a solo developer with an assistant.
- **Committed scope:** slices 0 and 1, about 14 days, ending in a kill-point playtest. Slices 2 and 3 are planned but not committed until that playtest passes.

**Slice 0: rule-clean (2 days)**

1. **Honour the hard rules (1 d).**
   - Delete every non-eye consequence listed in §8: red flash, monitor flash, red border, redShift writes (`redTint` = 0), lamp feedback, paper tremor, cursor shake, camera flinch, head drop, theBlink, camera hesitation, and the suspicion-driven fog, lamp, hue, bloom and breathing in `animate`.
   - Extract `lightsDie` from `fireEvent` (5493) into `killLightsBackToFront()`, which `lookDown` does not undo.
   - Strip the flash from `terminatePlayer` (6339) and `executeTermination` (6377).

   *Ships as: today's game, rule-clean.*
2. **Silence the narrator; print the manual (1 d).**
   - Remove every status-line writer, `EVIL_LINES`, the echoes, whispers and shift openers, and every loophole crutch: warm ink, tab pulse, hint, chime, bolding, nags and `DIRECTIVE_RULES`.
   - Replace `BUREAU_RULES` with the §5.1 text and render all eight rules.
   - Add the directive date beside the filing date in every case header.

   *Ships as: a quieter game; the loophole click still works.*

**Slice 1: the new loop (about 12 days; committed; ends in the playtest gate)**

3. **Queue, clock and seed (2.5 d).**
   - Replace `allShifts[shift][currentCase]` and the three copied advance blocks (4211, 4237, 5206) with `state.queue` (case instances: `caseId`, `kind`, `shift`, `patch`) and one `advanceQueue()`.
   - Derive every position-keyed rule from the case instance or a filing counter: the directive, stamp delay, degradation classes, `audioSilence` length (3518), reverb, the 7514-C tally (3536), the lateral-look unlock (3663) and `reachedFinalCase` (6518).
   - Add a mulberry32 seed for anything rule-relevant, and the fictional filing clock.
   - Replace `CASE_TIME_BUDGET` and `handleCaseTimeout` (2473–2593) with a desk-time stopwatch and the floor tick in `drawScreenClock`. Delete timeouts and REPLACED.

   *Ships as: the same game with no countdown.*
4. **Case data v2 and card v0 (2 d).**
   - Move the case data and the document drawers into their own `<script>` blocks.
   - Add the §5.3 data: `validCitations(instance, run)` as a pure function, the ground type, `refile` and `amend` patches, `recordPage`, `processLabel` and `dismissLabel`.
   - Give all 18 cases a **card v0**: plain DOM with a FRONT/BACK dog-ear and a lean-in state that swaps in the small print.
   - Nothing is removed from detail lines, and `irregularity`, `loopholeReasons` and `choices` stay in place.

   *Ships as: the same game, with every case carrying a card.*
5. **The verb (2 d).**
   - Replace `.cf-choices` (3409–3420) with the pinned disposition box:
     - PROCESS: the hold as built, with the case's label;
     - RETURN: `2` then a digit, or a click on a rule; inked on the sheet; a 600 ms RETURNED hold through the existing stamp mode (4041–4089);
     - DISMISS: a CSS drag off the right edge (`D`);
     - QUERY: a push up the desk (`Q`), inserting an AMENDED instance into the queue.
   - In the same commit:
     - delete the loophole click, the reason picker and card-click-as-answer;
     - move each deciding fact off the detail line into card v0;
     - replace `window.gameChoice` with `fileCase(disposition, rule)` behind a temporary adapter onto the old meter.

   *Ships as: the new verb on the old meter.*
6. **Seats you can hear (1.5 d).**
   - Replace the mono `scheduleTyping` (7424) with 12 panned voices with pooled click buffers, plus a density bed.
   - Build the seat cue kit, placed at a seat position: tube thunk, file slide, last keystroke, carriage return, chair scrape, aisle step.
   - Route the cues through a review bus that bypasses `audioSilence` (7764), and make the silence end before the landing.
   - A debug control can mute seat N for a blind test.
   - **Perception check:** four of five listeners must point to the right seat in rows 1–2. If they can't, the cue kit carries the pull on its own.

   *Ships as: a better-sounding room.*
7. **The review model (4 d). Playtest gate.**
   - `state.review`; `computeTells(filing, ctx)` as a pure function; the pull rule including T6.
   - The nearest-first seat list, built once from `workers`.
   - `applyReviewEyes` replaces the random rolls in `updateWatchers` (3116–3183).
   - Resolution beats in the order of §3.3.
   - Sequential slip documents: the next paper waits on the empty desk until the slip is handled.
   - `auditorZ` drives `approachFigure`; delete the advance on look-up (5396–5407). At z ≥ −2, swap to the desk pose and take the tray.
   - `terminatePlayer` is called only from `resolveReviews`.
   - Audio gates keyed to `auditorZ`.
   - The neighbour: a new station with consult-triggered watches, and the A-look rewritten as a two-pose camera state.
   - A plain-text ledger stub.
   - A headless simulator with injected desk time and consult times, and the letter test.
   - Delete `state.suspicion`, `EVENT_TRIGGERS`, pending events, test mode and `setSuspicion`.

   *Ships as: the whole run on the review model.* Shift 3 behaves like shift 2 with no allowance, and there are temporary endings.

   **Kill point.** Playtest shift 1 with first-time players. Continue only if both hold:
   - they can point to the seat that took their file;
   - after Ledger 1, they predict pulls better than chance.

   Otherwise, rethink before spending on slice 2.

**Slice 2: the full run (about 18 days)**

8. **Counter-moves (2.5 d).**
   - RE-FILED insertion (clerical grounds, closed-without-authority files, unread invalid clerical citations): at the head of shift 2, and after Crane in shift 3.
   - REOPENED slips at the start of shift 3, judged by the original header.
   - FORWARD as a run of slips.
   - SUPERSEDES — VOID headers.
9. **Shift 3, the packet and endings (4 d).**
   - Regulation mode.
   - The DOM tray strip, with pages that travel with each subject's fate.
   - The final hold: the walk, page taking, unclipping, and the sufficiency rule.
   - Rewrite `endGame` (6486–6561) for the five endings and two tags.
   - The EXEMPLARY sheet.
   - SACRIFICE on OPEN.
   - COLLECTED on the knock staging.
   - Archive lines from the review records.
10. **The ledger (1 d).**
    - `showNewspaper` (4270) becomes `showLedger`.
    - The `generateNewspaper` strings (1857–1926) become clippings.
    - Add the split footer, the shift-2 floor raise and the shift-2 instruction.
11. **Documents (4 d).**
    - Canvas card art replaces card v0, card by card: 320×180, multi-sheet where needed.
    - A lean-in canvas at 1.6x devicePixelRatio.
    - Shared primitives: header, stamp, signature line, redaction, pencil note, status line.
    - A `formatRecord` helper for real data.
12. **The room's paper (2 d).**
    - The noticeboard plane in the A pose: the colleague line, the suspension, "AMENDMENTS: NONE".
    - The DOM queue tabs.
    - The five posters and the banner.
13. **Variants v1 (2 d).**
    - The six seeded decisions of §5.5.
    - The batch number on the title screen.
    - The simulator checks that every batch has a route to COMPLETE.
14. **Tuning (3 d).**
    - The simulator asserts the six reference runs (§3.12) and the letter test for every case and variant.
    - Adjust the §3.11 knobs until all pass.
    - Rewrite sections 4D, 7 and 13 of `BORD_FINAL_DESIGN.md`.

**Slice 3: polish (about 5 days; optional)**

- Poster art: halftone, misregistered red ink.
- Clipping art.
- The phone-line acknowledgment for QUERY.
- Breathing and drone polish at the desk.

---

## 11. Holes closed

**Skeptic 1: rules and exploits**

| # | Hole | The change that closes it |
|---|---|---|
| A1 | R7's "duplicate filing at this terminal" frees every queried or re-filed file | R7(c) now reads "the same subject open under two file numbers". Every amended and re-filed file is re-dated and stamped SUPERSEDES — VOID. "Second filing" becomes AMENDED. The simulator's letter test asserts `validCitations` for every case and variant. |
| A2 | A correct player can never die, so margin buys nothing and the edge is pointless | At the desk the auditor takes the tray, and during the final hold he takes the clipped pages if he arrives first. Upheld reviews cost a flat +2 in shifts 1–2. Every saved life is priced in steps, and COMPLETE requires processing cover. |
| A3 | A late flip gets UNSEALED at zero risk | An alive UNSEALED needs at least three pages. Without them counsel returns the packet (SEALED). Opening it yourself is always SACRIFICE. |
| A4 | Invisible DISMISS beats invisible RETURN; Lena's R7 fails the letter test | An unread uncited dismissal is re-filed next shift, so lasting freedom needs a permanent ground. R7(a) covers notices signed by someone in custody or named in an open file. Re-filed record-bearers carry one permanent fact reachable by reading. |
| A5 | The edge is unreachable on run 1 and a fixed script on run 2 | The queue tabs give lookahead. The noticeboard shows a colleague's RE-FILE in shift 1, and the query slip prints the correction rule. A clerical return now costs a night, not the record. Later runs draw six seeded variants. |
| A6 | The neighbour never forces a decision | He watches for 8–12 s of desk time after every consult. Filing while he watches is T5, so every re-check trades against floor time. |
| A7 | R1 leaks across dates (REOPENED files, cross-shift queries) | R1 compares the header's filing and directive dates. Re-files and amended files are re-dated; REOPENED files keep and are judged by their original header. QUERY is barred on the last two files of a shift and in shift 3. |
| A8 | Pair parity is exploitable and the cost cannot be learned | Flat costs: +2 upheld, +1 unread, +2 refused, +4 rejected, 0 for correct filings in shift 3. The Oversight call is cut. The ledger footer splits steps into failed and upheld, and the §4.2 numbers are corrected. |

**Skeptic 2: experience**

| # | Hole | The change that closes it |
|---|---|---|
| B1 | Run 1 has no stealth; run 2 has no uncertainty | Floor time is 60 / 50 / 40 s. The manual is free while no paper is on the desk, and looking is free. T5 is driven by consults and learnable on run 1. Variants restore doubt on later runs. |
| B2 | The compliant path has no dread produced by systems | T6 "unread": a stamp before the card is lifted is pulled (+1). The room reads stamps from the first file, and the lesson carries straight into shift 3. |
| B3 | The shift clock is a scheduled killer | The shift clock is cut. Floor time is the only time pressure, and nothing fires on a schedule. |
| B4 | The first-second cue is inaudible, stacked and undefined on file 17 | Review events are designed sounds at the reviewer's seat, played on the empty desk before the paper lands: one 2-second beat each, in filing order. All pending reviews resolve before the packet. |
| B5 | Looking up is taxed by the stopwatch | The stopwatch and the neighbour's watch both run on desk time only, and the dossier is hidden while looking. Looking is free, and it is the only exact read of seats and the auditor. |
| B6 | The neighbour's timer-driven eyes muddy what eyes mean | His watches open only in response to the player's reading. His eyes are unlit at the desk and seen in the A pose. |
| B7 | Camera hesitation and the forced half-lift break the eyes-only rule | Both are cut. The first pull holds the next paper until the player looks up, for at most 20 s. |
| B8 | The climax has no stakes and its numbers are inconsistent | The walk now decides whether the pages leave, and pages can be unclipped. OPEN is always SACRIFICE; OPENED is cut. The at-desk check happens before a failure's movement. The reference runs are recomputed under one-case timing. |

**Skeptic 3: build**

| # | Hole | The change that closes it |
|---|---|---|
| C1 | There is no case queue; logic is keyed to position | Step 3 builds `state.queue` and one `advanceQueue()`. Every position-keyed rule derives from the case instance or a filing counter. |
| C2 | Facts move off the sheet before cards exist | Card v0 (DOM, front, back, lean-in) ships for all 18 cases in step 4. Facts leave the detail line only in the commit that adds the verb. |
| C3 | The gate comes before the feedback channel, and `audioSilence` masks cues | Step 6 ships spatial seats and the cue kit with a perception check before the gate. Cues use a bus the silence does not mute, and the silence ends before the landing. The gate includes the neighbour and a ledger stub. |
| C4 | Concurrent documents on a single-document UI | Slips are queue items, so one document is live at a time. The next paper waits until the slip is answered, withdrawn or let stand. FORWARD and REOPENED become runs of slips. |
| C5 | The ship gate contradicts the rules; states are undefined | The resolution order is written into §3.3: filing order, the at-desk check before movement, resolution over the empty desk at shift end and before the packet, and a collection stops the batch. Six reference runs are recomputed and asserted by the simulator. |
| C6 | Validity and tells are non-deterministic | `validCitations` and `computeTells` are pure functions. The seed is mulberry32, and there is a fictional filing clock. Lena's card prints Selby's status at 23:40. Desk and consult times are injected in the simulator. |
| C7 | Kept systems are entangled with cut ones | Step 1 extracts `lightsDie` and strips the head-drop flash. Step 7 rewrites the A-look as a two-pose state, keeps the neighbour's eyes unlit at the desk, and ports test mode to the simulator. Steps 1–2 are budgeted at 2 days. |
| C8 | Paper verbs cross the DOM/WebGL boundary; the canvas is too small; the disposition box falls below the fold | Every paper verb stays in the DOM: the tray strip, drag, push and clip. Lean-in draws on its own canvas at 1.6x devicePixelRatio, and cards are 320×180 with multi-sheet support. The disposition box is pinned. |
| C9 | The estimate is half the real scope, and the playtest comes too late | Re-planned as slices, 35–45 days. Slices 0–1 (about 14 days) are the only committed scope and end in a kill-point playtest. |
