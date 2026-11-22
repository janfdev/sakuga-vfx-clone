# Avatar

An anime hero avatar frame. Hovering or tapping activates an Awakening burst: power wedges, an energy shockwave ring, and a hollow **ポン**.

## Run it

```sh
python3 -m http.server 8000     # from the repo folder
# open http://localhost:8000/avatar/
```

## Use it

```html
<script src="avatar.js"></script>

<!-- Initials avatar -->
<sakuga-avatar text="UA" size="64" status="online"></sakuga-avatar>

<!-- Image avatar -->
<sakuga-avatar src="hero.jpg" alt="Deku" size="64" status="busy"></sakuga-avatar>
```

| attribute | what it sets | default |
|---|---|---|
| `size` | diameter in pixels | `56` |
| `text` | 1-2 fallback characters | `Hero` |
| `src` | image source URL | none |
| `alt` | accessible label | `Avatar` |
| `status` | dot indicator: `online`, `busy`, `away` | none |
