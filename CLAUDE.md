# longread.css

A single CSS file for reading essays, papers and long posts on screen, in many languages and scripts. No build step, no dependencies, MIT. This file holds the rules for working on it; README.md describes it for users.

## Rules

- The product is `longread.css`, one file. Do not add a build step, dependencies or JavaScript. Footnote popovers and tables of contents are left to other libraries, such as littlefoot and tocbot.
- The contract with pages is: `class="longread"`, a correct `lang`, `dir` where needed, and footnotes in pandoc or GFM markup. Do not require classes on elements inside the container, because sanitisers often remove them. KaTeX output is the only exception.
- No colour palette. Derive rules, borders and backgrounds from `currentColor` with `color-mix()`, and put a plain `currentColor` declaration before it as a fallback. Link colours belong to the page.
- Use logical properties for margins, padding and borders, so that right-to-left text works.
- Keep the file unlayered and every rule at the specificity of one class (`.longread :where(…)` or `.longread:where(:lang(…))`). Pages that use cascade layers import it with `layer(longread)`. Putting the file itself in a layer made unlayered resets such as `* { margin: 0 }` win over all of it.
- The public variables are those listed in README. Internal defaults use the prefix `--_lr-`.
- Typefaces switch at block-level elements that carry their own `lang`; line-breaking rules switch at every element that carries `lang`.
- Keep the documentation in English.

## Checking changes

Open the four pages in `examples/` (GFM in several languages, a pandoc paper, a reset with a dark theme and a compact reply, and math) in Chrome, Firefox and Safari, at a phone width of about 390px and with the text zoomed. For math, check sideways scrolling at narrow widths, the space between deep subscripts and the scrollbar, and the direction of math inside right-to-left text.

Headless Chrome can take screenshots, for example `google-chrome --headless=new --window-size=900,2600 --screenshot=out.png file://…`; add `--virtual-time-budget=15000` for the math page so that KaTeX renders first. To see which rules or properties a browser drops, inline the CSS in a test page and walk `document.styleSheets`. Put screenshots in `screenshots/`, which git ignores.

## Demo

`demo/` is the public demo, served by GitHub Pages from the main branch. Each page holds an excerpt that is in the public domain both in the United States and where the term is the author's life plus 70 years: the author died in 1955 or earlier, and the text was first published in 1930 or earlier, or was published outside the United States and was already in the public domain in its home country on 1 January 1996. The text is copied by script from the source linked at the foot of the page and checked against it. Do not edit the texts by hand. Where a transcription error was corrected against a scan or another printing (Portuguese, Indonesian, Urdu), the page says so at the foot. The pages set only `lang` and `dir`; keep it that way, since the demo shows the defaults.

## Releasing

1. Describe the change in `CHANGELOG.md` and raise the version in the header comment of `longread.css`.
2. Tag the commit (`vX.Y.Z`) and push the tag. Do not move tags.
3. Pages that use the file copy it from a tag and keep the header comment. They do not edit the copy.
