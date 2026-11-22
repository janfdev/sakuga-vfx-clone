# Card

An anime comic panel card. Interactive mode responds with spring tilt, corner speed lines, and a crisp **カチッ** on click.

## Run it

```sh
python3 -m http.server 8000     # from the repo folder
# open http://localhost:8000/card/
```

## Use it

```html
<script src="card.js"></script>
<sakuga-card interactive>
  <h2>UA High Hero Course</h2>
  <p>Training tomorrow's greatest champions with passion and grit.</p>
</sakuga-card>
```

| attribute | what it sets | default |
|---|---|---|
| `interactive` | enables spring tilt, hover speed lines, and click reactions | off |

- **Keyboard Accessible:** When `interactive` is present, the card is focusable via Tab and triggers with Enter or Space.
- **CSS Variable:** `--sk-card-width` (default: `360px`).
