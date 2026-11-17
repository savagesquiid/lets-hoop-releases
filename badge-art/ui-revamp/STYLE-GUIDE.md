# LET'S HOOP UI revamp: "Street night" style guide

**Release: next update. Not part of the current badge/HUD work.** Approved mockups are in `mockups/`:
`home.png`, `player.png`, `badges.png` and `store.png`.

The look is a night-time outdoor court behind dark panels, with neon edges, slanted condensed italic type, and
brush-stroke and torn-paper accents, like NBA Street. The neon glow belongs to the **interface only**. The court
behind it stays dry, matte and calm: no wet asphalt, no reflections.

## Leave these out (they're mockup leftovers)

- Every **crown** (on labels, ladder nodes, clothing, and the corner logo marks) and every slogan ("Next Level",
  "Skill Builds Legends").
- The **badge art and names** on the badges mockup. They're placeholders: use the approved shield badges, real badge
  names and the four categories from `../manifest.json`.
- **"My Court"** in the player screen's top tabs. It's dropped.
- The mockup's attribute names (Free Throw, Shot IQ, Post Fade). Use the game's real attributes.

## Navigation (final)

| Rail item | Game screen |
|---|---|
| Home | Home (matchday) |
| Train | Train |
| Bracket | Bracket / ladder (the mockup's "Progression") |
| My Player | Player: attributes, badges, moves, closet |
| Online | Multiplayer (the mockup's "Crew") |
| Store | Store |
| Life | Life: deals, sponsors, trophies |
| Settings | Settings, at the bottom of the rail |

- **Desktop:** a left rail with a neon icon plus a label. The active item gets an orange brush-stroke behind its
  label and an orange glow on its icon.
- **Phone:** a bottom bar with 5 items: Home, Train, My Player, Bracket and More. More opens Online, Store, Life and
  Settings. The HP pill in the header also opens the Store.

## Colour

| Token | Hex | Use |
|---|---|---|
| `--night` | `#0A0D14` | page base behind the court image |
| `--panel` | `#10141E` at 85 % | cards and panels |
| `--panel-edge` | `#2A3142` | resting 1 px panel border |
| `--text` | `#F5F3EE` | primary text |
| `--muted` | `#9AA3B5` | secondary text |
| `--gold` | `#FFC21A` | primary buttons (Buy, Play Game), "New" stickers, the active tab chip, **Shooting** |
| `--orange` | `#FF8A1F` | home team, active rail item, primary glow |
| `--magenta` | `#FF2BD6` | player card, away accents, season goals, attribute bars |
| `--cyan` | `#2EC8FF` | secondary buttons (Try On, Quick Sim), **Playmaking** |
| `--red` | `#FF3B4E` | **Defense** |
| `--purple` | `#B04CFF` | **Finishing**, Hall of Fame |
| `--green` | `#3EE08F` | **Physicals**, "Owned" stickers |

Category colours are the same everywhere: the badge tabs, the attribute tabs and the badge progress bars.
The player's **crest colour** (amber, red, orange, cyan, magenta or blue) can replace magenta as the player-card accent.

## Glow rules (keep them cheap on phones)

- Glow goes on **edges, buttons, active tabs and progress bars only**. Never put a blur behind large areas.
- Edge glow is a 1–2 px border in the accent colour plus `box-shadow: 0 0 12px <accent at 55%>`. Hover or focus
  raises it to 20 px.
- No `backdrop-filter` on scrolling content. Panels use a solid 85 % fill.
- Animate only `opacity` and `transform`, and respect `prefers-reduced-motion`.

## Type

- **Logo:** the graffiti-style LET'S HOOP wordmark, a new asset (see textures).
- **Headings, tabs, buttons, numbers:** Saira Condensed 800, *italic*, UPPERCASE, slight letter spacing (the game
  already loads it).
- **Body:** Barlow 500 / 600.
- **Big numbers:** OVR in the header and on the player card, 72–96 px italic. The rest of the scale is 32 / 22 / 16 / 13 px.

## Building blocks

- **Slanted tab chip:** a parallelogram (`transform: skewX(-12deg)`, with the text skewed back). It's dark when idle.
  When active it fills with its category colour, with a brush-stroke edge.
- **Primary button:** a gold fill, dark text, skewed, with an icon on the left (Play Game, Buy).
- **Secondary button:** a cyan 2 px outline with cyan text (Quick Sim, Try On).
- **Disabled:** a grey fill, no glow (e.g. Buy on an owned item).
- **Card:** a dark panel with a 2 px accent edge and a glow. Feature cards (matchday, player card) get a torn-paper
  or grunge frame texture.
- **Label tag:** a brush-stroke strip behind small uppercase text ("MATCHDAY", "LADDER PROGRESS", "HALL OF FAME").
- **Progress bar:** an 8 px track in `--panel-edge` with a glowing fill in the accent colour. The count ("6/10")
  goes to its right.
- **Ladder track:** one line with milestone nodes. Reached nodes glow and the next node pulses gently.
- **Pills:** OVR in orange with a brush shape. HP is a magenta outline with a basketball coin icon.
- **Stickers:** "NEW" (gold) and "OWNED" (green), as rotated stickers on the corners of store cards.
- **Player stage:** the 3D player stands on a glowing ring (Store) or under the floodlight (Home), on the left on desktop.

## Screens

- **Home:** the player on the left. On the right are the matchday card (both crests, team names, Play Game, Quick
  Sim), the ladder track, and two goal cards (daily goal, season goal).
- **My Player:** the player card (portrait, OVR, name, archetype, crest, top 3 badges) next to the attribute tabs and
  bars. The badges, moves and closet sub-tabs keep the same chips.
- **Badges:** the four category chips, a grid of the approved shield badges in their tier metals with progress bars
  (locked ones greyed out), and a detail panel for the selected badge.
- **Store:** the player on a ring on the left. On the right are the category chips and product cards (picture,
  name, colourway, HP price, Try On and Buy, with New and Owned stickers).
- **Train, Bracket, Online, Life:** use the same cards, chips and buttons. Bracket shows a real bracket tree with your path lit.

## Assets to make

1. The graffiti LET'S HOOP wordmark.
2. Brush-stroke strips: three widths, as tintable WebP/SVG masks.
3. Torn-paper and grunge card frames, as a 9-slice `border-image`.
4. A neon icon set: Home, Train, Bracket, My Player, Online, Store, Life, Settings, the coin and the stopwatch.
5. The player-card portrait, rendered from the game's own 3D player into the card frame.
6. Store item thumbnails, auto-rendered from the 3D models on a mannequin.
7. Opponent crests: simple ones from team colours plus an initial, or unique art later.

## Phone

The rail becomes the 5-item bottom bar. Cards stack in one column, and the player stage shrinks to a header strip
behind the matchday card. Touch targets are at least 44 px. Every control also needs a visible keyboard and controller
focus state, using the same glow as hover.
