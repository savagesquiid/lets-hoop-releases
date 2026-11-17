# LET'S HOOP badge art

All 20 badges in the gold-shield style. Each badge comes in five tiers that line up with
`TIER` in the game (`0 Not earned, 1 Bronze, 2 Silver, 3 Gold, 4 Hall of Fame`).

| Folder | What it holds |
|---|---|
| `webp/` | Game-ready art at 120×160, transparent, about 7 KB each (~740 KB for all 100). Use these in the game. |
| `png/` | Masters at 240×320, transparent. Use them for store pages, marketing, or re-exporting at another size. |
| `source/` | The original generated images, plus the tier reference the colours were sampled from. |
| `manifest.json` | Each badge key with its name, category (`group`), type (`kind`: core, signature or pure), stat counter (`c`), and a file path for every tier. |

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

## Pure archetype badges (`pure/`)

Five extra badges, one per pure archetype family. Each is a single tier that unlocks at **99 OVR** for a
pure build (both archetype slots from the same family). The shield is metallic red with a gold crown on top.

| Key | Badge | Archetype | Effect |
|---|---|---|---|
| `limitless` | Limitless | Sharpshooter / Stretch | The green window does not shrink with distance. |
| `unguardable` | Unguardable | Shot Creator | After a dribble move beats your man, the next pull-up or fadeaway within about 1 s gets a full green window, whatever the contest. |
| `launchpad` | Launch Pad | Slasher | Dunks can start from further out, and dunks through contact still go down. |
| `lockin` | Lock-In | Lockdown / Rim Protector | The player you guard can't heat up: hot streaks reset and badges like Catching Fire switch off. |
| `floorgeneral` | Floor General | Playmaker | For 3 s after catching your pass, a teammate gets a bigger green window. |

There are two states: `<key>_unlocked` and `<key>_locked` (greyed, for showing what the player is working toward).
The files are 240×380 (PNG) or 120×190 (WebP). The bottom 320 px (160 px in WebP) is the shield, exactly the size of the
other badges. The top 60 px (30 px) holds the crown, so line pure badges up with the rest by the bottom edge.

## Shot Creator archetype (new)

There's a new archetype, `create` (Shot Creator), with three new badges in the same gold style and all five tiers.

| Key | Badge | Type | Effect | Earned by (stat counter) |
|---|---|---|---|---|
| `stepback` | Step-Back Artist | Core · Shooting | Bigger green window on shots straight out of a step-back, quick stop or side-step, and the step-back creates a bit more space. | Shots made out of those moves (`rhy`, new) |
| `tough` | Tough Shot Maker | Core · Shooting | A hand in your face hurts your jumpers less. | Contested jumpers made (`tough`, new) |
| `iso` | Iso King | Signature (`arch:'create'`) · Shooting | One-on-one with the floor cleared, your defender's contests count half. | Buckets in isolation (`iso`, new) |

The archetype, as the user set it:
- **Primary:** shots on the move (pull-ups, step-backs, rhythm shots out of a move) and mid-range
- **Secondary:** speed, layups
- **Average:** standing threes (neither a strength nor a weakness)
- **Weak:** blocks, rebounding, interior defense
- **Positions:** all five
- **Linked core badges (`aff`):** `stepback`, `tough`, `elbow`
- **Signature:** `iso`
- **Pure badge (99 OVR):** `unguardable`

Any build can earn the two new core badges. Like every other archetype, Shot Creator can take its linked ones to Hall of Fame.

## Badge categories (the badges tab)

The badges tab has exactly four categories: **Shooting, Playmaking, Defense, Finishing**. There is no
"Signature" tab and no per-archetype tab. Every badge sits in the category that matches what it does.
Signature and pure are badge *types* (they decide who can earn a badge and how high it goes), not categories.

| Category | Badges |
|---|---|
| Shooting | Range Finder, Elbow Specialist, Ice Water, Catching Fire*, Trailer Three*, Step-Back Artist, Tough Shot Maker, Iso King*, Limitless†, Unguardable† |
| Playmaking | Dime Dropper, String Handles, Burst Mode, Eyes in the Back*, Freight Train*, Floor General† |
| Defense | No Easy Ones, Quick Hands, Swat Team, Board Bully, Shadow*, Paint Patrol*, Lock-In† |
| Finishing | Glass Finisher, Above the Rim, Through Contact, Bulldog Finish*, Launch Pad† |

\* signature badge (archetype-only) · † pure badge (99 OVR, pure build)

In code: `BGROUPS` becomes `['Shooting','Playmaking','Defense','Finishing']`, and each signature badge's `g` becomes
its category. Its `arch` field is unchanged, and it is still what makes a badge a signature badge.

### Badges your build can't earn

The user's decision: badges the current build can't earn (another archetype's signature badge, or a pure badge for a
different build) still show in their category, **greyed out**, so players can see what other archetypes get.
Use the `locked` art for them and say why, e.g. "Shot Creator signature" or "Pure Slasher at 99 OVR".
Don't hide them.
