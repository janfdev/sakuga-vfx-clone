# Drawer

A slide-over sheet. It streaks in with speed lines, brakes against the edge with wobble marks, and a crisp **シュッ** flies off.

## Run it

```sh
python3 -m http.server 8000     # from the repo folder
# open http://localhost:8000/drawer/
```

## Use it

```html
<script src="drawer.js"></script>
<sakuga-drawer id="menu" side="right">
  <h2>Navigation</h2>
  <p><a href="#dashboard">Dashboard</a></p>
  <button type="button" data-close>Close</button>
</sakuga-drawer>
```

```js
const drawer = document.getElementById('menu');
drawer.open();
drawer.close();
console.log(drawer.isOpen);
```

| attribute | what it sets | default |
|---|---|---|
| `side` | slide edge: `right`, `left`, `bottom` | `right` |

- **Auto-close trigger:** Any element inside with `data-close` closes the drawer when clicked.
- **Backdrop and Escape:** Clicking outside or pressing Escape closes the drawer.
- **CSS Variable:** `--sk-drawer-width` (default: `380px`), `--sk-drawer-height` (for bottom).
