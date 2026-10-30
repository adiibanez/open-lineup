# SensOcto digest

What the founder's earlier platform taught, what transfers to Open Lineup, and
what stays behind. Written from a full read of `adiibanez/sensocto` (404
commits, Jan 2025 – Apr 2026, ~92,000 lines of Elixir plus ~49,000 of
JS/Svelte) and `adiibanez/iroh_ex` (188 commits, Mar 2025 – Oct 2026) on the
night of 30 October 2026. Independent code inventories were run on each repo
and cross‑checked against the docs; where a README claims something the code
does not do, this digest says so.

## The essence, in SensOcto's own words

From `docs/VISION.md` (January 2026):

> Connection is felt, not performed.

> Find 10 people who say "I need this." Not "sounds cool." Actual pull. That's
> the nail test.

> Which community first?

SensOcto never ran its own nail test; the open question stayed open while the
platform grew eight sensor types, nine languages, a biomimetic back‑pressure
layer, 3D splats, MIDI, whiteboards, a graph view and four SDKs. Open Lineup
is the nail test. The first nail is Eoin, who answered the question with one
WhatsApp message after a phone video from the shore: *feels like I am there*.

The lesson that matters most is not technical: **the presence channel that
worked first was a phone, a friend, and mostly silence.** No ECG, no P2P, no
adaptive anything. The platform's thesis was right; the platform was not the
shortest path to it.

## The learning curve that transfers

These are ideas SensOcto got right, independent of the code:

1. **Attention decides bandwidth.** SensOcto sends sensor data at full rate only
   to what a viewer is actually looking at (focus, hover, viewport), and tells
   the *producer* to slow down otherwise. On a 15–25 Mbit/s satellite uplink
   shared by a 360° feed, a zoom feed, surfers' cameras and voice, this is the
   whole bandwidth plan: the rider's gaze is the attention signal; what they
   look at gets the bits, the rest degrades to snapshots. The call layer even
   has the tiers written down (`Calls.QualityManager`: active 2.5 Mbit/s →
   recent 500 kbit/s → viewer snapshots 50–100 kbit/s → idle ~0).
2. **Isolate failure domains.** A seven‑layer OTP supervision tree with a
   written blast‑radius table. The beach station must survive a camera crash,
   a radio hiccup and a satellite handover without losing the voice call; this
   is how.
3. **Back‑pressure is a conversation, not a wall.** Producer, server and viewer
   each adapt; nothing drops silently. The surfer's phone should behave the
   same way through a duck‑dive.
4. **Pairing without accounts.** Join codes, QR, guest sessions with a token
   and a TTL. A rider at home and a surfer on the sand pair the same way.
5. **Simulate before you ship.** A 50‑sensor simulator with scripted scenarios
   let the pipeline be tested without hardware. Open Lineup needs a simulated
   heat (two surfers, one rider, a flaky link) before a single beach day.
6. **Test the pipeline, not the UI.** The strongest tests in SensOcto are the
   contract tests around the data path. Keep that habit; skip the rest.

## What is solid and worth lifting (code)

Roughly 5,000 of the 92,000 lines, all on the tested hot path:

| Piece | Where in sensocto | Why it matters for the beach |
|---|---|---|
| Authenticated channel ingest with key whitelisting | `SensoctoWeb.SensorDataChannel`, `Types.SafeKeys` | the surfer phone's telemetry path, atom‑exhaustion safe |
| One process per sensor, ETS ring buffers with per‑type retention | `Sensocto.SimpleSensor`, `AttributeStoreTiered` | heart rate, GPS, IMU held in memory with mailbox self‑protection |
| Demand‑driven per‑viewer fan‑out with a quality ladder | `Lenses.Router`, `Lenses.PriorityLens`, `ViewerDataChannel` | exactly the shape for one rider at home |
| Attention tracker | `Otp.AttentionTracker` (+ JS hook) | swap "viewport" for "gaze direction / chosen camera" |
| Delta encoding for HR/ECG | `Encoding.DeltaEncoder`, `delta_decoder.js` | complete, tested, currently `enabled: false`; turn it on |
| Producer offline queue and connection monitor | `SensorService.svelte`, `connection-monitor.js` | the seed of dropout buffering (see risks: needs sequence numbers, disk spill, and the 30 s staleness drop removed) |
| Circuit breaker, system load monitor | `Resilience.CircuitBreaker`, `Otp.SystemLoadMonitor` | small, tested |
| SFU voice/video with TURN provisioning | `Calls.CallServer`, `CallChannel`, `CloudflareTurn`, `membrane_client.js`, `quality_manager.js` | voice both ways; a working skeleton, untested on a real link |
| Phone and wearable producers | `GeolocationClient`, `IMUClient`, `BluetoothClient` (BLE heart‑rate service) | what the surfer carries |
| Votes | `Collaboration.Poll/Vote`, `PollComponent` | the people's wave |
| Guest auth, join codes, QR | `GuestUserStore`, `GuestSession`, `Room.join_code`, `QRCode` hook | pairing on the beach |
| Kuramoto sync computation | `SyncComputer` | later: shared‑heartbeat presence between rider and surfer |

## What stays behind

Experiments and art, or scaffolding that the code does not actually use:

- **Iroh / Automerge / P2P room state.** `Iroh.RoomStore` creates fresh
  document namespaces every boot that no other node ever joins; its list
  functions return empty stubs; `RoomStateBridge` is never started;
  `RoomMarkdown`, `GossipTopic`, `CrdtDocument`, `TigrisStorage` have zero
  references outside tests; `RoomTicket` encodes nothing a peer could join
  (secret `nil`, addresses `[]`). The README's "P2P sync via Iroh document
  sync" is a plan, not a feature.
- Horde `RoomServer` (a second, unused room implementation),
  `RoomPresenceServer` (no callers), `Session.DocumentWorker` (never started),
  the clustering plan.
- The biomimetic layer (`Bio.*`: locus coeruleus, cerebellum, circadian …) —
  only the simulator uses its output.
- Media player, 3D splats, avatar, whiteboard, MIDI/Tone/Magenta, the 4,700‑line
  graph view, MediaPipe pose, AI chat, LiveView Native/SwiftUI, Unity/Rust/
  Python/three.js SDKs, the Swiss hydrology poller.
- `LobbyLive` (3,545 lines + 1,158 of template) and `RoomShowLive` (3,474) as
  modules: every subsystem is bound through them. Lift pieces, not the hubs.

## Risks to settle before lifting anything

1. **Licence.** The README says "Proprietary"; there is no LICENSE file; the
   `clients/` declare MIT. Open Lineup is CC BY‑SA / Apache‑2.0. The founder
   owns the code and can relicense; it needs one explicit commit.
2. **Nothing persists.** Measurement writes to Postgres are commented out; a
   restart loses every sample. The beach station must record to disk (the edge
   box), and the rider needs a replay/backfill path that does not exist yet.
3. **Dropouts.** The offline queue is memory‑only, drops anything older than
   30 s, has no sequence numbers, acks or gap detection. A satellite outage
   is minutes, not seconds. This is the first real engineering task of step 5.
4. **WebRTC on a satellite link** is untested: SFU + VP8 tuned for LAN/4G, no
   data channel, no store‑and‑forward, no 360° handling anywhere. The honest
   first live tests (strategy steps 3–4) use consumer apps, not this stack.
5. **No CI for the Elixir app.** No workflow runs `mix test` or `mix compile`;
   e2e and Iroh tests are excluded by default; coverage threshold is 35% with
   a long ignore list. A green badge cannot be claimed.
6. **Security loose ends.** The user socket accepts anonymous connections on a
   bad or missing token ("migration period"); a dev flag allows missing
   tokens; the Bridge socket accepts any token when unconfigured. Fine for an
   experiment, not for a stream carrying someone's heart rate.
7. **Doc drift.** HTTP ingest, Movesense ECG at 100 Hz, hot code upgrades and
   clustering are README/doc claims the code does not substantiate (ECG comes
   from the simulator; Movesense is handled as a plain BLE heart‑rate
   monitor). Open Lineup's rule: no claim without a beach test.
8. **Agents with the keys.** The sensocto GitHub Actions run Claude on labelled
   issues with permission checks disabled, and a scheduled job that implements
   backlog issues and opens PRs unattended. That is how a repository grows
   58 documents and 12 plans while the nail test waits. In Open Lineup,
   agents maintain and summarise; they never add scope (see `CLAUDE.md`).

## iroh_ex

`iroh_ex` (0.0.19 on hex.pm, iroh 1.3.0, Rustler NIF; ~150 of its 188 commits
in March–April 2025, last meaningful one a dependency bump on 5 Oct 2026) is
the founder's bridge from Elixir to Iroh's peer‑to‑peer stack. What it is:

- **A sound skeleton.** One tokio runtime per VM; one node per Elixir
  process holding a resource; gossip events forwarded into an Elixir mailbox
  through a bounded channel; relay URL and ed25519 secret key configurable;
  precompiled binaries for aarch64 Linux (a Raspberry Pi 4/5 or any 64‑bit
  ARM edge box), x86_64 Linux, macOS and Windows. Identity as an ed25519 node
  id is a good pairing key for later.
- **A research toy where it claims scale.** The swarm livebook draws
  "latency" edges from `:rand.uniform(300)`; the test suite asserts nothing
  about delivery; the CI matrix that would have measured 5–200 nodes has been
  `if: false` since March 2025; the "~4000 nodes" figure has no log, ratio or
  latency behind it anywhere in the repo. The picture is real; the number is
  a memory.
- **Not real until rebuilt:** one gossip topic per VM with a random name,
  string‑only payloads under 4 KiB, sender identity never passed to Elixir;
  blobs and docs are in‑memory and local only (no remote fetch, no tickets,
  no sync); `automerge_sync_via_gossip` is send‑only (the receive path drops
  it); `subscribe_to_topic`, `unsubscribe_from_topic`, `broadcast_message`,
  `list_topics`, `shutdown`, `connect_node_by_pubkey` are declared in Elixir
  with no Rust behind them. SensOcto pins 0.0.16 and calls three of those
  phantoms inside `try/rescue`, which is why its P2P layer is silently inert.
- **Lifecycle bugs** (found by reading, not running): a killed owner process
  leaves a zombie endpoint; a second `connect_node` detaches the old task
  rather than aborting it; a join failure unwraps inside a detached task and
  Elixir never hears of it; "connected" is emitted before the join starts.

**Fitness for the beach, by need:**

| Need | Today | Distance |
|---|---|---|
| Hold a connection through Starlink's NAT with relay fallback | inherited from iroh (QUIC hole punching, relays); self‑hosted relay possible on a "whale" box; no visibility from Elixir into direct‑vs‑relay or disconnects | short |
| A few Mbit/s of video | no stream API, gossip is 4 KiB flood, blobs cannot be fetched remotely | long (new NIF surface, untested on a lossy link) |
| Few‑Hz telemetry, pairing, votes | fits gossip, best‑effort, no acks, no sender id, no re‑join signal | medium |
| ARM Linux edge box | prebuilt | short |
| Phones in the mesh | not through this library; n0's iroh‑ffi (Swift/Kotlin) or iroh in the browser speaking the same topic is the route | long, and a different project |

**Verdict:** keep iroh_ex as reference code and a later‑phase bet (identity,
relay‑agnostic addressing, the phone‑mesh story), not as the pilot transport.
For step 5 the boring stack wins on effort: WebRTC (sensocto's Membrane +
TURN) for voice and video, Phoenix Channels for telemetry and votes, and —
if the founder wants the first real wide‑area numbers for Iroh — iroh_ex as a
side channel mirroring telemetry through a self‑hosted Linux relay, with a
two‑node beach↔home harness that finally asserts delivery. That harness would
be the first measurement the library ever had, and it is one week of work,
not a season.

If iroh_ex is ever to carry the station, in order: fix the lifecycle
(resource `down` callback, abort on reconnect, join/error events); make
gossip usable (binary payloads, sender id, real per‑topic API, remove the
phantom stubs); add a bulk path (blob tickets with remote download, or raw
QUIC streams); build the WAN harness; re‑enable CI. All of that is on the
`later.md` architecture line, pulled only when a real person needs what it
gives.

## The minimal subset, named

For strategy step 5 ("the station, minimal"), one surfer ↔ one rider:

- **Server (~5k lines, Ash only for Poll/Vote):** Endpoint + PubSub + Presence;
  `SensorDataChannel` + `SafeKeys`; `SensorsDynamicSupervisor` / `SimpleSensor` /
  `AttributeStoreTiered`; `Lenses.Router` + `PriorityLens` + `ViewerDataChannel`;
  `DeltaEncoder` on; `CircuitBreaker`; a trimmed `AttentionTracker` driven by
  the rider's gaze/camera choice; `Calls.*` for voice; a `Pairing` GenServer
  with Presence instead of the room machinery; `Poll/Vote`; guest auth.
- **Beach station producer:** `SenseApp` with `BluetoothClient` (HR),
  `GeolocationClient`, `IMUClient`; `SensorService` queue rebuilt with sequence
  numbers, disk spill and no staleness drop; `membrane_client.js` for audio.
  Video rides a separate pipeline (not in sensocto).
- **Rider client:** `CompositeMeasurementHandler` + the heart‑rate, map and IMU
  Svelte views; `PollComponent`; the call hooks; a gaze/switch input layer
  that does not exist yet and is the most important new code in the project.
- **Must be written new:** replay/backfill API, server‑side gap handling,
  disk recording on the edge box, 360° video path, the gaze input layer, and
  the decision whether telemetry rides the WebRTC data channel or the Phoenix
  channel over the satellite.

None of this is needed before strategy step 5. Steps 1–4 use a phone, a
consumer 360° camera and a video call, on purpose.
