# Archetype crests (next update)

**Release: next update. Not part of the current badge/HUD work.**

Six circular "burning core" crests: a dark charred disc, a molten-gold pictogram glowing from inside with heat cracks,
and an outer glow in the archetype's colour. Archetypes in the same family share a crest.

The game has five archetypes (see the roadmap). The crest follows the archetype **name the player sees**, so
Slasher has two crests: the bolt for guards and wings, and the mailbox when it shows as Post at PF and C.

| Key | Crest | Shown for | Pictogram | Glow |
|---|---|---|---|---|
| `shooter` | Sharpshooter / Stretch | Sharpshooter (Stretch at PF and C) | crosshair over a ball | amber `#FFB020` |
| `lockdown` | Lockdown / Rim Protector | Lockdown (Rim Protector at PF and C) | open palm, stop | red `#E5402C` |
| `slasher` | Slasher | Slasher at PG, SG and SF | lightning bolt through a ball | orange `#FF7A1A` |
| `post` | Post | Slasher shown as Post at PF and C | mailbox with a ball as the mail | blue `#2F7FE0` |
| `playmaker` | Playmaker | Playmaker | ball sending out pass arrows | cyan `#38C6F4` |
| `creator` | Shot creator | Shot creator | crossover path ending at the ball | magenta `#E040FB` |

- **Where it shows:** it replaces the Ego mode icon while Ego is active (it swaps in and glows; the Ego bar stays the
  timer), and it's the 38 px emblem on the player panel.
- **Dual builds:** while Ego is active, the crest crossfades smoothly back and forth between the main and the secondary
  archetype's crest. A build whose two archetypes share a crest shows just that one and doesn't crossfade.
- **Files:** `png/<key>.png` 256×256 and `webp/<key>.webp` 128×128, both transparent. The disc is about 80 % of the
  width and the glow fades out to the edge. They're checked at 60 px (the Ego button) and 38 px (the emblem).
- **Sources:** `source/` holds the original generated images.

## Ego mode change (also next update), FINAL

The crests ship together with a change to how Ego mode works. Ego now gives **point pools**, and each pool is split
**evenly** across an archetype's attributes. An archetype's attributes are both its primary and its secondary ones.

- **Dual build:** the main archetype gets a pool of **8**; the secondary archetype gets a pool of **5**.
- **Pure build:** one pool of **10**.
- An attribute in both archetypes gets points from both pools. Ratings never pass 99.
- This replaces the current Ego boost. The crest swap and the dual-build crossfade show when it's on.

Example, Shot Creator (main) + Playmaker (secondary):

| Attribute | Shot Creator pool (8 ÷ 4) | Playmaker pool (5 ÷ 5) | Ego total |
|---|---|---|---|
| Shots on the move | +2 | | +2 |
| Mid-range | +2 | +1 | +3 |
| Speed | +2 | +1 | +3 |
| Layups | +2 | | +2 |
| Passing, ball handling, steals | | +1 each | +1 each |

Still to confirm with the user: how leftovers are handled when a pool doesn't divide evenly (proposal: one extra point
each to the archetype's primary attributes first).
