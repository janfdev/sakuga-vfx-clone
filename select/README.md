# Select

A dropdown select menu. The trigger squashes on click, the menu unfolds downward on a spring, and picking an item triggers an anime slice with **カチッ**.

## Run it

```sh
python3 -m http.server 8000     # from the repo folder
# open http://localhost:8000/select/
```

## Use it

List the choices as `<option>`s inside it:

```html
<script src="select.js"></script>
<sakuga-select label="Hero" name="hero" placeholder="Choose your hero">
  <option value="deku" selected>Izuku Midoriya</option>
  <option value="bakugo">Katsuki Bakugo</option>
  <option value="todoroki">Shoto Todoroki</option>
</sakuga-select>
```

```js
el.addEventListener('change', () => console.log(el.value));
el.value = 'bakugo';     // set from code
```

| attribute | what it sets | default |
|---|---|---|
| `label` | what a screen reader calls the select | Select |
| `placeholder` | hint when no option is picked | Select an option |
| `value` | selected option value | selected option or empty |
| `name` | sent with its form | none |
| `disabled` | disables the select | off |

- **Keyboard navigation:** Tab to focus, Space/Enter/ArrowDown/ArrowUp to open, Arrow keys to navigate options, Space/Enter to select, Escape to close.
- **Form-associated:** Works inside `<form>` elements and appears in `new FormData(form)`.
- **CSS Variable:** `--sk-select-width` (default: `230px`).
