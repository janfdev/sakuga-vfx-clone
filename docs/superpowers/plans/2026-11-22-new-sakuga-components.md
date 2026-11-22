# Sakuga VFX: New Components Expansion Plan (Phases A, B, C)

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Expand the Sakuga VFX library with 9 new production-grade, anime-reactive components organized into 3 phased tiers: Form & Navigasi (A), Overlay & Feedback (B), and Gamified & Micro-elements (C), fully compliant with modern web accessibility (WCAG 2.2) and the Sakuga VFX core architecture.

**Architecture:** Each component is a self-contained custom element extending `SakugaFX.Base`, carrying its own embedded copy of `core.js` for zero-dependency standalone usage. Visual effects render to the shared global front-layer canvas or element back-layer, driven by the centralized physics clock (`Spring`, `advance(dt)`, `later(ms)`). All components support `--sk-*` CSS tokens, keyboard navigation, form association (where applicable), and automatic suppression for `prefers-reduced-motion`.

**Tech Stack:** Vanilla JavaScript (ES2022+), Web Components (Custom Elements v1, Shadow DOM, ElementInternals, Form-associated custom elements), HTML5 Canvas API, Native Dialog & Popover APIs, CSS Custom Properties.

**Spec & Design System:**
- Design Rules: Two tones and a line (`P.fill`, `P.shade`, `P.line`, `P.accent`), squash preserves volume, springs over easings, shrink/thinning exit over fade, clean minimal at rest.
- Sound-effect typography: Japanese onomatopoeia (`WORDS`: don, kachi, shu, pon, zuza, gogo).
- Accessibility: WAI-ARIA 1.2 / WCAG 2.2 compliant keyboard focus & screen-reader announcements, native semantic fallback.

## Global Constraints

- Zero external npm runtime dependencies; no bundler required for consumers.
- Each component file must be fully standalone (`public/sakuga-vfx/<component>.js`).
- Must maintain `// >>> sakuga core` ... `// <<< sakuga core` stamping compatibility with `tools/build.mjs`.
- Palette colors must use `--sk-*` CSS variables with `:where(:root)` zero-specificity fallback.
- Must honor `prefers-reduced-motion` (disable drawn effects while keeping state and spring transitions functional).
- Form value controls must implement `static formAssociated = true` with `ElementInternals`.
- Interactive elements must provide visible focus indicators (`:focus-visible`).

## Review Focus

1. **Keyboard-only usability:** Every interactive element must be fully operable via Tab, Space, Enter, Arrow keys, and Escape without trapping focus.
2. **Reduced Motion mode:** Verification under `prefers-reduced-motion: reduce` ensures full state functionality with zero visual canvas spam.
3. **Form submission & reset:** Form-associated controls (`select`, etc.) properly serialize in `new FormData(form)` and reset on `form.reset()`.
4. **Mobile & responsive reflow:** Tested down to 360px viewport width without horizontal scrollbars or clipping.
5. **Canvas coordinate syncing:** Floating effects (`at(el, fx, fy)`) align correctly across scroll, resize, and zoom scenarios.

---

## Phase 1: Opsi A — Form & Navigasi

### Task 1: `<sakuga-select>` (Custom Dropdown Select)

**Files:**
- Create: `select/select.js`
- Create: `select/index.html`
- Create: `select/README.md`
- Modify: `registry.json`
- Modify: `tools/build.mjs`
- Modify: `gallery/index.html`

- [ ] **Step 1: Scaffolding and Component Template**
  Create `select/` directory and structure `select.js` extending `fx.Base` with `formAssociated = true`, custom shadow DOM containing a combobox trigger button, display value slot, and popup listbox with `role="listbox"`.
- [ ] **Step 2: Implement Keyboard & Accessibility Contract**
  Implement combobox pattern (WAI-ARIA 1.2): `aria-haspopup="listbox"`, `aria-expanded`, `aria-activedescendant`. Support `ArrowUp`/`ArrowDown` navigation, `Enter`/`Space` to select, `Escape` to close, and typeahead search.
- [ ] **Step 3: Wire Anime Spring Reactions & VFX**
  - Trigger click: Squash spring (`squashy`).
  - Menu open: Spring-loaded downward unfolding.
  - Option hover/navigate: Crisp glint (`kira`) or subtle tick (`ticks`).
  - Selection hit: Light crescent slash (`slash`) + `sfx('kachi', x, y, hollow())`.
- [ ] **Step 4: Form Integration & Documentation**
  Wire `ElementInternals.setFormValue()` to selected value. Create `select/README.md` and standalone demo `select/index.html`.
- [ ] **Step 5: Stamping & Registry Integration**
  Add `'select'` to `NAMES` in `tools/build.mjs` and register entry in `registry.json`.

---

### Task 2: `<sakuga-accordion>` (Collapsible Panel)

**Files:**
- Create: `accordion/accordion.js`
- Create: `accordion/index.html`
- Create: `accordion/README.md`
- Modify: `registry.json`
- Modify: `tools/build.mjs`
- Modify: `gallery/index.html`

- [ ] **Step 1: Scaffolding and Semantic Structure**
  Create `accordion/` folder. Implement `<sakuga-accordion>` supporting multiple `<sakuga-accordion-item>` or nested `<details>`/`<summary>` semantically.
- [ ] **Step 2: Physics-based Unfurl & Height Transition**
  Use `Spring` to animate content container height from 0 to `scrollHeight`, preventing layout jank with `overflow: hidden` on panel wrapper.
- [ ] **Step 3: Anime Effects on Expand/Collapse**
  - Header click: Header squashes horizontally (`squashy`).
  - Expand impact: As panel slams open, emit hinge dust puff (`puff`) on left and right borders with **ズザッ** (*zuza*) sound-effect lettering.
  - Collapse: Sharp snap closed with subtle wobble marks (`wob`).
- [ ] **Step 4: Keyboard Navigation & Docs**
  Ensure headers are keyboard navigable via Tab, Enter, Space, and Arrow keys between headers. Create `accordion/README.md` and demo.
- [ ] **Step 5: Registry & Tooling Update**
  Add to `tools/build.mjs` and `registry.json`.

---

### Task 3: `<sakuga-stepper>` (Step Progress & Navigation)

**Files:**
- Create: `stepper/stepper.js`
- Create: `stepper/index.html`
- Create: `stepper/README.md`
- Modify: `registry.json`
- Modify: `tools/build.mjs`
- Modify: `gallery/index.html`

- [ ] **Step 1: Stepper Structure & Attributes**
  Create `<sakuga-stepper>` with attributes `steps` (count), `current` (active step 1-based), and label list. Expose `el.next()`, `el.prev()`, `el.goto(step)`.
- [ ] **Step 2: Step Transition Physics & Beam Effect**
  Connect circles with animated track line. Stepping forward charges an anime laser beam / line spurt (`lines`) along the connecting track.
- [ ] **Step 3: Footstep Landing Hit & SFX**
  When target step activates: step node bounces on spring (`Spring`), ejects circular shockwave ring (`ring`) and kicks up small dust puffs (`puff`), accompanied by hollow **ポン** (*pon*).
- [ ] **Step 4: Standalone Demo & Docs**
  Write `stepper/README.md` and standalone interactive test in `stepper/index.html`.
- [ ] **Step 5: Stamping & Registry**
  Add `'stepper'` to `build.mjs` and `registry.json`.

---

## Phase 2: Opsi B — Overlay & Feedback

### Task 4: `<sakuga-dialog>` (Anime Impact Modal)

**Files:**
- Create: `dialog/dialog.js`
- Create: `dialog/index.html`
- Create: `dialog/README.md`
- Modify: `registry.json`
- Modify: `tools/build.mjs`
- Modify: `gallery/index.html`

- [ ] **Step 1: Native `<dialog>` Core Architecture**
  Wrap native HTML `<dialog>` with `showModal()` and `close()`. Manage focus trapping, backdrop styling (`::backdrop` with light lavender tint and dim ink), and Escape key dismissal.
- [ ] **Step 2: Slam-Down Entrance Physics**
  Animate modal position using a heavy vertical spring (`Spring(y, k=380, d=18)`), starting above viewport and slamming into center with dramatic overshoot.
- [ ] **Step 3: Impact VFX & Sound-Effect Lettering**
  - Impact moment: Bottom corners kick out paired dust clouds (`puff`), floor shockwave ring (`ring`), and screen-shake wobble marks (`wob`).
  - Text: Dramatic centered **ドン!** (*don*) appears right above the modal header.
  - Close animation: Modal cuts diagonally or shrinks rapidly into a point (`kira`).
- [ ] **Step 4: Accessibility & Standalone Demo**
  Verify focus restoration to opener button, `aria-labelledby`, and `aria-describedby`. Add `dialog/README.md` and demo.
- [ ] **Step 5: Stamping & Registry**
  Add `'dialog'` to `build.mjs` and `registry.json`.

---

### Task 5: `<sakuga-drawer>` (Slide-over Sheet)

**Files:**
- Create: `drawer/drawer.js`
- Create: `drawer/index.html`
- Create: `drawer/README.md`
- Modify: `registry.json`
- Modify: `tools/build.mjs`
- Modify: `gallery/index.html`

- [ ] **Step 1: Drawer Architecture (Right/Bottom/Left Sides)**
  Implement `<sakuga-drawer side="right|bottom|left">` with modal overlay, dismissible backdrop, and drag-to-dismiss gesture support.
- [ ] **Step 2: Smear Entrance & Edge Slam**
  Drawer streaks in with high-velocity spring. Emits speed lines (`lines`) parallel to the entry edge.
- [ ] **Step 3: Brake Settle & SFX**
  When slamming against the edge, brake sparks/shards (`shards`) and wobble lines (`wob`) pop out, accompanied by **シュッ** (*shu*) or **ズザッ** (*zuza*).
- [ ] **Step 4: Demo, Docs & Registry**
  Create docs, demo, and register in `build.mjs` and `registry.json`.

---

### Task 6: `<sakuga-popconfirm>` (Speech-bubble Confirmation)

**Files:**
- Create: `popconfirm/popconfirm.js`
- Create: `popconfirm/index.html`
- Create: `popconfirm/README.md`
- Modify: `registry.json`
- Modify: `tools/build.mjs`
- Modify: `gallery/index.html`

- [ ] **Step 1: Popover Anchoring Architecture**
  Implement floating confirmation bubble that anchors next to trigger buttons (using Modern Web CSS Anchor Positioning or fallback bounding rect).
- [ ] **Step 2: Manga Speech Bubble Appearance**
  Bubble pops open with jagged anime speech bubble styling and accent wedges (`ticks`) pointing from target.
- [ ] **Step 3: Action Buttons & Sound-Effect**
  Confirm / Cancel buttons with mini-squash; confirm plays crisp **カチッ** (*kachi*) and dispatches `confirm` event.
- [ ] **Step 4: Docs & Registry**
  Complete documentation and registry entry.

---

## Phase 3: Opsi C — Gamified & Micro-elements

### Task 7: `<sakuga-badge>` (Animated / Dismissible Tag)

**Files:**
- Create: `badge/badge.js`
- Create: `badge/index.html`
- Create: `badge/README.md`
- Modify: `registry.json`
- Modify: `tools/build.mjs`
- Modify: `gallery/index.html`

- [ ] **Step 1: Badge Structure (Count & Tag variants)**
  Create `<sakuga-badge count="5" max="99" dismissible>` supporting numeric pill mode or text tag mode with optional close button.
- [ ] **Step 2: Numeric Change Spring & Pop**
  Incrementing count causes badge to bounce with squash & overshoot (`Spring`), throwing sparkle glints (`kira`) and sound-effect **ポン** (*pon*).
- [ ] **Step 3: Slice-and-Shard Dismissal**
  Clicking dismiss button slashes the badge into two falling halves with crystal chips (`shards`) and leaves the DOM cleanly.
- [ ] **Step 4: Docs & Registry**
  Complete documentation, demo, and registry wiring.

---

### Task 8: `<sakuga-counter>` (Combo / Milestone Stat Counter)

**Files:**
- Create: `counter/counter.js`
- Create: `counter/index.html`
- Create: `counter/README.md`
- Modify: `registry.json`
- Modify: `tools/build.mjs`
- Modify: `gallery/index.html`

- [ ] **Step 1: Counter Structure & Odometer Roll**
  Implement `<sakuga-counter value="0" label="Combo">` with digit roll animation driven by `Spring`.
- [ ] **Step 2: Combo Milestone Burst Thresholds**
  Every 10 counts kicks up dust (`puff`); milestone counts (e.g., 50, 100) trigger speed lines (`lines`), star burst (`burst`), and **ドン!** (*don*).
- [ ] **Step 3: Accessibility Live Region**
  Include visually hidden polite `aria-live` announcement for assistive technology.
- [ ] **Step 4: Docs & Registry**
  Write README, demo, and integrate with build tools.

---

### Task 9: `<sakuga-card>` (Interactive Anime Focus Card)

**Files:**
- Create: `card/card.js`
- Create: `card/index.html`
- Create: `card/README.md`
- Modify: `registry.json`
- Modify: `tools/build.mjs`
- Modify: `gallery/index.html`

- [ ] **Step 1: Card Container & Comic Shading**
  Create `<sakuga-card>` with comic offset shadow (`--sk-sh`), bold ink border, and optional header/action slots.
- [ ] **Step 2: Pointer Hover Tilt & Speed Accent**
  Pointer movement creates subtle spring tilt; rapid hover or click emits corner speed lines (`lines`) and impact star behind card.
- [ ] **Step 3: Focus & Keyboard Accessibility**
  Cards functioning as links or buttons receive proper ARIA roles and tab indexing.
- [ ] **Step 4: Docs & Registry**
  Add documentation, demo, and registry update.

---

## Phase 4: Final Gallery Showcase & Verification

### Task 10: Gallery Refresh & E2E Validation

**Files:**
- Modify: `gallery/index.html`
- Modify: `README.md`
- Modify: `llms.txt`
- Modify: `tools/build.mjs`
- Test: `tools/test.mjs`

- [ ] **Step 1: Stamping All Components**
  Run `node tools/build.mjs` to ensure all 9 new components contain the exact stamped core and metadata.
- [ ] **Step 2: Gallery Showcase Cards**
  Add interactive showcase cards for all 9 components into `gallery/index.html` with real-time feedback, install commands, and copyable prompts for AI agents.
- [ ] **Step 3: Documentation & LLM Catalog Update**
  Update `README.md` and `llms.txt` with the expanded list of 20 components.
- [ ] **Step 4: Browser & Interaction Test Verification**
  Run automated tests with `node tools/test.mjs` to verify touch, keyboard, and form validity across all components.
