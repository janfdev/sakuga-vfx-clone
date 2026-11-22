# Accordion

A collapsible panel group. Headers squash on click, panels expand with a snappy spring, dust puffs roll from the hinges, and **ズザッ** lands in dotted letters.

## Run it

```sh
python3 -m http.server 8000     # from the repo folder
# open http://localhost:8000/accordion/
```

## Use it

List sections with `data-title` inside it:

```html
<script src="accordion.js"></script>
<sakuga-accordion exclusive>
  <div data-title="Sakuga Overview" data-open>
    Ordinary UI controls that react with anime sakuga impact frames, springs, and hand-drawn manga effects.
  </div>
  <div data-title="Zero Dependencies">
    Drop-in custom elements with self-contained runtime, no bundlers or third-party dependencies required.
  </div>
</sakuga-accordion>
```

| attribute | what it sets | default |
|---|---|---|
| `exclusive` | only one panel open at a time | off (multi-open allowed) |

- **Panel attributes:** Put `data-open` on any child element to have it open initially.
- **Accessible keyboard support:** Tab between headers, Enter or Space to toggle panels.
- **CSS Variable:** `--sk-accordion-width` (default: `540px`).
