# Concept

## The sentence

One heat at a surf competition that anyone can join from home, paired live with
one surfer, both ways.

## Why a competition and not a stream

A broadcast has viewers. A heat has participants. The difference is pairing:
one person at home is attached to one surfer for the duration of a heat, hears
the same briefing, chooses what to look at, talks to their rider between waves,
and casts a vote that the surfer knows about. The person at home is not the
audience; they are in the lineup, by proxy.

The official judging does not change. Open Lineup adds a **people's wave**
voted by remote riders, which sits beside the scores and never replaces them.

## Roles

| Role | Where | Carries | Does |
|---|---|---|---|
| Rider at home | Anywhere with internet | The eye‑gaze device, switch, or tablet they already use | Watches the 360° feed, looks around, talks, votes |
| Camera surfer | In the water | Waterproof phone in a wetsuit pouch, 360° camera on board or wrist, optional HR strap | Surfs the heat; talks to their rider between waves |
| Station crew (2) | On the sand | The tripod kit | Sets up in 30 minutes, runs pairing, watches batteries and link |
| Organisers | Beach | Nothing new | One heat slot, a permit, a corner of the sand |
| Lifeguards | Beach | Nothing new | Same role as always; veto over any night session |

## What a heat looks like

1. **Pairing**, the evening before or the morning of: each camera surfer is
   matched with a rider at home. They meet on the call. Pairing is done on the
   beach by QR or NFC, never in the water.
2. **Briefing**: the rider hears the heat briefing through the beach mic and
   sees the lineup from the mast camera.
3. **The ride**: the rider sees the board's 360° view, head‑tracks or gazes to
   look around, hears the water. The station's zoom camera follows the active
   surfer.
4. **Between waves**: one held gaze (or one switch press) opens the rider's mic
   to the surfer's phone for a few seconds. Short, real, both ways.
5. **Vote**: riders vote the people's wave. The result is read out with the
   heat result.
6. **After**: the rider keeps the replay of "their" waves. Nothing is published
   without both people saying yes.

## What a lesson looks like

Same kit, no competition. A surf school adds one remote seat to an ordinary
group lesson. The instructor wears a chest or helmet camera and a phone in the
wetsuit. The remote student joins the warm‑up and theory, rides along with the
instructor's camera (or with a volunteer who is "their body" that day), can
speak to the instructor between sets, and joins the feedback round. The
instructor says what they always say; the station carries it.

Three offers follow naturally for a school: a **remote seat** (free or
sponsored, through patient associations), a **family link** (paid add‑on for
camp families watching a first wave live from abroad), and a **lit session**
(dusk or night, advanced students, small group, lifeguard present).

## The station

Fits in one car boot. Two people, about thirty minutes, no generator, no cable
across the sand, nothing fixed to the beach.

- **Starlink Mini** for the uplink (about 1.1 kg, 25–40 W, IP67).
- **Beach radio**: a directional Wi‑Fi link aimed at the lineup plus a mesh node
  by the judges. Phones and cameras in the water talk to this, not to the
  satellite.
- **Edge box**: a fanless mini PC. Mixes feeds, buffers them through
  duck‑dives, runs pairing and the vote, records locally.
- **Cameras**: one 360° on the mast for the whole bay, one zoom camera on a
  pan‑tilt that tracks the active surfer, plus the surfers' own cameras.
- **Power**: one 1 kWh LiFePO4 pack for a day of heats, a folding panel to top
  up, separate packs for the lamps.
- **Lights** (optional): two or three battery floodlight heads on the same
  pan‑tilt bearing as the zoom camera. See `night-light-rig.md`.

## What we deliberately do not claim

- The lights **assist** a short night session for experienced surfers, with
  lifeguards present and the park's permission. They do not make night surfing
  safe on their own.
- The remote rider is not a judge and does not affect official scores.
- Nothing here has been tested on a beach yet. The first test morning will
  produce real numbers for link, battery and how it feels, and those will
  replace the estimates in these documents.

## Why open

Assistive technology dies when its vendor does. The station, the apps, the
bracket drawings and the build guide are published so a school in Galicia,
Portugal or anywhere else can rebuild it without asking. Partner money buys kit
and beach days, not equity. Participants own their data.
