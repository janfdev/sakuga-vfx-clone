# Sakuga VFX (Clone & Extended)

> [!NOTE]
> **Pemberitahuan / Disclaimer:**  
> Repositori ini adalah hasil **fork/clone dan eksplorasi pengembangan lanjutan** dari projek asli **[Sakuga VFX](https://github.com/finktheartist/sakuga-vfx)** yang diciptakan oleh **Justin Finkelman ([@finktheartist](https://github.com/finktheartist))**.
> 
> * 🌐 **Situs Asli Resmi:** [https://sakuga-vfx.vercel.app/](https://sakuga-vfx.vercel.app/)
> * 📦 **Repositori GitHub Asli:** [https://github.com/finktheartist/sakuga-vfx](https://github.com/finktheartist/sakuga-vfx)
>
> Seluruh konsep orisinal, teknik rendering efek anime di canvas, tipografi onomatopoeia manga, dan arsitektur inti merupakan karya luar biasa dari author aslinya.

---

Ordinary UI controls that react like anime. At rest they are plain. Use one and it squashes and overshoots on springs, and throws drawn effects around itself: smoke puffs, impact bursts, crystal chips, slashes, splashes, smoke rings and rumbling, with manga sound-effect lettering (ドン!, カチッ, ズザッ, ポン, シュッ, ゴゴゴゴ). No characters, just the way a key animator would sell a hit.

Every effect is drawn in code on one canvas over the page. No dependencies, no build step for you, MIT licensed.

---

## Komponen yang Ditambahkan pada Clone Ini (13 Komponen Baru)

Selain **11 komponen asli** (Button, Toggle, Slider, Checkbox, Radio, Input, Tabs, Progress, Rating, Toast, Tooltip), clone ini memperluas pustaka dengan **13 komponen baru** yang tetap mematuhi prinsip desain *Sakuga VFX*, *modern-web-guidance*, dan *WCAG 2.2 accessibility*:

1. **[Select](select/) (`<sakuga-select>`)**: Dropdown select listbox form-associated; tombol tertekan elastis (*squash*), menu terbuka dengan downward spring unfolding, dan opsi terpilih memicu tebasan sabit dengan suara **カチッ** (*kachi*).
2. **[Accordion](accordion/) (`<sakuga-accordion>`)**: Panel lipat dengan transisi tinggi berbasis physics spring murni; saat terbuka mengeluarkan kepulan debu di engsel (`puff`) diiringi suara gesekan **ズザッ** (*zuza*).
3. **[Stepper](stepper/) (`<sakuga-stepper>`)**: Step navigation bar; garis track terisi tembakan energi laser (`lines`), bulatan step mendarat memicu cincin shockwave (`ring`), debu hentakan kaki (`puff`), dan letupan **ポン** (*pon*).
4. **[Dialog](dialog/) (`<sakuga-dialog>`)**: Modal berbasis native HTML `<dialog>`; meluncur dari atas (*slam down*) dengan getaran lantai (`wob`), awan debu di kedua sudut bawah (`puff`), dan onomatopoeia raksasa **ドン!** (*don*) di atas modal.
5. **[Drawer](drawer/) (`<sakuga-drawer>`)**: Slide-over sheet berkecepatan tinggi; melesat masuk dengan garis kecepatan (`lines`) dan mengerem di tepi layar menghasilkan pecahan kristal (`shards`) dan suara **シュッ** (*shu*).
6. **[Popconfirm](popconfirm/) (`<sakuga-popconfirm>`)**: Balon dialog konfirmasi manga yang melompat keluar dengan aksen panah (`ticks`), tombol konfirmasi memicu kilatan (`kira`) dan suara **カチッ** (*kachi*).
7. **[Badge](badge/) (`<sakuga-badge>`)**: Status badge angka yang membal elastis dengan kilatan bintang dan suara **ポン** (*pon*). Mode dismiss membelah badge menjadi dua dengan pecahan kristal (`shards`).
8. **[Counter](counter/) (`<sakuga-counter>`)**: Combo stat counter dengan digit roll spring; mencapai milestone kelipatan tertentu memicu ledakan bintang anime (`burst`) dan benturan **ドン!** (*don*).
9. **[Card](card/) (`<sakuga-card>`)**: Kartu panel komik interaktif dengan 3D spring tilt mengikuti kursor, bayangan komik offset (`--sk-sh`), dan sudut garis aksi saat di-hover/klik.
10. **[Meter](meter/) (`<sakuga-meter>`)**: Health & combat power gauge; saat terkena serangan (`damage`) berkedip merah (*impact frame*) menyemburkan pecahan kristal (`shards`) dan cipratan (`splash`), saat diisi ulang (`heal`) bergetar dengan suara gemuruh **ゴゴゴゴ** (*gogogo*).
11. **[Segmented](segmented/) (`<sakuga-segmented>`)**: Multi-option pill switcher; indikator melar memanjang (*motion smear / shunpo dash*), melesat, dan mengerem dengan kepulan debu di kedua sudut serta suara **シュッ** (*shu*).
12. **[Spinner](spinner/) (`<sakuga-spinner>`)**: Ki vortex & charging aura loader; terdiri dari 3 cincin energi berputar asinkron yang secara periodik memancarkan gelombang cincin energi (`ring`) dan partikel berkilau (`kira`), serta finishing burst saat selesai.
13. **[Avatar](avatar/) (`<sakuga-avatar>`)**: Frame avatar hero; disentuh atau di-hover memicu mode *Awakening* (lingkaran membal elastis, kipas jarum energi `ticks`, cincin kejut `ring`, dan letupan `pon`).

---

## Daftar Lengkap (24 Drop-in Custom Elements)

| | element | what happens |
|---|---|---|
| [Button](button/) | `<sakuga-button>` | Press and it squashes flat. Let go and it inverts for one frame, a burst goes off behind it, clouds roll off the corners and ドン! lands. `done()` puts a check on it. The secondary variant is a small squash and three wedges. |
| [Toggle](toggle/) | `<sakuga-toggle>` | A drawn animation: the knob smears across, slams into the end and throws up a splash, and the track floods and settles. |
| [Slider](slider/) | `<sakuga-slider>` | The thumb stretches into a teardrop and lags on a spring. Drag fast and cumulus rolls up behind it; let go and a crescent flies on ahead. |
| [Checkbox](checkbox/) | `<sakuga-checkbox>` | Two crescents swing round the box, crystals fly, the tick draws itself, ズザッ in dotted letters. |
| [Radio](radio/) | `<sakuga-radio>` | The dot springs in, a fan of wedges, two puffs and a hollow ポン. |
| [Input](input/) | `<sakuga-input>` | Every key kicks up dust where the caret is. |
| [Tabs](tabs/) | `<sakuga-tabs>` | The raised tab slides, stretching, and lands with wedges and a puff. |
| [Progress](progress/) | `<sakuga-progress>` | A storm cloud rides the leading edge, pebbles lift off the ground, ゴゴゴゴ; at the end a burst, ドン! and a check. |
| [Rating](rating/) | `<sakuga-rating>` | Stars pop in one after another; five gets a burst. |
| [Toast](toast/) | `<sakuga-toast>` | Streaks in as a smear, lands in dust with ズザッ, leaves by shrinking. |
| [Tooltip](tooltip/) | `<sakuga-tooltip>` | The hint springs out like a speech bubble with puffs and カチッ. |
| [Select](select/) | `<sakuga-select>` | Trigger squashes on click, menu drops open on a spring, option selection slashes with カチッ. |
| [Accordion](accordion/) | `<sakuga-accordion>` | Headers squash on press, panels expand with a snappy spring, dust puffs roll from the hinges, ズザッ. |
| [Stepper](stepper/) | `<sakuga-stepper>` | Shoots energy lines along the track, node springs in with a shockwave ring, puff and ポン. |
| [Dialog](dialog/) | `<sakuga-dialog>` | Slams down from above on a spring with dust clouds, floor shockwave, and a massive ドン!. |
| [Drawer](drawer/) | `<sakuga-drawer>` | Streaks in with speed lines and brakes against the viewport edge with シュッ. |
| [Popconfirm](popconfirm/) | `<sakuga-popconfirm>` | Speech-bubble confirmation pops open with accent ticks, confirms with カチッ. |
| [Badge](badge/) | `<sakuga-badge>` | Bounces with a sparkle and ポン on update; dismiss slices with shards. |
| [Counter](counter/) | `<sakuga-counter>` | Numbers roll on a spring; milestone intervals trigger speed lines, impact burst, and ドン!. |
| [Card](card/) | `<sakuga-card>` | Comic panel card with 3D spring tilt, corner speed lines, and click reaction. |
| [Meter](meter/) | `<sakuga-meter>` | Combat power and health gauge. Taking damage flashes an impact frame with crystal shards; charging rumbles with ゴゴゴゴ. |
| [Segmented](segmented/) | `<sakuga-segmented>` | Multi-option dash switcher. Streaks with motion smear and brakes with dust puffs and シュッ. |
| [Spinner](spinner/) | `<sakuga-spinner>` | Ki aura vortex that spins, charges with shockwave rings, and finishes with an impact burst. |
| [Avatar](avatar/) | `<sakuga-avatar>` | Hero avatar frame that awakens with power wedges, shockwave ring, and ポン on hover or tap. |

## The look

White paper, two-tone effects (white, lavender and a violet line), pink accents, and an impact burst on every confirm. The controls' colours are `--sk-*` CSS variables (`--sk-ink`, `--sk-card`, `--sk-pri`, `--sk-acc` and so on), and a page's own `:root { --sk-acc: ... }` wins over the defaults.

## Try them locally

```sh
python3 -m http.server 8000     # from this folder
# open http://localhost:8000/
```

That opens the gallery, with all twenty-four controls live.

## Use one

Each is a single standalone file that defines an element (zero dependencies, plain JavaScript). Copy the component `.js` file directly from this repo into your project (e.g. into `public/sakuga-vfx/` or your assets directory).

Load it with a plain script tag (not `type="module"`) and use its custom element:

```html
<!-- Load any component file directly -->
<script src="meter.js"></script>
<sakuga-meter value="100" max="100" label="HP"></sakuga-meter>
```

> [!NOTE]
> Perintah instalasi CLI registry (`npx shadcn add ...`) sengaja dicabut untuk sementara waktu agar tidak mengarah ke registry pihak ketiga dan menghindari 404, sampai registry baru dipublikasikan. Untuk saat ini cukup copy/download file komponen secara langsung dari repositori ini.

Each folder's README lists the attributes, properties and events. Value controls (select, segmented, toggle, slider, checkbox, radio, input, rating) work inside a `<form>` like the native ones.

**How the files share.** Each file carries its own copy of the core (springs, the effects layer, the lettering, about 40 KB). The first one loaded sets `window.SakugaFX` and the others reuse it, so any mix of them on a page shares one canvas and one animation loop. The toggle is about 500 KB because its frames are inside it.

## Make your own

`skills/sakuga-vfx/` is the workflow these were made by, written as a skill for coding agents. Skill ini tersedia langsung di repositori ini pada folder `skills/sakuga-vfx/` (dan terinstall di Antigravity pada `~/.gemini/config/skills/sakuga-vfx/`).

- `SKILL.md` is the workflow and the rules.
- `core.js` is the core every component is built on.
- `starter.html` is the smallest whole example, a like button.
- `look.mjs` stops the clock, steps a reaction to chosen moments and saves the frames side by side.

## License & Credits

MIT. See [LICENSE](LICENSE).  
Original Author: Justin Finkelman ([GitHub](https://github.com/finktheartist) / [X @crtvTeknologist](https://x.com/crtvTeknologist)).
Original Project: [https://github.com/finktheartist/sakuga-vfx](https://github.com/finktheartist/sakuga-vfx)
