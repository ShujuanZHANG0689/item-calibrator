# Item Calibrator · 试题校准器

**See how your test questions performed — in your browser, for free.**
**看清每道试题的表现 — 免费，且全程在你的浏览器中完成。**

Item Calibrator is a single-page web app that takes a grid of student scores and tells you which questions on a test worked, which were too easy or too hard, and which to fix. It also estimates each student's ability and shows how well the whole test is targeted to your class.

It is built for **teachers and assessment teams**: no sign-up, no installation, and no data ever leaves the browser. Open the page, paste your scores, and read the results in plain language.

> Two analysis modes are included:
> - **Classical Test Theory (CTT)** — difficulty, discrimination, item–total correlation, and KR-20 reliability.
> - **Item Response Theory (IRT)** — a 2PL or Rasch (1PL) model that places item **difficulty (b)**, item **discrimination (a)**, and student **ability (θ)** on one shared scale, with a Wright map, item characteristic curves, and a test information function.

---

## Quick start

No build step, no dependencies. Either:

- **Download and open** — grab `index.html` and double-click it. It works offline.
- **Or host it** — drop `index.html` on any static host (see *Publish your own copy* below).

Then click **"Try it with an example class"**, or paste your own data.

A ready-made example, `sample-data.csv`, is included — 40 students and 10 questions, with a deliberately easy item and a deliberately mis-keyed one so you can see how the app flags problems.

---

## What you get

- **Bilingual interface (English / 中文).** Every label, insight, chart axis, and tooltip switches language from the toggle in the top bar; the page also auto-detects Chinese browsers on first load. 界面支持中英双语，一键切换。
- **Light and dark themes.** A calm light theme for daylight and a deep slate dark theme, switchable from the top bar.
- **Plain-language insights.** Every analysis opens with a short, prioritised read-out: what's working, what's too easy or too hard, and which question to check first (mis-keyed answers are surfaced at the top).
- **A "How to read these results" guide** built into the page, so newcomers don't need a measurement background.
- **Clear visuals.** A difficulty scale, a difficulty × discrimination map, and — in IRT mode — a Wright map, item characteristic curves, and a test information curve.
- **Sortable tables** of every item and (in IRT) every student, with a precision estimate (SE) per student.
- **Exports.** Download item statistics and ability scores as CSV, or **Print / Save as PDF** for a clean one-page report to attach to a test review.
- **Privacy by design.** All computation is client-side. Nothing is uploaded.

---

## Your data format

A simple grid: **one row per student, one column per question.** Use `1` for a correct answer and `0` for incorrect.

```
Student,Q1,Q2,Q3,Q4
Ann,1,1,0,1
Ben,1,0,0,1
Cara,1,1,1,0
```

- The **first row** can name your questions (toggle "First row is item names").
- The **first column** can hold student names or IDs (toggle "First column is an ID").
- Have raw answers instead of 0/1? Switch to **"Raw + answer key"** and paste the key; the app scores it for you.
- Blank cells are treated as incorrect by default (you can change this).

CSV and tab-separated data both work. You can paste, upload a file, or load the built-in example.

---

## How it works

**Classical Test Theory.** Difficulty `p` is the proportion of students answering correctly. Discrimination `D` is the correct-rate in the top 27% of scorers minus the bottom 27%. The corrected item–total correlation `r(item-rest)` relates each item to the total of the *other* items. Test reliability is reported as **KR-20**. Discrimination labels follow Ebel's bands (≥.40 excellent, .30–.39 good, .20–.29 fair, <.20 poor).

**Item Response Theory.** A 2PL (or Rasch/1PL) model is fit by **marginal maximum likelihood** (EM with 40-point quadrature; ability assumed standard normal). Item difficulty `b` and discrimination `a` are reported on the logit scale; student ability `θ` is the **expected a-posteriori (EAP)** estimate with a standard error. Mild priors regularise small samples, and discrimination is bounded below so poorly-fitting or mis-keyed items flag themselves. Reliability is the **marginal reliability**, Var(θ) / (Var(θ) + mean SE²).

Everything is implemented in vanilla JavaScript in a single file — no external libraries, no network calls.

---

## Publish your own copy (GitHub Pages)

1. Create a new repository on GitHub and add these files (`index.html`, `sample-data.csv`, `README.md`, `LICENSE`, `CONTRIBUTING.md`).
   ```bash
   git init
   git add .
   git commit -m "Item Calibrator"
   git branch -M main
   git remote add origin https://github.com/<you>/item-calibrator.git
   git push -u origin main
   ```
2. On GitHub, open **Settings → Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**, select branch **main** and folder **/ (root)**, then **Save**.
4. After a minute your site is live at `https://<you>.github.io/item-calibrator/`.

Because the app is a single static file, it also works on Netlify, Cloudflare Pages, GitLab Pages, or any web server — just serve `index.html`.

---

## Contributing

Contributions are welcome — see [CONTRIBUTING.md](CONTRIBUTING.md). Good first additions include a 3PL model (guessing parameter), Rasch fit statistics (infit/outfit), distractor analysis for multiple-choice options, and translations of the interface copy.

## License

Released under the [MIT License](LICENSE). Free to use, adapt, and share, including in schools and districts.

## A note on interpretation

These statistics describe how questions behaved with *this* group of students; they are tools for review, not verdicts. Small classes give noisier estimates, and a flagged question is an invitation to look closely, not an instruction to delete it. Always pair the numbers with your reading of the question itself.
