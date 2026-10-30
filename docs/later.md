# Later

A parking lot, not a roadmap. One line per thread, so it can live here instead of
in anyone's head. We pull **one** line off at a time and work it properly;
nothing on this list is a commitment.

Rule for adding: write it down the moment it arrives, in one line, and go back
to what you were doing.

## Audiences and use cases (talk specifics first, then pick one)

- People with ALS and other high‑dependency conditions — the first case, already in the decks.
- Tetraplegia and spinal injury — same station, different input devices.
- Long hospital stays — a remote seat in a lesson as a scheduled thing to look forward to.
- Depression — presence without demand; what does "riding along" look like when getting out of bed is the hard part.
- People weighing assisted dying — an experience, not an argument; needs the right partners (palliative teams, associations) before any design.
- Addiction and recovery — shared physical experience as an alternative to isolation; partner with existing programmes.
- Loneliness in ordinary life — people in jobs or on platforms that treat them as inventory; the family‑link offer is the first toe in this water.
- Children, and anyone "sick", doing what we did on day one end‑to‑end with as little screen as possible; time spent together as the currency. (The mission in one line; keep it near the top.)
- Intimacy and sensuality for people with ALS, tetraplegia and similar — a real, under‑funded assistive‑tech problem. Scope for the AI side of this project: pairing, consent flows, interfaces for someone who moves only their eyes, privacy that holds, the clinical literature. Explicit content itself is out of scope here and belongs to whoever builds it; buttplug.io is the open‑source reference for the device side.
- Darts in a pub with a remote player (the inclusive darts game) — the same presence problem, indoors, with a drink.

## Language

- Spanish first, with a light Canarian register (`docs/es/estilo.md` to write before translating).
- German second (PerfectTen's camp families, Homebrace).
- Translation structure: `docs/<lang>/`, deck folders as siblings; Fluent or gettext when there is an app.

## Place

- Chamorga / Anaga as a base: part of the year, van, mostly offline. Decide in daylight, with a spreadsheet.
- Benijo and Almáciga as the home beaches; El Roque as backup; a station that lives on the island.

## Architecture (read sensocto and iroh_ex first, properly, when this line is pulled)

- The station as a node in a peer‑to‑peer mesh rather than a client of a cloud: phones in the water, the edge box, the rider at home, and "whale" relay nodes in data centres.
- Compute that follows renewable energy: the heavy work (video mixing, tracking) migrating between a data centre and, eventually, a cluster of participants' own phones.
- Physiological synchrony (heart rate shared both ways) as a presence channel, from SensOcto.
- What was an art project and what should become an end‑user implementation; keep both, label them.

## Hardware

- Quotes for every `[€__]` in `hardware/bom.md`.
- Moonlight "Proffbruker" form.
- Radio reach test: mast to lineup at water level.
- Anaga rules on artificial light at night.

## Funders and institutions

- Cabildo de Tenerife via IDECO / DXT Tenerife ("Activa tu vida") — already a sponsor of the Almáciga championship; the natural public funder for a beach test. After the clip exists, not before.
- Servicio de Deportes, Ayuntamiento de Santa Cruz de Tenerife — the organiser on site; the clip conversation happens with them first.

## People

- The organisers: a thirty‑minute coffee, then a test morning date.
- PerfectTen: which instructor, which beach.
- The person met in Chamorga today (to be told later).
- Patient associations in the Canaries and on the mainland for the first remote riders.
