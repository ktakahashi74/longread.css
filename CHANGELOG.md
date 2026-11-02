# Changelog

## v0.1.2 (2026-11-03)

- Chinese text on Windows now stops at Microsoft YaHei (Simplified) or Microsoft JhengHei (Traditional) before the generic serif, instead of falling back to SimSun or MingLiU, which are hard to read in long text on screen. Devices with a Song or Ming face listed earlier still use it.
- Japanese text also looks for "BIZ UDPMincho Medium", the medium weight of BIZ UDPMincho, which Windows lists as a family of its own.

## v0.1.1 (2026-11-02)

- On screens 40rem wide or narrower, running text is slightly smaller (1.0625rem) with tighter leading, so lines stay long enough to read. Scripts with tall marks, footnotes and table cells keep their size, and so does text whose size the page sets.

## v0.1.0 (2026-11-02)

First public release.
