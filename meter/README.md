# Meter

An anime combat health and energy gauge. Taking damage flashes an impact frame with crystal shards and splashes; charging rumbles with **ゴゴゴゴ**.

## Run it

```sh
python3 -m http.server 8000     # from the repo folder
# open http://localhost:8000/meter/
```

## Use it

```html
<script src="meter.js"></script>
<sakuga-meter value="100" max="100" label="HP"></sakuga-meter>
```

```js
const meter = document.querySelector('sakuga-meter');
meter.damage(30);     // damage impact with shards & splash
meter.heal(25);       // rumble recharge with ゴゴゴゴ
meter.set(50);
```

| attribute | what it sets | default |
|---|---|---|
| `value` | current gauge value | `100` |
| `max` | maximum capacity | `100` |
| `label` | title displayed above gauge | `Power` |

- **CSS Variable:** `--sk-meter-width` (default: `320px`).
