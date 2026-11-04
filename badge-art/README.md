# LET'S HOOP badge art

All 20 badges in the gold-shield style. Each badge comes in five tiers that line up with
`TIER` in the game (`0 Not earned, 1 Bronze, 2 Silver, 3 Gold, 4 Hall of Fame`).

| Folder | What it holds |
|---|---|
| `webp/` | Game-ready art at 120×160, transparent, about 7 KB each (~740 KB for all 100). Use these in the game. |
| `png/` | Masters at 240×320, transparent. Use them for store pages, marketing, or re-exporting at another size. |
| `source/` | The original generated images, plus the tier reference the colours were sampled from. |
| `manifest.json` | Each badge key with its name, group, stat counter (`c`), and a file path for every tier. |

File names are `<key>_<tier>.webp` or `.png`. `key` is the badge's `k` in `BADGES`
(`rim`, `atr`, `contact`, `range`, `elbow`, `cold`, `dime`, `handles`, `first`, `wall`,
`hawk`, `swat`, `board`, `vision`, `hot`, `downhill`, `shadow`, `bully`, `paint`, `pop`).
`tier` is one of `locked`, `bronze`, `silver`, `gold`, `hof`, in the same order as the `TIER` index.

## Art rules (keep them if anything is regenerated)

- Same frame on every badge: black pentagon shield, bevelled metal border, thin inner line, glossy black field.
- The pictogram is shaded in the tier's metal. There is no flat white anywhere, except the white defender on Through Contact.
- Tiers change only the metal. The gold art is recoloured using colours sampled from `source/tiers-reference.png`.
  "Not earned" is the gunmetal version, darkened a further 22 %.

## Where badges appear in the game (as of build 0.23.0)

- `rBadges()`: the Badges screen. Each `.bdg` card has a name, a `.tier tN` label, pips, a progress bar and text.
- The in-game HUD strip `#hsb`: the top two badges currently making progress.
- After a game (and `mpGameOver()` in multiplayer): the "Badge upgraded: …" messages, and the `bprog` progress list.
- The build creator: the Hall of Fame / Gold / signature badge lists for an archetype.
- The dev badge editor (`plist('dev:bd', …)`).

The `.badge` CSS class is also used for trophies and sponsor deals. Those are not badges, so leave them alone.
