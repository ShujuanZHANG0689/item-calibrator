# Contributing to Item Calibrator

Thanks for your interest in improving this tool for educators.

## Ground rules

- **One file, no build.** The whole app lives in `index.html` (HTML + CSS + vanilla JavaScript). Please keep it dependency-free and working offline — no external scripts, no network calls, no analytics.
- **Privacy first.** Never add anything that uploads, logs, or transmits user data.
- **Plain language.** This is for teachers. New copy should be readable without a measurement background; keep the technical detail available but not in the way.
- **Accessibility.** Maintain keyboard focus styles, sufficient colour contrast, and text labels on anything colour-coded (don't rely on colour alone).

## Working on it

1. Fork and clone the repository.
2. Open `index.html` in a browser. Edit, refresh, repeat — that's the whole loop.
3. Test with `sample-data.csv` and with edge cases: very small classes, items everyone gets right or wrong, missing cells, and a mis-keyed item.
4. Open a pull request describing the change and who it helps.

## Ideas that would help educators

- **3PL model** (adds a guessing parameter) for multiple-choice tests.
- **Rasch fit statistics** (infit / outfit mean-squares) to flag misfitting items.
- **Distractor analysis** — which wrong options attracted which students.
- **Differential item functioning (DIF)** between two groups.
- **Interface translations** for non-English classrooms.
- **More export formats** (e.g., a formatted printable report template).

## Methods

If you touch the statistics, please keep the methods note in the footer accurate, and add a short comment explaining any formula so the next contributor can follow it.
