# Archetype crests (next update)

**Release: next update. Not part of the current badge/HUD work.**

Six circular "burning core" crests: a dark charred disc, a molten-gold pictogram glowing from inside with heat cracks,
and an outer glow in the archetype's colour. Archetypes in the same family share a crest.

| Key | Crest | Archetypes | Pictogram | Glow |
|---|---|---|---|---|
| `shooter` | Sharpshooter / Stretch | Sharpshooter, Stretch big | crosshair over a ball | amber `#FFB020` |
| `lockdown` | Lockdown / Rim protector | Lockdown, Rim protector | open palm, stop | red `#E5402C` |
| `slasher` | Slasher | Slasher | lightning bolt through a ball | orange `#FF7A1A` |
| `playmaker` | Playmaker | Playmaker | ball sending out pass arrows | cyan `#38C6F4` |
| `creator` | Shot Creator | Shot Creator | crossover dribble path ending at the ball | magenta `#E040FB` |
| `post` | Post scorer | Post scorer | mailbox with a ball as the mail | blue `#2F7FE0` |

- **Where it shows:** it replaces the Ego mode icon while Ego is active (it swaps in and glows; the Ego bar stays the
  timer), and it's the 38 px emblem on the player panel.
- **Dual builds:** while Ego is active, the crest crossfades smoothly back and forth between the main and the secondary
  archetype's crest. A build whose two archetypes share a crest shows just that one and doesn't crossfade.
- **Files:** `png/<key>.png` 256×256 and `webp/<key>.webp` 128×128, both transparent. The disc is about 80 % of the
  width and the glow fades out to the edge. They're checked at 60 px (the Ego button) and 38 px (the emblem).
- **Sources:** `source/` holds the original generated images.

## Ego mode change (also next update)

The crests ship together with a change to how Ego mode works:

- **Ego boosts only the player's own archetype categories.**
- **Pure build** (both archetypes from the same family): a flat **+8** to its archetype categories.
- **Dual build:** **+5** to the main archetype's categories and **+3** to the secondary archetype's.
- This replaces the current Ego boost. The Ego crest swap and the dual-build crossfade above show when this boost is on.

- **Categories** are both the archetype's primary and its secondary attributes.
- **Overlap:** if an attribute is in both archetypes of a dual build, the boosts add up: +5 + 3 = **+8**, the same as
  the pure-build max. No attribute gets more than +8 from Ego, and Ego never takes a rating past 99.
  Example, Shot Creator (main) + Playmaker (secondary): mid-range +8, speed +8, shots on the move +5, layups +5,
  passing +3, ball handling +3, steals +3, everything else +0.

Still to confirm with the user: that the overlap reading above is right (sent to them for a yes or no), and that
"the limit" means the +8 max, with ratings also capped at 99.
