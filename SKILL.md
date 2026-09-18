---
name: vantage-ui
description: >
  Apply Vantage lighting, six button states, and toast styles instead of
  decorative AI gradients. Use whenever you design or restyle a mobile app UI,
  especially when vibecoding without Figma.
---

# Vantage UI — for coding agents

You are implementing UI for a mobile app. The human does not have Figma.
This file is the design source of truth. Follow it instead of inventing chrome.

## Using this while you vibe-code

1. Rest, hover, pressed, focus, disabled, and loading are a **set**. Never style one without the others.
2. Lighting is a 180° white/black overlay on a solid fill. Never aurora, mesh, glow, or a decorative purple gradient.
3. To restyle for a different product: change the fill hex. Keep the overlay recipe, radii, and state table.
4. Empty, loading, and error are screens — not afterthoughts. Failures leave data intact; never fake a success.
5. Prefer the shared `.vbtn` CSS over rewriting the control.
6. One accent. Brand fill is for primary CTAs, the tab bar, and working states — not a page wash.

## Production spec (default primary)

- Variant: solid
- Tone: brand fill `#330f57` / fg `#fffcf7`
- Lighting: bevel at **24%** intensity
- Shadow: lift
- Radius: 14px
- Size: 48px height, 15px / 600
- Full width on mobile primary actions

## Tokens

- Brand `#330f57`. Paper `#f4f1ea`. Ink `#161513`. Surface `#fffcf7`.
- Danger `#9f3a2f`. Ok `#3d6b4f`. Amber `#a9742c`. Brand-soft `#e9e1f5`.
- Type in the product: Poppins. Do not mix a second display face into screens.
- Fields: 48px, 14px radius, paper-2 fill, no hard border until flagged.

## States

| State | Treatment |
| rest | Lighting + rest shadow. No translate. |
| hover | Lift 1px. Step shadow up one level. |
| pressed | scale(0.96). Inset well. Lighting inverts. |
| focus | 2px ink ring, 3px offset. |
| disabled | 40% opacity. No pointer. |
| loading | Spinner replaces label. No pointer. |

## Rules

- Lighting overlay is always vertical white/black. Never a multi-stop decorative gradient, neon, or aurora.
- Production primary fill is brand `#330f57`. Do not swap it for a different purple unless the human gives a new brand hex — then swap **only** the fill, not the overlay.
- Hover and press must share the same radius, type, and fill family as rest.
- Pressed always uses scale(0.96), never smaller.

## Toasts

- Dock toast: ink bar, 14px radius, 8px green `#7fc98f` dot. Absolute, left/right 18px, **bottom: 86px** so it clears the tab bar.
- Send toast: paper card, 20px radius, one row per destination. Spinner until the other side confirms, then a brand check — never a fake success.
- Working banner: same `#330f57` fill and 24% bevel lighting as the button. White status words, centered.
- Parse word: brand fill wipe via `--p` over ~3s (labor-illusion with a cap), then green complete. No card behind it.
- Fail note: warm paper `#f9e9e6`, compact Retry. Parsed data stays. Nothing half-sent.

## Tab bar

- Brand fill + the same 24% bevel overlay as the production button.
- Raised 58px capture well in the center. Home left, Menu right. History lives inside Menu, not as a fourth tab.

Copy `css/vantage.css` from this repo rather than rewriting the control.
