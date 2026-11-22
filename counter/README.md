# Counter

A combo or milestone stat counter. Digits roll on a spring; hitting milestones triggers speed lines, an impact burst, and a massive **ドン!**.

## Run it

```sh
python3 -m http.server 8000     # from the repo folder
# open http://localhost:8000/counter/
```

## Use it

```html
<script src="counter.js"></script>
<sakuga-counter value="0" label="Combo" milestone="10"></sakuga-counter>
```

```js
const counter = document.querySelector('sakuga-counter');
counter.add(1);       // increment combo
counter.add(10);      // milestone burst + ドン!
counter.reset();      // reset to 0
```

| attribute | what it sets | default |
|---|---|---|
| `value` | current numeric value | `0` |
| `label` | description text | `Hits` |
| `milestone` | interval triggering the impact burst | `10` |
