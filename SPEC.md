# Prompt Lab — design spec

The design behind the tool. This is the "revised Prompt Lab Score spec" — but note
the deliberate shift: **the number is no longer the point.** The goal is to take a
task/prompt and improve it to where **Claude understands it and is set up to
succeed**. The rubric below is used as an *improvement lens* (a checklist that
drives the rewrite), not as a grade to chase.

## 1. Purpose & audience
- **Purpose:** help people get better results from Claude on **project kickoffs and
  larger tasks** that need detailed instructions — without learning prompt
  engineering theory.
- **Audience:** people who already use Claude (chat and/or Claude Code), from
  non-technical to moderately technical.

## 2. How it connects to each person's Claude
It doesn't "connect" to anything — it **runs inside the Claude the person is
already signed into** (chat or Claude Code). No API key, no shared credentials, no
backend, no hosting. This is what makes setup under 10 minutes and keeps every
person on their own account.

## 3. The improvement lens (9 elements)
The original seven, plus two for bigger projects (8–9):

| # | Element | Fixable by Claude? | Usually needs the user? |
|---|---------|:---:|:---:|
| 1 | Goal | partly | — |
| 2 | Context | — | ✅ |
| 3 | Audience | — | ✅ |
| 4 | Deliverable & format | ✅ | — |
| 5 | Constraints | — | ✅ |
| 6 | Success criteria | partly | ✅ |
| 7 | Collaboration | ✅ | — |
| 8 | **Scope & steps** | ✅ | partly |
| 9 | **Examples & references** | — | ✅ |

There are no fixed weights. Elements that are usually **user-only** (Context,
Audience, Constraints, Success, Examples) are the ones most worth a question when
missing; the rest are filled during the rewrite.

## 4. Score → action (the core logic)
After reading the draft, each weak/missing element is classified:
- **NEEDS-INPUT** — only the user knows it.
- **FIXABLE** — Claude can resolve it.

Then it **branches (smart branch by gap type):**
- **Material NEEDS-INPUT gaps present →** ask **one batch of ≤5 targeted
  questions** (numbered, each with a reason/example and a labelled default), then
  wait, then rewrite.
- **No material NEEDS-INPUT gaps →** rewrite immediately, filling FIXABLE gaps with
  clearly-reasonable, labelled defaults.

Design constraints on the ask step: at most one round, at most five questions,
every question skippable ("use your defaults"). It should **never block** or
interrogate.

## 5. Output contract
1. **✨ Improved prompt** — one copy-paste code block, written as instructions to
   Claude in the user's voice, labelled sections, specific, tool-appropriate,
   ending with "Before you start, ask me about anything important that's missing."
2. **🔧 What changed & why** — 2–4 bullets.
3. **✅ Readiness** — one line (ready / ready-with-assumptions). This replaces the
   old 0–100 score as a light signal.

## 6. Tool-appropriate shaping
- **Claude Code** task (build/edit code): shape around files, concrete steps,
  acceptance checks.
- **Claude chat** task (written deliverable): shape around the output and its
  format.
- Unclear which → it asks as one of the ≤5 questions.

## 7. Triggering (Claude Code skill)
A skill, not a hook — it does not run on every message. It activates only on
explicit invocation (`/prompt-lab`) or a clear "improve my prompt" intent, and the
skill `description` carries explicit *do-not-use* guidance for ordinary task
requests. See `claude-code/prompt-lab/SKILL.md`.

## 8. Packaging & distribution
- Public GitHub repo, one shareable link, "Download ZIP" for non-technical users.
- Two entry points from one brain: the paste-in chat prompt (`chat/prompt-lab.md`)
  and the Claude Code skill (`claude-code/prompt-lab/SKILL.md`). Both encode the
  same flow so results match across surfaces.

## 9. Success criteria (from the brief)
- A colleague downloads it, uses their own Claude, and improves a prompt in **under
  5 minutes** without help → README + paste-in prompt.
- A weak prompt scoring **below 60** reaches **85+** after **one** rewrite or
  question round → the flow + `examples/before-after.md`.
- The share link and the paste-in prompt both work in a **fresh Claude chat and in
  Claude Code** → verified before release.
