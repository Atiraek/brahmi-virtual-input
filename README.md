# 𑀩𑁆𑀭𑀸𑀳𑁆𑀫𑀻 Keyboard · Brahmi Virtual Input

A responsive, browser-based virtual keyboard for typing in the **Brahmi script** (𑀩𑁆𑀭𑀸𑀳𑁆𑀫𑀻, U+11000–U+1107F) — the ancient writing system behind most South and Southeast Asian scripts. No installation, no OS-level changes, works on any device with a browser.

---

## Access

**Docker (self-hosted):**
```sh
docker compose up -d
# → http://localhost:8082
```

**GitHub:** [github.com/Atiraek/brahmi-virtual-input](https://github.com/Atiraek/brahmi-virtual-input)

Or just open `index.html` directly in any browser — it works offline.

---

## How to Use

1. **Tap a key** — the character appears in the text box above.
2. **Compose freely** — tap vowels, consonants, vowel signs, diacritics, digits, or punctuation in any order.
3. **Copy** — tap the **📋 Copy** button to copy your text to clipboard.
4. **Undo** — tap **↩ Undo** to step back through your edit history.
5. **Clear** — tap **✕ Clear** to start fresh.
6. **Backspace** — the **⌫** key deletes the last character (or selected text).

The text box is read-only to prevent your device's on-screen keyboard from popping up — all input happens through the virtual keys.

### Pro tip
Brahmi is an **abugida**: each consonant carries an inherent vowel /a/. To suppress it, tap **virama** (𑁆, U+11046) after a consonant. To add a different vowel, tap a **vowel sign** after the consonant.

---

## Keyboard Layout

The keys are grouped by linguistic category, mirroring the traditional Brahmic varga system.

| Section | Contents |
|---------|----------|
| **Vowels** | A, Ā, I, Ī, U, Ū, ṛ, ṝ, ḷ, ḹ, E, AI, O, AU — independent vowel letters |
| **Vowel Signs** | AA, Bhattiprolu AA, I, II, U, Ū, Voc R, Voc RR, Voc L, Voc LL, E, Ai, O, Au — dependent matras (attach to consonants) |
| **Velar** (Ka-varga) | ka, kha, ga, gha, ṅa |
| **Palatal** (Ca-varga) | ca, cha, ja, jha, ña |
| **Retroflex** (Ṭa-varga) | ṭa, ṭha, ḍa, ḍha, ṇa |
| **Dental** (Ta-varga) | ta, tha, da, dha, na |
| **Labial** (Pa-varga) | pa, pha, ba, bha, ma |
| **Other Consonants** | ya, ra, la, va, śa, ṣa, sa, ha |
| **Liquid & Rare** | ḷa, O.Tamil LLLA / RRA / NNNA, O.Tamil Short E / O, O.Tamil LLA |
| **Diacritics & Signs** | candrabindu, anusvāra, visarga, jihvāmūlīya, upadhmānīya, **virama** (halant), O.Tamil virama |
| **Digits** | 𑁦 0 through 𑁯 9 |
| **Numbers** | 1–9, 10, 20, 30… 90, 100, 1000 — Brahmi numeral symbols |
| **Punctuation** | danda, double danda, dot, double dot, line, crescent bar, lotus, number joiner |

The **Controls** row at the bottom gives you backspace, space, and newline.

---

## Font Support

Brahmi glyphs require a font covering the Unicode Brahmi block (U+11000–U+1107F).

| Font | Notes |
|------|-------|
| [Noto Sans Brahmi](https://fonts.google.com/noto/specimen/Noto+Sans+Brahmi) | Best option — comprehensive, well-hinted |
| Segoe UI Historic | Ships with Windows 10+ |
| Arial Unicode MS | Bundled with Microsoft Office |
| FreeSerif | Included in many Linux distros |

Without a supporting font, characters will appear as blank boxes or tofu.

---

## Self-Hosted Deployment

```sh
# Build & start
docker compose up -d --build

# Stop
docker compose down

# Rebuild after changes
docker compose up -d --build
```

The container runs nginx:alpine on port **8082**. Edit `docker-compose.yml` to change the port.

---

## Development

Single `index.html` with embedded CSS and JS — no framework, no bundler, no dependencies. The keyboard data lives in the `ROWS` array inside the `<script>` tag. Add or reorder keys by editing this array.

```js
// Each row: { label, keys: [{ c: '\\uD804\\uDCxx' }, ...] }
// Characters use JavaScript surrogate pairs for SMP Unicode codepoints.
```

---

## Planned

- **v2** — Phonetic transliteration (type "namaha" → "𑀦𑀫𑀂")
- **Layout switching** — Toggle between varga groups and a compact layout
- **Dark/light theme toggle**
- **Mobile long-press** for diacritic variants

---

## License

MIT — free to use, modify, and share.
