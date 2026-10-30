# The surfer‑side app

The waterproof phone lives in a wetsuit pouch. It has a short feature list and a
long robustness list: wet hands, salt water, a radio link that drops every
duck‑dive.

## Core jobs

- **Telemetry**: GPS position and, when a chest strap or watch is paired, heart
  rate, a few times a second, over UDP or MQTT so a dropped packet never stalls
  anything.
- **Voice**: push‑to‑talk or always‑on audio to the station, and one‑way audio
  *in*, so the rider at home can speak to the surfer between waves.
- **Camera bridge**: the phone owns the Wi‑Fi link to the 360° camera (start,
  stop, battery, status) so the camera's own app is out of the loop.
- **One glanceable screen**: heat timer, score, who is riding along, whether
  the mic is open. Nothing else.

## Constraints that shape it

- **Buffer and replay**: everything is written locally and re‑sent on
  reconnect; the link will be lost every time the surfer goes under.
- **No fine touch**: huge targets, voice, or a single hardware button.
  Touchscreens misfire wet, so the UI locks during rides and unlocks on a long
  press.
- **Battery and heat**: screen mostly off, radio duty‑cycled, a dark UI.
- **Pairing on the beach**: surfer ↔ rider pairing happens before the heat by
  QR or NFC at the station, never in the water.
- **Fail quiet**: if the link is gone, the surfer should not notice. The rider
  sees a "between waves" card and the mast camera instead of a frozen frame.

## The simplest version to prototype first

The phone as a pure sensor and relay in the wetsuit, no screen use at all; all
control from the station. Add the screen only when a surfer asks for it.

## Open questions

- Which waterproof phones and pouches survive a season of Atlantic beach breaks
  without fogging or losing the camera link.
- Whether 2.4 GHz Wi‑Fi from the mast reaches 200–300 m to the lineup with the
  phone at water level, or whether a small buoy repeater is needed.
- Heart‑rate straps under a wetsuit: which stay put.
