# Popconfirm

A comic speech-bubble confirmation popup. It pops open with anime accent ticks, and confirming hits with a crisp **カチッ**.

## Run it

```sh
python3 -m http.server 8000     # from the repo folder
# open http://localhost:8000/popconfirm/
```

## Use it

Wrap a trigger button with it:

```html
<script src="popconfirm.js"></script>
<sakuga-popconfirm title="Discard unsaved changes?">
  <button type="button">Discard</button>
</sakuga-popconfirm>
```

```js
const el = document.querySelector('sakuga-popconfirm');
el.addEventListener('confirm', () => console.log('Confirmed!'));
el.addEventListener('cancel', () => console.log('Cancelled!'));
```

| attribute | what it sets | default |
|---|---|---|
| `title` | question or prompt | `Are you sure?` |
| `confirm-text` | label of confirm button | `Confirm` |
| `cancel-text` | label of cancel button | `Cancel` |
