# Strategy

One step at a time, with a plan for the seasons when nobody is here.

## What we are actually building

Not a station. Not a satellite link. Not a light. Those are tools we may or
may not need. What we are building is **the feeling Eoin described after a
phone video from the shore at Benijo: that he was there.** Everything else is
in service of making that feeling repeatable, for people who don't have a
friend standing in the waves with a phone.

The founder's earlier project, SensOcto, wrote the thesis down in January 2026:
*connection is felt, not performed*. It also wrote down the test it never got to
run: *find ten people who say "I need this", not "sounds cool"*. Eoin is the
first. This project exists to find the other nine, and to serve them.

## The rule for every step

A step is one thing one person can finish in one day, and at the end of it a
real person feels something. If a step needs two weeks of building before
anyone feels anything, it is the wrong step; split it or drop it.

Each step has a **done signal** (how we know it worked) and a **kill signal**
(how we know to stop and try something else). Nothing proceeds to the next
step on enthusiasm alone.

## The steps, in order

| # | Step | Done signal | Kill signal | Needs |
|---|---|---|---|---|
| 0 | Repo, decks, the ask (done 30 Oct 2026) | this file exists | — | an evening |
| 1 | **A five-minute clip for Eoin** from the Almáciga championship, raw footage from people already filming | Eoin has it | nobody will share footage: shoot it on the phone instead; still done | one beach day |
| 2 | **A video a week.** Repeat step 1 as a habit, with Eoin and two more people who cannot get to a beach. No software; WhatsApp is the platform | three people say "I need this" without being asked | after six weeks nobody beyond Eoin has asked for the next one | a phone, a shore, an hour a week |
| 3 | **Live, zero build.** A phone on the beach, a video call to Eoin, he says where to point it | one 20‑minute live session; a list of what broke (wind, audio, signal, battery) | the live version is clearly worse for him than the clip | a phone, a windscreen for the mic |
| 4 | **Live 360°, consumer kit.** A 360° camera streaming to a private link; Eoin looks around on his own from his eye‑gaze device in a browser | he turns his head (or gaze) and the view follows | the latency or the controls make it worse than step 3 | one camera, one afternoon of setup |
| 5 | **The station, minimal.** The subset of SensOcto that matters: pairing room, voice both ways, buffering through dropouts, bandwidth that follows attention. Beach test morning at Benijo | one surfer, one rider at home, one morning, numbers for link and battery | the kit takes two people more than an hour to set up | the `docs/sensocto-digest.md` subset, Q1 2027 |
| 6 | **A lesson with a remote seat** at PerfectTen, weekly through spring | a remote student comes back for a second lesson | the instructor says it gets in the way | step 5 kit, one instructor |
| 7 | **The heat at Almáciga 2027** | it happens; co‑riders vote a people's wave | organisers say no: step 6 continues and is already worth it | steps 5–6, the organisers' yes |
| 8+ | Night rig, peer‑to‑peer transport, phones as mesh, other audiences | one line each in `later.md` | — | a reason pulled from a real person |

Steps 1–3 need no code and no money. That is deliberate: they are the nail
test, and they are also the steps that can be done from a potato field in
Chamorga on a bad month.

## What we don't do

- Build a feature nobody named has asked for. Every feature traces to a person.
- Add an audience before the current one is served. ALS first, because Eoin.
- Open a partner conversation while a previous one is still unanswered.
- Let an AI agent add scope. Agents maintain, test, summarise and translate;
  humans add features, and only from the table above.
- Confuse breadth for progress. SensOcto's history is the warning: 90,000 lines,
  58 documents, and the nail test still unrun.

## Seasons

This project has one founder whose availability comes in seasons, and its
history will have bursts and gaps. The plan is built for that, not in spite of
it. `NOW.md` always states the current **mode** and the single current step.

### ACTIVE

Normal operation. One step at a time from the table. `NOW.md` updated when the
step changes.

### HIGH

Lots of energy, many ideas, many conversations possible at once. Rules that
apply in this mode, agreed in advance:

- **Commit, don't push.** New ideas go to `later.md` the moment they arrive,
  one line each. They do not go to partners, sponsors or institutions the same
  day.
- Anything involving money, contracts, legal commitments or a message to an
  institution waits **24 hours** and gets a **second reader** before it is sent.
- No messages to organisations between 22:00 and 08:00.
- At most **one new external conversation per day**.
- One step at a time still holds, even when ten feel possible. The table is
  the table.
- The founder, or the second maintainer, can set the mode to HIGH in `NOW.md`.
  Nobody needs to justify it.

### QUIET

Low energy, the founder is in Chamorga growing potatoes and building walls, or
anywhere else, for weeks or months. This is a valid mode of the project, not a
failure of it. Rules:

- **The project is allowed to sleep.** A dormant project is not a dead one. The
  repo is built to wait.
- No new commitments. Open conversations get the short note in
  `docs/templates/away-note.md`; nobody is left hanging.
- Any kit goes to the loan library (the school or the organisers hold it), so
  it keeps being useful.
- The **minimum unit** — a short video to a friend who cannot be there — is the
  only work, and it counts as the project running. It can be done from a field.
  It is also good for both people.
- CI and dependencies stay green by automation. Agents do maintenance only.
- A **monthly digest** is written (by a person or a scheduled agent) into
  `docs/digests/`, one page: what changed, what is waiting, what the next step
  still is. A returning human reads one page, not six months of history.
- The second maintainer answers the door. They do not have to build anything.

### Coming back

Read `NOW.md`, the latest digest, and `later.md`. Pick up the single current
step. Do not read everything. Do not apologise for the gap in the commit log.

## People

The plan has to name humans; a repository cannot answer a message.

| Role | Who | What they do |
|---|---|---|
| Founder | Adrian Ibáñez | sets the mode, does the steps, names the rest |
| Second maintainer | [name] | write access; answers the door in QUIET; second reader in HIGH |
| First participant | Eoin Egan | the person every step must reach; the one who says whether it felt real |
| Check‑in | [name] | gets a message if `NOW.md` has not changed in 60 days and the founder hasn't said why |
| On the beach | PerfectTen, the Sports Service | hold the kit in QUIET, host the steps in ACTIVE |

The founder fills the brackets in daylight, not at night.

## What the AI does, honestly

Claude wrote most of this repository in one session and will keep helping, but
it does not run between sessions, does not remember beyond its notes, and
cannot message anyone on its own. What it can do:

- Any session opened on this repository (by the founder, a contributor, or a
  scheduled job) reads `CLAUDE.md` and picks up the project's state, rules and
  current step without a human briefing.
- Act as the second reader in HIGH when a human asks.
- Write digests, translations, tests and docs in QUIET when scheduled.
- Never add features, audiences or partners on its own.

The torch is carried by the repository and by people. The AI keeps it readable.

## Review

This file is reread, in daylight, by the founder and the second maintainer,
whenever the mode changes. Changes go through a pull request with a 24‑hour
wait, which is itself one of the rules.
