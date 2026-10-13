# Prompt Lab in action — before & after

A real example of a weak, project-kickoff prompt turned into one Claude can execute
well — in a single question round.

---

## ⬇️ Before (weak)

> Help me make an app to keep track of my card game.

**Why it's weak:** no platform, no audience, no idea what "track" means, no success
measure, no scope, nothing to match. Claude would have to guess almost everything.
*(Covers maybe 2 of the 9 lens elements.)*

---

## 💬 What Prompt Lab does

Because the real gaps are things **only the user knows**, it asks one short batch
of questions (not a rewrite yet):

> A few quick questions, then I'll write the prompt — answer any subset, or say
> "use your defaults":
> 1. **Where will you use it?** phone, web, or desktop? *(or I'll assume: a
>    mobile-friendly web app)*
> 2. **Just you, or other players too?** *(or I'll assume: you now, shareable
>    later)*
> 3. **What's the one thing it must do well?** e.g. score a match point-by-point,
>    track wins/losses, log decks. *(or I'll assume: score a match live)*
> 4. **Any tech to use or avoid?** e.g. no server, works offline. *(or I'll
>    assume: plain web, offline-first, no backend)*
> 5. **Do you want Claude to *build* it (Claude Code) or *plan* it (chat)?** *(or
>    I'll assume: build it in Claude Code)*

**The user replies:**

> 1. Web, but it must work great on my phone. 2. Just me for now. 3. Score a match
> live, one tap per point. 4. Offline, no server. 5. Build it in Claude Code.

---

## ⬆️ After (ready to send)

````
Build a mobile-first web app to score my card-game matches live.

Context: I play a two-player card game and want to track a match point by point as
I play, on my phone, without any internet connection.

Audience: Just me for now; keep it simple enough that I could share it with another
player later.

Deliverable & format: A working web app (HTML/CSS/JavaScript) I can open on my
phone's browser and add to my home screen. No build tools if avoidable.

Core behaviour (the thing it must do well):
- One tap per point to add a point to a player.
- Show the current score large and clear.
- Let me start a new match and undo the last point.

Constraints:
- Must work fully offline — no server, no account, no external calls.
- Save the current match so it survives a page refresh (use local storage).
- Mobile-first layout; big tap targets.

Scope & steps:
1. Scaffold a single-page app with two player panels and a score display.
2. Add tap-to-score, undo, and new-match.
3. Persist the match locally and reload it on open.
4. Make it installable (add-to-home-screen) and offline-capable.
Out of scope for now: multiple simultaneous matches, stats history, online play.

Success criteria: I can open it on my phone with no internet, tap through a full
match, refresh mid-match without losing the score, and install it to my home
screen.

Examples/references: Keep the feel of a simple sports scoreboard — minimal,
high-contrast, readable at arm's length.

Before you start, ask me about anything important that's missing.
````

**🔧 What changed & why**
- Pinned the platform, offline requirement, and core action (one tap per point) so there's nothing to guess.
- Broke the build into ordered steps with explicit *out of scope*, so a big task stays focused.
- Added testable success criteria and a style reference.

**✅ Readiness:** Ready to send.

*Now covers all 9 lens elements — the jump from "guess everything" to "execute
confidently."*
