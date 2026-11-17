# Founder's Crest

Earned by players who joined in early access. It shows next to the player's name wherever the name appears.

| File | Size | Use |
|---|---|---|
| `founder-mini-32` / `-64` / `-128` (png, webp) | 32, 64, 128 px | **Next to the player name everywhere**: menus, HUD, scoreboard, online lists, bracket. Use 32 for names under ~24 px tall (it reads down to 18 px), 64 for the header, 128 on hi-DPI. |
| `founder-full-256` / `-512` (png, webp) | 256, 512 px | **Player card, profile, and the screen where it's earned.** Has corner rivets and court lines, so don't use it below ~38 px. |

- Both are transparent, full colour (gold): don't tint them. Cut to the octagon, with no glow; the game can add its own.
- Design: a gold octagon, the L'H with a basketball as the apostrophe, a star above, and a laurel wreath. No crown.
- `source/` holds the original generated images.
- Canvas board: "Founder's Crest · full and mini" (asset ids: full-512 `aa2df6b4bc9c3f0da142313c15f987cc`, mini-128 `d2d809c4bf64bf04209e61beb33e21c1`).
