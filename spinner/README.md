# Spinner

An anime ki vortex and charging aura spinner. Rings spin with fluctuating speed, periodically throwing energy shockwave rings and sparkles.

## Run it

```sh
python3 -m http.server 8000     # from the repo folder
# open http://localhost:8000/spinner/
```

## Use it

```html
<script src="spinner.js"></script>
<sakuga-spinner size="60"></sakuga-spinner>
<sakuga-spinner size="60" charging label="Charging Ki"></sakuga-spinner>
```

```js
const spinner = document.querySelector('sakuga-spinner');
spinner.done();      // finishes with burst & カチッ
```

| attribute | what it sets | default |
|---|---|---|
| `size` | diameter in pixels | `52` |
| `charging` | rapid rotation with shockwave rings | off |
| `label` | accessible aria-label | `Loading` |
