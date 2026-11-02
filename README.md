# longread.css

A single CSS file for reading essays, papers and long posts on screen, in many languages and scripts.

- One file. No build step, no dependencies, no JavaScript.
- Typefaces, line height, line length and line breaking follow `lang`.
- Works on plain HTML and under resets such as Tailwind Preflight.
- No colours of its own, so dark themes work.
- Right-to-left text works with `dir`.

See the [demo](https://ktakahashi74.github.io/longread.css/demo/): public-domain texts in 23 languages.

## Use

```html
<link rel="stylesheet" href="longread.css">

<article class="longread" lang="ja">
  <h2>見出し</h2>
  <p>本文……</p>
  <p lang="en">A passage in English inside a Japanese article.</p>
</article>
```

Put `class="longread"` on the element that contains the prose, set `lang` (and `dir="rtl"` for right-to-left text), and give passages in other languages their own `lang`. No other classes are needed. Footnotes from pandoc and GFM, tables, figures and KaTeX math are supported.

The column is not centred. Add `.longread { margin-inline: auto; }` to centre it.

## Fonts

longread.css does not load fonts. It uses those on the reader's device: a serif for English and most other languages (Source Serif 4 if the page loads it, otherwise Iowan Old Style, Palatino or Georgia), Mincho for Japanese, Song or Ming for Chinese, Gothic for Korean, and the system font for Thai, Burmese, Khmer, Lao, the Arabic script and the scripts of South Asia. The variables below change them.

## Variables

Set these on `.longread` or an ancestor. The defaults depend on the language and are in `longread.css`.

| Variable | Sets |
|---|---|
| `--longread-font`, `--longread-font-{ja,zh-hans,zh-hant,ko,ui,mono}` | Typefaces |
| `--longread-size`, `--longread-leading` | Text size and line height |
| `--longread-measure` | Maximum line length (`none` for no limit) |
| `--longread-gap` | Space between paragraphs |
| `--longread-align` | Paragraph alignment (`start` by default) |
| `--longread-scroll-margin` | Space above a heading or note reached by a link |

To justify Japanese text only where the column is at full width:

```css
@media (min-width: 44rem) {
  .longread:lang(ja) { --longread-align: justify; }
}
```

## With Tailwind CSS

Import it into a layer between Preflight and the utilities, and do not combine it with `.prose`:

```css
@layer theme, base, components, longread, utilities;
@import "tailwindcss";
@import "./longread.css" layer(longread);
```

## Notes

- Colours, including link colours, are left to the page.
- Wide code blocks, tables and math scroll sideways.
- Not included: tables of contents, footnote popovers, print styles, vertical writing.

## Versions

Copy `longread.css` from a release tag and keep its header comment.

## Credits

longread.css grew out of tomola, a multilingual community, where it is used. Many of its defaults follow [Tailwind CSS Typography](https://github.com/tailwindlabs/tailwindcss-typography), with thanks.

## Licence

MIT. See [LICENSE](LICENSE).
