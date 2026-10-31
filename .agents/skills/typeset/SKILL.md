---
name: typeset
description: Applies mathematical and optical digital typography, non-cliche font pairings, W3C text-box trimming, fluid clamp() derivations, dark-mode grade compensation, and zero-CLS metrics. Use whenever selecting fonts, styling UI or brand surfaces, configuring CSS/Tailwind/Next.js typography, or calibrating visual hierarchy.
---

# Typeset

Mathematical and optical typography for digital interfaces, high-density technical substrates, and bespoke brand surfaces.

## 1. Non-Lossy Mathematical Laws (System-2 Engine)

Do NOT guess tracking, leading, or fluid scales, and NEVER default to cliché template fonts (`Inter`, `Roboto`, `Open Sans`, `Montserrat`, `Lato`, `Arial`) or OS-locked non-web fonts (`SF Pro`). Compute typography deterministically using these five physical invariants:

### Law 1 — Surface Allocation ($85 / 15$ Entropy Split)
$$\text{Area}(\text{Core} \cup \text{Substrate}) \ge 0.85, \qquad \text{Area}(\text{Signature}) \le 0.15$$
- **85% Functional Surface (`Core Type` + `Substrate Type`):** Navigation, controls, body text, tables, and code require open apertures, tall $x$-height ($x_h \ge 0.52$), and zero ornamental distraction.
- **15% Visceral Surface (`Signature Type`):** Hero titles, section headers, pull quotes, and inline italic voice shifts carry sculptural contrast and calligraphic memory.

### Law 2 — Logarithmic Optical Tracking $\tau(s)$
For any nominal font size $s$ (in `px`), letter-spacing must scale inversely with the natural logarithm of size relative to $16\text{px}$:
$$\tau(s) = \text{clamp}\!\left(-0.045\text{em},\; -0.022 \cdot \ln\!\left(\frac{s}{16}\right)\text{em},\; +0.025\text{em}\right)$$
- **Micro UI ($11\text{px}\text{–}13\text{px}$):** Add $+0.01\text{em}$ to $\tau(s)$ ($\approx +0.015\text{em}\text{ to }+0.025\text{em}$); add $+0.06\text{em}$ if `UPPERCASE`.
- **Reading Body ($15\text{px}\text{–}18\text{px}$):** $\tau(s) \approx 0\text{em}$ (never apply negative tracking below $18\text{px}$).
- **Display ($48\text{px}\text{–}96\text{px}$):** $\tau(s) \approx -0.024\text{em}\text{ to }-0.040\text{em}$.

### Law 3 — Hyperbolic Leading & Measure $\lambda(s, M)$
For font size $s$ (`px`) and line measure $M$ (in `ch`, constrained to $45\text{ch} \le M \le 70\text{ch}$ for prose):
$$\lambda(s, M) = 1.02 + \frac{8.5}{s} + 0.003 \cdot \max(0,\; M - 55)$$
- Yields $\approx 1.56\text{–}1.62$ for reading copy, $\approx 1.30$ for subheads, and $\approx 1.06\text{–}1.14$ for display headers.

### Law 4 — Harmonic Fluid Scale $S(n, v)$
For scale step $n \in \{-2, -1, 0, 1, 2, 3, 4\}$, base $S_0 = 1\text{rem}$, mobile ratio $r_{\min} = 1.15$ at $V_{\min} = 22.5\text{rem}$ ($360\text{px}$), and desktop ratio $r_{\max} = 1.28$ at $V_{\max} = 90\text{rem}$ ($1440\text{px}$):
$$S_{\min}(n) = S_0 \cdot r_{\min}^{\,n}, \quad S_{\max}(n) = S_0 \cdot r_{\max}^{\,n}, \quad m(n) = \frac{S_{\max}(n) - S_{\min}(n)}{V_{\max} - V_{\min}}, \quad b(n) = S_{\min}(n) - m(n)V_{\min}$$
$$\text{font-size}(n) = \texttt{clamp}\!\left(S_{\min}(n)\text{rem},\; b(n)\text{rem} + 100m(n)\text{vw},\; S_{\max}(n)\text{rem}\right)$$

### Law 5 — Optical $x$-Height Normalization & `TrueGrade` Polarity
- **$x$-Height Invariant (`Optical Voice Shift`):** When mixing a secondary font (e.g., an inline italic serif with $x$-height ratio $x_2$) inside a primary font ($x_1$), equalize perceived size via `font-size-adjust: ex-height from-font;` or $S_2 = S_1 \cdot (x_1 / x_2)$ ($\approx 1.06\text{em}$).
- **Luminance Polarity (`TrueGrade`):** For background polarity $P \in \{0\text{ (light)},\; 1\text{ (dark)}\}$, counter OLED halation without layout shift via:
  $$\text{GRAD}(P) = -25 \cdot P \quad \text{or weight offset } \Delta w(P) = -35 \cdot P$$

---

## 2. System-1 Fast Path: De-Clichéd Trilogy Presets

When no brand typeface is pre-mandated, select one of these legally embeddable, high-craft presets:

| Preset | 85% `Core Type` (UI & Body) | 15% `Signature Type` (Display & Voice Shift) | `Substrate Type` (Code, Data & Long Reading) |
| :--- | :--- | :--- | :--- |
| **Preset A: Architectural Precision** *(Open-Source / Modern Web & AI)* | **Aspekta** or **Switzer** *(or **Schibsted Grotesk**)* | **Instrument Serif** or **Newsreader** (`opsz` 36–72) | **Monaspace Neon** or **Commit Mono** |
| **Preset B: Humanist Craft** *(Open-Source / Product & Editorial)* | **General Sans** or **Satoshi** *(or **Uncut Sans**)* | **Sentient** or **Fraunces** (`SOFT` 0, `WONK` 1) | **Literata** (Reading) + **Lilex** (Code) |
| **Preset C: Independent Foundry** *(Commercial License Tier)* | **Roobert**, **ABC Diatype**, or **Söhne** | **GT Alpina**, **Signifier**, or **PP Editorial Old** | **GT Alpina Typewriter** or **Intel One Mono** |

---

## 3. Modern CSS & OpenType Invariants
1. **Box Trim (`Metric Trim`):** On buttons, badges, pills, and grid-aligned headers, apply `text-box: trim-both cap alphabetic;` so vertical padding is mathematically symmetrical around cap-height and baseline.
2. **Tabular Data:** On all numbers, prices, counters, timers, and tables, enforce `font-variant-numeric: tabular-nums slashed-zero;` (`"tnum" 1, "zero" 1`).
3. **Optical Sizing & Disambiguation:** Always set `font-optical-sizing: auto;` and disambiguate `I/l/1` (`"cv05" 1, "cv08" 1, "ss01" 1`).
4. **Headline Wrapping:** Apply `text-wrap: balance;` on `h1–h3` and `text-wrap: pretty;` on reading paragraphs (`max-width: 65ch`).
5. **Deep Reference:** Read `resources/reference.md` whenever you need the full curated typeface catalog, evergreen foundry discovery vectors, ready-to-drop CSS/Tailwind v4/Next.js code blocks, or live DOM verification snippets.
