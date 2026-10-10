# PRD Studio

**Write the requirement. Then pressure-test it.**

A browser tool that turns a rough idea into a structured Product Requirements Document, and runs any PRD through a senior-PM review that scores completeness and flags ambiguity, missing acceptance criteria, and unquantified metrics.

No backend, no API key, no cost — it runs entirely client-side and is free to host. An optional live-AI mode adds a qualitative pass from Claude when available.

🔗 **Live demo:** [pragatisirsat24-creator.github.io/prd.html](https://pragatisirsat24-creator.github.io/prd.html) · 👤 **Built by** [Pragati Sirsat](https://www.linkedin.com/in/pragatisirsat/)

---

## Why I built this

I've written and shipped 30+ PRDs across fintech and insurance products. The slow part was never the writing — it was catching the gaps: the goal with no number behind it, the user story with no acceptance criteria, the word "seamless" doing the work that a measurable outcome should.

So I encoded the review I run in my head into a tool. It's the same rubric I use as a Product Owner: a PRD a team can actually build against, or it isn't done.

## What it does

**Generate** — Fill in a few inputs (problem, users, goal, scope, metric) and get a structured PRD: overview, problem & context, goals and non-goals, auto-generated user stories, functional requirements, success metrics, Given/When/Then acceptance criteria, dependencies, and open questions. Anything you leave blank becomes a clearly flagged `TODO` rather than silently disappearing.

**Review** — Paste any PRD and get:
- a **completeness score out of 100**,
- a **rubric checklist** (pass / warn / fail) across the eight things a PRD needs,
- a **vague-language scan** that highlights subjective words to replace with something testable,
- a ranked list of the **top fixes**.

## The rubric

The review engine weights what actually makes a PRD buildable:

| Check | Weight | Passes when… |
|---|---|---|
| Problem is defined | 16 | The problem, who feels it, and the evidence are stated |
| Success metrics present | 14 | At least one metric exists **and is quantified** |
| Acceptance criteria | 14 | Given / When / Then (or a clear definition of done) is present |
| Target users named | 12 | A specific segment, not "users" |
| Goals stated | 12 | The intended outcome is explicit |
| Non-goals / scope boundary | 12 | What it will *not* do is written down |
| User stories | 10 | Requirements framed as As a… I want… so that… |
| Dependencies / risks | 10 | Assumptions, dependencies and risks are surfaced |

Vague language ("intuitive", "scalable", "fast", "TBD", "as needed", and ~40 more) applies a density-based penalty — because a spec full of subjective words isn't testable.

## How it works

Plain HTML, CSS and JavaScript in a single file. The generator and the review engine are deterministic and run in the browser, so the tool works offline and forever with zero hosting cost.

The **live-AI buttons** call the Anthropic API for a qualitative draft or second opinion. That path is active when the page runs inside Claude; on a static host it degrades gracefully back to the built-in engine, so nothing ever breaks. (To enable live AI on your own domain, route the request through a small server-side proxy that holds the key — never ship an API key in client-side code.)

## Run it

It's a static site. Any of these work:

```bash
# locally
python3 -m http.server 8000   # then open http://localhost:8000/prd.html
```

- **Netlify:** drag the folder onto [netlify.com/drop](https://app.netlify.com/drop)
- **GitHub Pages:** push to a repo, enable Pages on the default branch
- **Vercel:** import the repo, no build step needed

Keep `prd.html` alongside `index.html` if you're hosting the portfolio too — the portfolio links to it directly.

## Roadmap

- [ ] Export generated PRD to PDF
- [ ] Save / load drafts (in-session)
- [ ] Domain presets (insurance, loyalty, e-commerce) for faster examples
- [ ] Server-side proxy template for live AI on a custom domain

## What this demonstrates

Requirements engineering as a craft, not a template: knowing what a PRD needs, why each part matters, and how to spot a weak one fast — plus shipping a small AI-adjacent product end to end.

---

© 2026 Pragati Sirsat · Product Owner @ Mercedes-Benz Insurance · MSc Entrepreneurship & Innovation Management
