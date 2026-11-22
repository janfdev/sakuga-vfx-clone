# Stepper

A step navigation control. Reaching a step shoots energy lines along the track, the node springs in with a shockwave ring and puff, and a hollow **ポン** pops up.

## Run it

```sh
python3 -m http.server 8000     # from the repo folder
# open http://localhost:8000/stepper/
```

## Use it

List the steps as `<option>`s inside it:

```html
<script src="stepper.js"></script>
<sakuga-stepper current="1" clickable>
  <option>Plan</option>
  <option>Build</option>
  <option>Test</option>
  <option>Ship</option>
</sakuga-stepper>
```

```js
el.next();        // advance to next step
el.prev();        // step backwards
el.goto(3);       // jump to step 3
console.log(el.current);
```

| attribute | what it sets | default |
|---|---|---|
| `current` | 1-based index of active step | 1 |
| `clickable` | allow user to click steps directly | off |
| `label` | accessible name for navigation | Steps |

- **CSS Variable:** `--sk-stepper-width` (default: `480px`).
