# The night‑light rig

A light that follows one surfer.

## Idea

The station already tracks the active surfer for the zoom camera. Mount two or
three battery floodlight heads on the same motorised pan‑tilt (or a second
head slaved to the same bearing) and they follow the same target. One lit lane
on an otherwise dark bay; everything else stays night.

## Candidate heads

Adrian's hint was "Norwegian battery‑powered Moonlight brand products". That is
**Moonlight Norway Mountain Gear AS** (Åndalsnes), whose Bright As Day series
are high‑output headlamps rather than floodlights:

| Head | Lumen | Weight (with battery) | Runtime | Mount | Rating | List |
|---|---|---|---|---|---|---|
| Bright As Day 4000 | 4,000 | 522 g | 1.5–30 h | GoPro quick clip | IP67 | NOK 4,999 |
| Bright As Day 3000 | 3,000 | 500 g | 2–40 h | GoPro quick clip | IP67 | NOK 3,699 |

Their heads are aluminium with a thermal design meant to hold rated output
across the battery, which matters for a rig that runs on full for a 20‑minute
heat. Three 4000 heads together are in the range of a car's high beams, pointed
where it matters. Batteries are 71 Wh (14.8 V) packs, swappable, so a crew can
run spares.

The GoPro mount is the reason they fit: the pan‑tilt bracket needs only a row
of GoPro fingers, which is a trivial print or an off‑the‑shelf part.

Alternatives, if Moonlight does not want to play: any IP67 LED work light with
a 12–24 V input, driven from the station's main battery. Heavier, cheaper,
less of a story.

## Bracket

- Pan‑tilt: a weatherproof two‑axis gimbal rated for ~2 kg at the end of a
  short arm; the camera already needs one, the lamps add about 1.6 kg.
- Mount lamps above and either side of the zoom camera so their beams converge
  at 80–150 m.
- Beam angle: Moonlight heads are spot‑biased (15–30° cones). That is what a
  "follow light" wants; a flood would light the whole bay and ruin night
  vision for everyone.
- Hard stops on tilt so a lamp can never point at the beach crowd, the judges'
  tent or the road.

## Tracking

The pan‑tilt follows whichever surfer is "active" for the heat: a mix of GPS
from the surfer's phone (coarse, but enough to point within a few degrees) and
the zoom camera's own motion tracking (fine). Manual override from the crew's
tablet always wins.

## Safety framing, in the words we use in public

> This assists a short night session for experienced surfers, with lifeguards
> present and the park's permission. It does not, on its own, make night
> surfing safe.

Things we do not do: light a session where lifeguards are not present; light
beginners; aim lamps at anyone's eyes at water level; run a night session
without the organisers' and the park authority's written agreement.

## Open items

- Confirm with Moonlight whether their "Proffbruker" programme covers a loan of
  three heads plus batteries for a pilot.
- Measure actual lux on the water at 100 m with three heads; the car‑headlight
  comparison is a sanity check, not a measurement.
- Local rules in the Parque Rural de Anaga on artificial light at night (bird
  nesting, turtles, dark‑sky considerations on the north coast).
