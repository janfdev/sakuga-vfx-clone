# Badge

An animated notification badge or dismissible tag. Bounces with a sparkle and **ポン** on count update, and slices with shards when dismissed.

## Run it

```sh
python3 -m http.server 8000     # from the repo folder
# open http://localhost:8000/badge/
```

## Use it

```html
<script src="badge.js"></script>

<!-- Notification Count -->
<sakuga-badge count="5"></sakuga-badge>

<!-- Max Threshold -->
<sakuga-badge count="120" max="99"></sakuga-badge>

<!-- Dismissible Tag -->
<sakuga-badge dismissible>Pro Hero</sakuga-badge>
```

```js
const badge = document.querySelector('sakuga-badge');
badge.count = 12;      // triggers bounce & ポン
badge.dismiss();       // dismisses with shards
```

| attribute | what it sets | default |
|---|---|---|
| `count` | number to display | none |
| `max` | maximum number before appending `+` | `99` |
| `dismissible` | show close button to dismiss | off |
