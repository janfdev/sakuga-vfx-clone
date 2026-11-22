# Segmented

A multi-option dash switcher. Switching options streaks the indicator with a motion smear, brakes with dust puffs, and a sharp **シュッ** flies off.

## Run it

```sh
python3 -m http.server 8000     # from the repo folder
# open http://localhost:8000/segmented/
```

## Use it

List options inside it:

```html
<script src="segmented.js"></script>
<sakuga-segmented value="weekly" name="timeframe">
  <option value="daily">Daily</option>
  <option value="weekly">Weekly</option>
  <option value="monthly">Monthly</option>
</sakuga-segmented>
```

```js
const seg = document.querySelector('sakuga-segmented');
seg.addEventListener('change', () => console.log(seg.value));
seg.value = 'monthly';
```

| attribute | what it sets | default |
|---|---|---|
| `value` | active option value | first option |
| `disabled` | disables interaction | off |

- **Keyboard Accessible:** Arrow keys navigate between options with instant dash reaction.
- **Form-associated:** Works inside `<form>` elements and serializes with form data.
