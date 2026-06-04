# The Anatomy of Failure

> How a single human assumption becomes a hidden fault — and how a hidden fault becomes a rocket that explodes, an airline that grounds, a patient who dies.

A self-contained, animated keynote presentation for a **Professional Practices** course on computer errors, faults, failures, and incidents. Built as a single HTML file with zero dependencies — it runs fully **offline** in any modern browser, so it won't break in a classroom with no internet.

**Core thesis:** computer failures are rarely single random events. They are **chains** — a human mistake, a design assumption, a hidden fault, a weak process, or a missing safeguard propagates until it becomes a visible failure and real-world harm. Professional practice is about **breaking that chain** before users pay the price.

---

## Quick start

No build step, no install. Just open the file:

```text
index.html
```

- **Double-click** it, or drag it into Chrome / Edge / Firefox.
- Press **`F`** for fullscreen and present.

That's it. Everything (engine, styling, animations, and the six case-study diagrams) is inlined in the one file.

**On a phone?** The deck is responsive. Open the same file — or a hosted URL (e.g. GitHub Pages, which is why it's named `index.html`) — on mobile: layouts stack into a single column, each slide scrolls, all build-steps are shown, and tap / swipe moves between slides. The desktop view is unchanged.

---

## Presenting it

| Key | Action |
| --- | --- |
| `→` &nbsp;·&nbsp; `Space` &nbsp;·&nbsp; click | Next reveal / next slide |
| `←` | Back |
| `Home` / `End` | First / last slide |
| `F` | Toggle fullscreen |
| **`N`** | **Speaker notes** — talking points + a timing cue for every slide |
| `O` | Slide overview grid (click any slide to jump) |
| `1`–`9` | Jump to slide *n* |
| `?` | Keyboard help overlay |

Slides also support **swipe** on touch screens, and you can deep-link to a slide with a URL hash (e.g. `…presentation.html#15`).

The talk is paced for **~8–10 minutes**. Slides 1–26 are the core; slides 27–29 are **backup slides for Q&A**. Press `N` during practice — each slide carries its own notes and a target time.

---

## Features

- **100% offline & self-contained** — one HTML file, no CDN, no fonts to download, no JavaScript libraries.
- **Custom presentation engine** — keyboard / click / swipe navigation, fragment reveals, progress bar, slide counter, overview mode, and a help overlay.
- **Dark "keynote" design** — animated ambient background, neon accent palette, large typography that scales to a projector via `clamp()`/`vmin`.
- **Six bespoke animated SVG diagrams** — each *visualises the actual error mechanism* (see below). They animate on slide entry and replay when you navigate back.
- **Built-in speaker notes** (`N`) with per-slide timing cues.
- **Accessibility-aware** — honours `prefers-reduced-motion` to dampen animation for sensitive viewers.
- **Responsive** — a mobile layer (≤ 820px) stacks every layout, makes slides scrollable, turns the chain diagram vertical, and reveals all build-steps for reading on a phone — all scoped to media queries, so the desktop view is byte-for-byte unchanged.

---

## Deck structure

| # | Slide | Purpose |
| --- | --- | --- |
| 1 | Title | Hook + the 30-years-to-the-day Ariane anniversary |
| 2 | The view from outside | Failure looks sudden… |
| 3 | Thesis | …but it's a chain |
| 4 | Definitions | Mistake → fault → error → failure → incident |
| 5 | The chain | Animated hero diagram of propagation |
| 6 | Internal vs visible | Vocabulary punchline |
| 7 | Why it matters | Safety, money, trust, society, duty (+ the $2.41T stat) |
| 8 | Reliability redefined | Reliability = containment, not zero bugs |
| 9–12 | Taxonomy | By source, duration, and behaviour |
| 13 | Case studies divider | Four failures, one pattern |
| 14–19 | **Case studies** | BSOD · Ariane 5 · Mars Orbiter · CrowdStrike · Therac-25 · Knight Capital |
| 20 | The pattern | What all the cases share |
| 21–24 | Prevention | Defense-in-depth · blameless postmortems · ACM ethics |
| 25 | Closing | "Remember the chain." |
| 26 | References | Sources |
| 27–29 | **Backup (Q&A)** | Six more famous failures + "redundancy done right" |

---

## Case studies & their diagrams

Each case maps to the same fault→failure chain and ships with a custom animated illustration of *how* it failed:

| Case | What failed | The diagram shows |
| --- | --- | --- |
| **Blue Screen of Death** | Kernel-level fail-stop | A stop screen turning blue with a protective "shield" — a deliberate halt, not a random crash |
| **Ariane 5 Flight 501** (1996) | 64-bit float cast to a 16-bit signed int → overflow | A register filling cell-by-cell and **overflowing past 32 767**, then the rocket exploding |
| **Mars Climate Orbiter** (1999) | `lbf·s` vs `N·s` unit mismatch | Two trajectories diverging — a safe ≈226 km arc vs an actual ≈57 km arc that clips the atmosphere |
| **CrowdStrike** (2024) | Out-of-bounds read in a kernel content update | A pointer marching across memory cells 0–19 and stepping into a **21st "out of bounds" cell** |
| **Therac-25** (1985–87) | Race condition + removed hardware interlocks | The safety target sliding out of the beam path as the dose gauge spikes ≈200 → ≈25 000 rad |
| **Knight Capital** (2012) | Dormant code on one un-updated server | 7 servers green, the **8th red**, an order cascade, and the P&L plunging to −$460M |

Backup slides add **Pentium FDIV, the AT&T 1990 collapse, the 2003 Northeast Blackout, Boeing 737 MAX, Y2K, and Heartbleed**, plus a "redundancy done right" counterpoint (dissimilar / N-version redundancy).

---

## Accuracy & sources

Every figure on the slides was fact-checked against primary or authoritative sources before publishing. Key references:

- Avizienis, Laprie, Randell & Landwehr — *Basic Concepts and Taxonomy of Dependable and Secure Computing* (IEEE TDSC, 2004)
- Microsoft Learn — *Bug Checks (Stop Code Errors)*
- ESA / CNES — *Ariane 501 Inquiry Board Report* (1996)
- NASA — *Mars Climate Orbiter* Mishap Investigation Board report (1999)
- CrowdStrike — *Falcon Content Update Post-Incident Review / RCA* (2024); Microsoft outage statement
- Leveson & Turner — *An Investigation of the Therac-25 Accidents* (IEEE Computer, 1993)
- U.S. SEC — *Knight Capital* Market Access Rule order, Release 2013-222
- Google SRE — *Postmortem Culture: Learning from Failure*
- ACM — *Code of Ethics and Professional Conduct* (2018)
- James Reason — *Human error: models and management* (BMJ, 2000) — the Swiss-cheese model
- Lamport, Shostak & Pease — *The Byzantine Generals Problem* (ACM TOPLAS, 1982)
- CISQ — *The Cost of Poor Software Quality in the US: A 2022 Report*

A few honesty notes baked into the deck: the Ariane `$370M` figure is press-sourced (not the ESA report); "incident" is an operational/ITIL extension of the fault→error→failure model, not part of the 2004 taxonomy; and the CrowdStrike defect is framed precisely as *"a rule read a 21st field when only 20 were supplied."*

---

## Customizing

It's plain HTML/CSS/JS — open it in any editor.

- **Colours / theme:** edit the CSS custom properties in `:root` (top of the `<style>` block) — `--cyan`, `--amber`, `--red`, `--bg-0`, etc. *(Note: the SVG diagrams use hard-coded hex values rather than `var()`, because CSS variables aren't reliably substituted inside SVG presentation attributes — change those inline if you re-theme.)*
- **Content:** each slide is a `<section class="slide">`. Add `class="fragment"` to anything you want to reveal on click. Add `data-notes="…"` and `data-timing="…"` for speaker notes.
- **Scale / sizing:** `.wrap { max-width }`, `.slide { padding }`, and the `.case` grid columns control how large the content and diagrams render on a projector.
- **Add a slide:** drop in a new `<section class="slide">…</section>`; the engine counts slides automatically — no config to update.

---

## How it works

- A small vanilla-JS engine (bottom of the file) tracks the current slide and fragment index, toggles an `.active` class, and drives all transitions via CSS.
- Diagram animations are pure CSS `@keyframes` scoped under `.slide.active …`, so they restart each time a slide becomes active.
- No framework, no bundler, no network requests at runtime.

**Browser support:** any current Chromium (Chrome/Edge), Firefox, or Safari. Best presented fullscreen (`F`).

---

## Repository

```text
software-ethics/
├── index.html   # the entire deck (open this)
└── README.md
```

---

## License & use

Created as coursework for a Professional Practices module. The slide content draws on publicly reported incidents; please keep the source attributions if you reuse or adapt it. Free to use for educational purposes.

*Author: add your name / student ID here.*
