# Vantage Studio

A Figma stand-in for people who **vibe-code mobile apps**.

You design a control once — lighting, shadow, radius, six states — see it on a real 16-screen flow, then copy a prompt your coding agent can actually follow. No decorative gradients. Depth comes from light.

Made at [Censai Systems](https://os.censai.app) because we couldn't use Figma and the agent kept inventing a new button every screen.

## Why it exists

Vibecoding is fast until the UI falls apart:

- rest looks different from hover
- loading is a spinner someone guessed
- errors are afterthoughts
- every agent turn adds a new purple glow

This studio treats **states as the product**. Rest / hover / pressed / focus / disabled / loading share one radius, one type, one fill family. Lighting is a vertical white/black overlay on a solid fill — a material, not a decoration.

## How to use it (5 minutes)

1. Open the studio. **Deck** is the 16-screen Vantage example. **Toasts** is the status system.
2. In **Inspect**, tune the live button. Production spec: solid, brand `#330f57`, bevel 24%, round 14px, 48px tall, lift shadow.
3. Flip screens. Every primary CTA follows the live spec.
4. Open **Hand off**. Copy **Agent** into Grok, Cursor, Claude, or OpenCode.
5. Or copy **Skill** into `.cursor/skills/vantage-ui/SKILL.md` or `.grok/skills/vantage-ui/SKILL.md` so the agent keeps the system after the chat ends.

To restyle for *your* app: change the fill hex. Keep the overlay recipe, the state table, and the toast geometry.

## Production tokens

| Token | Value |
|---|---|
| Brand | `#330f57` |
| Paper | `#f4f1ea` |
| Ink | `#161513` |
| Surface | `#fffcf7` |
| Danger | `#9f3a2f` |
| Ok | `#3d6b4f` |
| Type (app) | Poppins |
| Button | 48px × 14px radius |

## States (do not skip)

| State | Treatment |
|---|---|
| rest | Lighting + rest shadow. No translate. |
| hover | Lift 1px. Step shadow up one level. |
| pressed | `scale(0.96)`. Inset well. Lighting inverts. |
| focus | 2px ink ring, 3px offset. |
| disabled | 40% opacity. No pointer. |
| loading | Spinner replaces the label. No pointer. |

## Toasts

- **Dock** — ink bar, green `#7fc98f` dot, `bottom: 86px` so it clears the tab bar.
- **Send** — one row per destination. Spinner until the other side confirms. Never a fake success.
- **Working** — same brand fill and 24% bevel as the button.
- **Parse word** — brand fill wipe via `--p`, ~3s cap, then green complete.
- **Fail** — warm paper, compact retry, data stays.

## What's in this repo

- `SKILL.md` — drop into your agent's skill folder
- `css/vantage.css` — portable button + toast CSS

The 16-screen deck is Vantage (photo-to-CRM). Treat it as a **reference product**, not a template to clone blindly. Steal the state discipline.

## License

MIT. Use it. Fork it. Make your app look like someone sat with it.

If this saves you from another aurora-gradient login, that's the whole point.
