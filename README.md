# Prompt Lab 🧪

**Turn a rough idea into a prompt Claude actually nails.**

Prompt Lab is a tiny, free tool that takes a task or prompt you're about to send an AI and either **rewrites it** into a clear, complete, ready-to-send prompt — or asks you **a few quick questions first** when something important is missing. It's built for kicking off **new projects or bigger tasks** that need good instructions, not quick one-off questions.

- ✅ Runs inside the Claude you already use — **no API key, no sign-up, no cost beyond your normal Claude usage**
- ✅ Works in **Claude chat** *and* **Claude Code**
- ✅ Nothing to host, no account to connect — **under 10 minutes to set up**
- ✅ In Claude Code it only activates when you ask — it won't butt in on every message

---

## Two ways to use it

### A) Claude chat (easiest — ~1 minute)
1. Open [`chat/prompt-lab.md`](chat/prompt-lab.md) and **copy the whole thing**.
2. Paste it into a new Claude chat and send it.
3. Claude replies asking for your rough prompt. Paste your draft.
4. You get back an improved prompt (or a couple of quick questions first).

That's it — no install.

### B) Claude Code (a drop-in skill — ~5 minutes)
Install once, then use it in any project.

**Install (Windows):**
1. Download this repo (green **Code ▸ Download ZIP**, then unzip).
2. Copy the folder `claude-code/prompt-lab` into your personal skills folder:
   ```
   C:\Users\<your-username>\.claude\skills\prompt-lab
   ```
   (Create the `skills` folder if it isn't there.) PowerShell one-liner — run it from inside the unzipped repo:
   ```powershell
   $dest = "$HOME\.claude\skills\prompt-lab"
   New-Item -ItemType Directory -Force -Path $dest | Out-Null
   Copy-Item -Recurse -Force ".\claude-code\prompt-lab\*" $dest
   ```
   *Mac/Linux:* copy it to `~/.claude/skills/prompt-lab` instead.
3. Restart Claude Code.

**Use it:** type `/prompt-lab`, or just ask — *"improve this prompt"*, *"help me write a prompt for …"*, *"make this task instruction stronger."*

> **Prefer it in one project only?** Put the folder in that project's `.claude\skills\prompt-lab` instead of your home folder.

---

## Will the skill trigger on everything? No.

A **skill** is not a **hook**. A hook runs on every message; Prompt Lab doesn't. It only activates when:
1. You call it by name (`/prompt-lab`), or
2. You clearly ask to improve a *prompt* (e.g. "sharpen this prompt before I send it").

Normal requests — "fix this bug", "write me an email", "explain X" — won't wake it. If it ever offers when you didn't want it, just ignore it; it never rewrites anything on its own.

---

## What it checks (the improvement lens)

It strengthens your prompt across nine things great instructions share:

| # | Element | What it means |
|---|---------|---------------|
| 1 | **Goal** | One clear objective |
| 2 | **Context** | Background Claude needs (your situation, tools, end use) |
| 3 | **Audience** | Who the output is for |
| 4 | **Deliverable & format** | The exact shape of the output (doc, table, checklist, code…) |
| 5 | **Constraints** | Budget, platform, tools, timeline, skill level, must/avoid |
| 6 | **Success criteria** | How you'll know it worked |
| 7 | **Collaboration** | Permission to ask before assuming |
| 8 | **Scope & steps** | For big work: the phases, and what's in vs out of scope |
| 9 | **Examples & references** | Samples, files, links, or a style to match |

The point isn't a score — it's getting your prompt to where **Claude understands it and is set up to succeed**.

---

## See it work

[`examples/before-after.md`](examples/before-after.md) shows a weak prompt turned into a strong one.

## How it's designed

[`SPEC.md`](SPEC.md) — the full design (the flow, the lens, when it rewrites vs asks questions).

## License

MIT — see [LICENSE](LICENSE). Use it, share it, change it.
