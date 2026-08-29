# Yokubi Enhanced

> A typographically restyled build of **Yokubi**, the Japanese grammar guide for beginners and new learners.

📖 **Read it here → [maitodesu.github.io/yokubi-enhanced](https://maitodesu.github.io/yokubi-enhanced/)**

---

## 🎯 What this is

Yokubi is a from-scratch Japanese grammar guide written by [**Morgawr**](https://github.com/Morgawr) — it teaches Japanese as Japanese, rather than as decoded English, and it is genuinely excellent. This repository contains **the same book, none of the words changed**, rebuilt with a reworked reading experience.

Not a rewrite. Not a translation. Not a fork of the *content*. Every lesson, every example, every explanation is Morgawr's, verbatim. What changed is how it looks on the page.

**Original:** [github.com/Morgawr/yokubi](https://github.com/Morgawr/yokubi) · [yoku.bi](https://yoku.bi)

---

## ✨ What changed

### 🔤 Typography

| | Before | After |
|---|---|---|
| **Latin text** | Open Sans | **Geist** |
| **Japanese text** | *unspecified* — fell through to whatever the OS defaulted to (Yu Gothic, Meiryo, MS PGothic…) | **Noto Sans JP** |
| **Monospace** | Source Code Pro | **Geist Mono** |

The Japanese font was the real problem. Nothing in the original stylesheet named a CJK typeface, so kana and kanji rendered in the browser's script default — meaning the book looked different on every machine, and often quite ugly. It is now pinned to Noto Sans JP, loaded subset-by-subset so the page stays light.

### 📐 Example blocks

Every Japanese specimen in this book lives in a `<pre>` block, and they were previously drawn as a 4%-alpha panel — effectively invisible against the page. They are now typeset as quoted specimens:

- 🎨 Themed background with a hairline border and an accent rule down the left edge
- 📏 `line-height: 1.9`, because CJK glyphs need vertical room that Latin leading doesn't give them
- 📖 Full content width instead of an awkward centered 80%
- 🔆 **The grammar point is tinted.** The bolded fragment in each example — the particle or ending the lesson is actually teaching — now renders in the accent colour, so you can see the subject of the lesson at a glance instead of hunting for it

### 🈁 Furigana

Ruby annotations were cramped and oversized. Now scaled to `0.55em` at 75% opacity, explicitly positioned above the base text, and marked `user-select: none` — **so copying a sentence gives you clean Japanese, not kanji interleaved with kana.**

### 📊 Everything else

- 🪜 Reworked heading rhythm and body leading for long-form reading
- 📋 Tables stripped of their boxed-grid look — a single accent rule under the header, uppercase tracked-out labels, row hover
- 🖼️ Rounded images, tightened sidebar spacing, bolded active chapter

### 🎨 Theme support

Every colour keys off mdBook's own CSS variables rather than hardcoded values, so **light, rust, coal, navy, and ayu all stay coherent.** The accent is amber, tuned per theme — `#e0a53f` on dark backgrounds, `#a55f00` on light ones.

### ⚙️ Build

- ⬆️ CI tracks the **latest mdBook release** instead of the original's 0.4.36 pin
- 🚀 Deploys to GitHub Pages on every push to `main`

---

## 🛠️ Building locally

```bash
cargo install mdbook
mdbook serve
```

Then open <http://localhost:3000>. The book live-reloads as you edit.

Furigana is expanded by a preprocessor (`scripts/preprocess-furigana.py`) that turns `{f|漢字|かんじ}` into `<ruby>` markup, so **Python 3 must be on your `PATH`** for the build to work.

---

## 🔄 Staying current with upstream

Morgawr's repository is wired up as the `upstream` remote:

```bash
git fetch upstream
git log --oneline HEAD..upstream/main   # anything new?
git merge upstream/main
git push
```

Lesson content lives entirely in `src/` and is never modified here, so new and revised lessons merge cleanly. The only file that can realistically conflict is `style/custom.css`, since that is precisely what this repository rewrites.

---

## 🙏 Credits & licence

**Yokubi is written by [Morgawr](https://github.com/Morgawr)** and the contributors to the [original repository](https://github.com/Morgawr/yokubi). All of the writing, teaching, grammar explanations, and example sentences are theirs. Please read it at **[yoku.bi](https://yoku.bi)**, and consider joining the project's [Discord community](https://discord.gg/KZj4dVFDzu) or contributing corrections upstream — improvements belong there, where everyone benefits.

This repository contributes stylesheet changes and nothing else.

Licensed under **[Creative Commons Attribution 4.0 International](LICENSE)** (CC BY 4.0), the same licence as the original work.
