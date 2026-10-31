# Typeset

*Mathematical & optical typography for Humans and AI Agents.*

**[Live Interactive Specimen & Presentation](https://chama-x.github.io/typeset/)**

`typeset` encodes non-lossy mathematical laws, W3C CSS Level 3/4/5 invariants, and de-clichéd type curation directly into an AI agent skill for Google Antigravity and universal agent runners. It eliminates typographic guesswork, default template fatigue (`Inter`, `Roboto`, `Open Sans`), and OS font fragmentation.

---

## The 5 Mathematical Laws

### Law 1: Surface Allocation ($85 / 15$ Entropy Split)
$$\text{Area}(\text{Core} \cup \text{Substrate}) \ge 0.85, \qquad \text{Area}(\text{Signature}) \le 0.15$$
- **85% Functional Surface (`Core Type` + `Substrate Type`):** Open apertures, tall $x$-height ($x_h \ge 0.52$), and zero ornamental distraction across navigation, controls, body copy, tables, and code.
- **15% Visceral Surface (`Signature Type`):** Sculptural contrast, calligraphic memory, and deliberate voice shifts reserved for hero headlines, pull quotes, and editorial accents.

### Law 2: Logarithmic Optical Tracking $\tau(s)$
Letter-spacing scales inversely with the natural logarithm of font size relative to $16\text{px}$:
$$\tau(s) = \text{clamp}\!\left(-0.045\text{em},\; -0.022 \cdot \ln\!\left(\frac{s}{16}\right)\text{em},\; +0.025\text{em}\right)$$
- **Micro UI ($11\text{px}\text{–}13\text{px}$):** $+0.015\text{em}\text{ to }+0.025\text{em}$ ($+0.06\text{em}$ for uppercase).
- **Body Text ($15\text{px}\text{–}18\text{px}$):** $\approx 0\text{em}$ (never apply negative tracking below $18\text{px}$).
- **Display Headlines ($48\text{px}\text{–}96\text{px}$):** $-0.024\text{em}\text{ to }-0.040\text{em}$.

### Law 3: Hyperbolic Leading & Measure $\lambda(s, M)$
For font size $s$ (`px`) and measure $M$ (`ch`, $45\text{ch} \le M \le 70\text{ch}$):
$$\lambda(s, M) = 1.02 + \frac{8.5}{s} + 0.003 \cdot \max(0,\; M - 55)$$
- Delivers $\approx 1.56\text{–}1.62$ for reading prose, $\approx 1.30$ for subheads, and $\approx 1.06\text{–}1.14$ for large display headers.

### Law 4: Harmonic Fluid Scale $S(n, v)$
Linear interpolation across viewport boundaries ($V_{\min} = 22.5\text{rem} / 360\text{px}$, $V_{\max} = 90\text{rem} / 1440\text{px}$) with ratios $r_{\min} = 1.15$ and $r_{\max} = 1.28$:
$$S_{\min}(n) = S_0 \cdot r_{\min}^{\,n}, \quad S_{\max}(n) = S_0 \cdot r_{\max}^{\,n}, \quad m(n) = \frac{S_{\max}(n) - S_{\min}(n)}{V_{\max} - V_{\min}}, \quad b(n) = S_{\min}(n) - m(n)V_{\min}$$
$$\text{font-size}(n) = \texttt{clamp}\!\left(S_{\min}(n)\text{rem},\; b(n)\text{rem} + 100m(n)\text{vw},\; S_{\max}(n)\text{rem}\right)$$

### Law 5: $x$-Height Normalization & Luminance Polarity (`TrueGrade`)
- **$x$-Height Invariant:** Equalize optical scale when combining fonts using `font-size-adjust: ex-height from-font;` or $S_2 = S_1 \cdot (x_1 / x_2)$ ($\approx 1.06\text{em}$).
- **Luminance Polarity (`TrueGrade`):** Eliminate OLED dark-mode halation without layout shift reflow:
  $$\text{GRAD}(P) = -25 \cdot P \quad \text{or weight offset } \Delta w(P) = -35 \cdot P \quad (P \in \{0, 1\})$$

---

## Modern W3C CSS Invariants

- **W3C Metric Box Trim:** `text-box: trim-both cap alphabetic;` strips leading half-leading on buttons, badges, pills, and grid titles for exact vertical symmetry.
- **Dynamic Optical Sizing:** `font-optical-sizing: auto;` coordinates physical stroke weight with viewport size.
- **Glyph Disambiguation & Tabular Metrics:** `font-variant-numeric: tabular-nums slashed-zero;` and `"cv05" 1, "cv08" 1, "ss01" 1` for unambiguous `I/l/1` differentiation and aligned financial tables.
- **Editorial Line Wrapping:** `text-wrap: balance;` on headings and `text-wrap: pretty;` on reading copy ($M \le 65\text{ch}$).

---

## Installation

### Option 1: Universal Skills CLI (Agent Marketplace)
Install directly into your agent runner:
```bash
npx skills add chama-x/typeset -a antigravity
```

### Option 2: Global Setup for Google Antigravity
Clone and symlink into Google Antigravity's global skill directories for live Git synchronization:

```bash
# Clone repository
git clone https://github.com/chama-x/typeset.git ~/projects/typeset
cd ~/projects/typeset

# Symlink into Antigravity global skill roots
mkdir -p ~/.gemini/antigravity/skills ~/.gemini/config/skills ~/.agents/skills
ln -sfn "$(pwd)/.agents/skills/typeset" ~/.gemini/antigravity/skills/typeset
ln -sfn "$(pwd)/.agents/skills/typeset" ~/.gemini/config/skills/typeset
ln -sfn "$(pwd)/.agents/skills/typeset" ~/.agents/skills/typeset
```

---

## Architecture & File Layout

```text
typeset/
├── README.md                                 # Architecture, mathematical laws & quickstart
└── .agents/
    └── skills/
        └── typeset/
            ├── SKILL.md                      # System-1 presets & System-2 mathematical invariants
            └── resources/
                └── reference.md              # Curated catalog, CSS tokens, zero-CLS locks & DOM audit
```

## License

MIT
