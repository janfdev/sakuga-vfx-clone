# Dialog

An anime impact modal dialog. It slams down from above on a spring, dust puffs roll from the base, a shockwave ring expands, and a massive **ドン!** lands overhead.

## Run it

```sh
python3 -m http.server 8000     # from the repo folder
# open http://localhost:8000/dialog/
```

## Use it

```html
<script src="dialog.js"></script>
<sakuga-dialog id="modal">
  <h2>Mission Briefing</h2>
  <p>Prepare for the upcoming raid on the villain hideout!</p>
  <button type="button" data-close>Acknowledge</button>
</sakuga-dialog>
```

```js
const modal = document.getElementById('modal');
modal.showModal();   // opens with slam animation
modal.close();       // closes with shrink slice
```

- **Built on native `<dialog>`:** Native focus trapping, `::backdrop`, and Escape key to close.
- **Auto-close trigger:** Any element inside with `data-close` attribute closes the dialog when clicked.
- **CSS Variable:** `--sk-dialog-width` (default: `460px`).
