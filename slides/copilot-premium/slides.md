---
title: "Spend Smart: Copilot Premium Requests"
theme: black
revealOptions:
  transition: slide
  backgroundTransition: fade
---

<!-- .slide: data-background="linear-gradient(135deg, #0d1117 0%, #161b22 40%, #1a1a4e 100%)" -->

# Spend Smart

### Copilot Premium Requests

<br>

*Stop burning tokens — start spending smart* <!-- .element: style="opacity:0.6; font-size:0.75em" -->

Note: This talk is for developers who use GitHub Copilot with premium model access. The goal is practical tactics to get maximum value without blowing through your request quota.

---

<!-- .slide: data-background="#1a1a2e" -->

## 😬 The Problem

<div>
A great portion of premium requests could have been handled by a free model
<small>Don't default to premium — escalate only when needed</small>
</div>

---

<!-- .slide: data-background="#16213e" -->

## Know Your Model Tiers

<div class="three-col" style="margin-top:1em;">

<div>

### <span class="tier tier-free">FREE</span>

**GPT-4.1 · GPT-4o · GPT-5 mini**

✅ Daily coding tasks

✅ Autocomplete

✅ Quick Q&A

<br>

**Cost: 0** premium requests <!-- .element: style="font-size:0.8em; opacity:0.7" -->

</div><!-- .element: class="fragment fade-right" -->

<div>

### <span class="tier tier-mid">MID-TIER</span>

**Claude Sonnet · Gemini 2.5 Pro**

✅ Complex logic

✅ Multi-file reasoning

✅ Code review

<br>

**Cost: 1×** premium request <!-- .element: style="font-size:0.8em; opacity:0.7" -->

</div><!-- .element: class="fragment fade-up" -->

<div>

### <span class="tier tier-heavy">HEAVY</span>

**Claude Opus · o3 · Deep Research**

✅ Architecture decisions

✅ Deep debugging

✅ System design

<br>

**Cost: varies, up to 10×+** <!-- .element: style="font-size:0.8em; opacity:0.7" -->

</div><!-- .element: class="fragment fade-left" -->

</div>

Note: Model availability and multipliers can change — check GitHub's docs for current pricing. The key principle is that heavier models cost dramatically more per request, so match model power to your actual task difficulty.

--

<!-- .slide: data-background="#16213e" -->
### Cost Multiplier Reference

| Model | Multiplier | Best For |
|-------|:----------:|----------|
| GPT-4o / GPT-5 mini | **0** (included) | Everyday coding |
| Claude Sonnet 4 | **1×** | Balanced reasoning |
| Gemini 2.5 Pro | **1×** | Large context tasks |
| Claude Opus 4 | **~5×** | Hard problems only |
| o3 | **~5×** | Deep reasoning chains |
| Deep Research | **~10×+** | Exhaustive analysis |
<br>

[Note: Multipliers are estimates only and subject to change; check current pricing for exact values.](https://docs.github.com/en/billing/concepts/product-billing/github-copilot-premium-requests)

---

<!-- .slide: data-background="#0f3460" -->

## The Escalation Ladder 🪜

<div class="ladder">
<div class="step step-1 fragment fade-up" data-fragment-index="1">
🟢<br>Start<br><strong>FREE</strong><br><span style="font-size:0.75em">GPT-4.1 / 4o</span>
</div>
<div class="step step-2 fragment fade-up" data-fragment-index="2">
🟡<br>If stuck<br><strong>MID-TIER</strong><br><span style="font-size:0.75em">Sonnet / Gemini</span>
</div>
<div class="step step-3 fragment fade-up" data-fragment-index="3">
🔴<br>Last resort<br><strong>HEAVY</strong><br><span style="font-size:0.75em">Opus / o3</span>
</div>
</div>

> *"Treat premium models like senior consultants — bring them in for the hard problems, not the daily standup."* <!-- .element: class="fragment fade-in" data-fragment-index="4" style="font-size:0.8em; opacity:0.8" -->

---

<!-- .slide: data-background="#1a1a2e" -->

<!-- .slide: data-background="#1a1a2e" -->

## Auto Model Selection ✨

<div class="callout" style="font-size:1.05em; text-align:center;">
Turn it on. Keep it on. Forget about it.
</div>

- Optimizes for model availability and load to reduce rate‑limit failures and improve throughput/latency. <!-- .element: class="fragment fade-up" -->
- Automatically falls back to responsive endpoints and lower‑cost models when appropriate, lowering spend without manual tuning. <!-- .element: class="fragment fade-up" -->
- Zero maintenance after setup. <!-- .element: class="fragment fade-up" -->

**→ Recommended as your default configuration** <!-- .element: class="fragment fade-in" style="color:#3fb950" -->

Note: See GitHub's docs for details and behavior: [Auto model selection](https://docs.github.com/en/copilot/concepts/auto-model-selection)

---

<!-- .slide: data-background="#16213e" -->

## Prompt Like a Pro 🎯

<div class="two-col do-dont" style="margin-top:1em;">

<div>
<h4><span class="do">✅ Do</span></h4>
<ul>
<li class="fragment fade-right" data-fragment-index="1">Give full context in <strong>one</strong> prompt</li>
<li class="fragment fade-right" data-fragment-index="2">Ask for a <strong>plan first</strong>, then code</li>
<li class="fragment fade-right" data-fragment-index="3">Share only <strong>relevant</strong> files/snippets</li>
<li class="fragment fade-right" data-fragment-index="4"><strong>Batch</strong> related tasks together</li>
</ul>
</div>

<div>
<h4><span class="dont">❌ Don't</span></h4>
<ul>
<li class="fragment fade-left" data-fragment-index="1">Send many tiny back-and-forth prompts</li>
<li class="fragment fade-left" data-fragment-index="2">Jump straight to "write the code"</li>
<li class="fragment fade-left" data-fragment-index="3">Dump the whole repo as context</li>
<li class="fragment fade-left" data-fragment-index="4">Ask one question per message</li>
</ul>
</div>

</div>

<br>

<div class="callout fragment fade-up" data-fragment-index="5">
💡 <strong>Power move:</strong> "Fix the bug, add edge-case tests, and optimize the loop" → one prompt instead of three.
</div>

Note: Every round-trip is a request. If you're on a premium model, three small questions cost 3× more than one well-scoped prompt. Also asking for a plan first catches misunderstandings before you waste a generation on wrong code.

---

<!-- .slide: data-background="#1a1a2e" -->

## Agent Mode: Handle with Care ⚡

<div class="icon-text fragment fade-up" data-fragment-index="1">
<span class="icon">⚠️</span>
<span>Agent mode triggers <strong>multiple hidden model calls</strong> — one run can consume <strong>5–10+ premium requests</strong></span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="2">
<span class="icon">✅</span>
<span><strong>Best for:</strong> multi-file refactors, scaffolding, complex debugging</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="3">
<span class="icon">🚫</span>
<span><strong>Avoid for:</strong> simple edits, quick questions, single-file changes</span>
</div>

<div class="callout warn fragment fade-up" data-fragment-index="4">
⚡ Before hitting "agent mode" — ask: <em>is this a 1-prompt job or a 10-prompt job?</em>
</div>

Note: Agent mode is incredibly powerful but it's a premium-request amplifier. It plans, executes, validates, and iterates and each step is a model call. Use it intentionally for work that genuinely needs multi-step autonomous execution.

---

<!-- .slide: data-background="#0f3460" -->

## Supercharge Your Context 📂

<div class="two-col" style="margin-top:1em;">

<div>
<h3>What to Add</h3>
<ul>
<li class="fragment fade-right" data-fragment-index="1"><code>AGENTS.md</code> / project instructions</li>
<li class="fragment fade-right" data-fragment-index="2">Coding standards & conventions</li>
<li class="fragment fade-right" data-fragment-index="3">Architecture overview & patterns</li>
<li class="fragment fade-right" data-fragment-index="4">Key dependencies & API contracts</li>
</ul>
</div>

<div>
<h3>Why It Helps</h3>
<ul>
<li class="fragment fade-left" data-fragment-index="1">Fewer retries & clarification rounds</li>
<li class="fragment fade-left" data-fragment-index="2">Output matches your style on first pass</li>
<li class="fragment fade-left" data-fragment-index="3">Avoids wrong assumptions about structure</li>
<li class="fragment fade-left" data-fragment-index="4">Reduces context-stuffing in every prompt</li>
</ul>
</div>

</div>

<br>

<div class="callout fragment fade-up" data-fragment-index="5">
💡 <strong>Better context = better first-pass output = fewer premium retries</strong>
</div>

Note: Think of project instructions as a one-time investment. You write them once, and every future Copilot interaction benefits. This is especially high-ROI for teams — one good AGENTS.md saves premium requests across all developers.

---

<!-- .slide: data-background="#16213e" -->

## Team Playbook 📋

<div class="icon-text fragment fade-up" data-fragment-index="1">
<span class="icon">📏</span>
<span><strong>Define tier guidelines</strong> — which model for which task type. No guessing, no waste.</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="2">
<span class="icon">📝</span>
<span><strong>Create prompt templates</strong> — for bug fixes, refactors, test generation. Reduces iteration and improves consistency.</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="3">
<span class="icon">🔍</span>
<span><strong>Use Copilot as a reviewer</strong> — ask for edge cases, performance risks, maintainability issues. High-value reasoning, fewer requests.</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="4">
<span class="icon">📊</span>
<span><strong>Track metrics</strong> — premium requests per PR, time saved, suggestion acceptance rate. Optimize on data, not gut feeling.</span>
</div>

--

<!-- .slide: data-background="#16213e" -->

### Prompt Template Examples

<div class="two-col" style="font-size:0.85em;">

<div>

**🐛 Bug Fix Template**

```text
Bug: [description]
File: [path]
Expected: [behavior]
Actual: [behavior]

Steps to fix:
1. Identify root cause
2. Propose minimal fix
3. Add regression test
```

</div>

<div>

**♻️ Refactor Template**

```text
Refactor: [function/module]
Goal: [readability / performance / DRY]
Constraints:
- Keep public API unchanged
- Maintain test coverage
- Follow [pattern]

Output: refactored code + explanation
```

</div>

</div>

<br>

> *Templates eliminate prompt iteration — get it right the first time.* <!-- .element: style="font-size:0.8em; opacity:0.7" -->

---

<!-- .slide: data-background="linear-gradient(135deg, #1a1a4e 0%, #2d1b69 50%, #0d1117 100%)" -->

## Key Takeaways — Quick Wins 🚀

<ol class="action-plan">
<li class="fragment fade-up" data-fragment-index="1">Enable <strong>auto model selection</strong> — today</li>
<li class="fragment fade-up" data-fragment-index="2">Follow the <strong>escalation ladder</strong> — free → mid → heavy</li>
<li class="fragment fade-up" data-fragment-index="3"><strong>Batch & scope</strong> your prompts — fewer requests, better results</li>
</ol>

---

<!-- .slide: data-background="linear-gradient(135deg, #1a1a4e 0%, #2d1b69 50%, #0d1117 100%)" -->

## Key Takeaways — Team & Habits 🚀

<ol class="action-plan">
<li class="fragment fade-up" data-fragment-index="4">Set up <strong>project instructions</strong> — invest once, save forever</li>
<li class="fragment fade-up" data-fragment-index="5"><strong>Track usage weekly</strong> — don't burn quota early in the cycle</li>
</ol>

<p class="fragment fade-in" data-fragment-index="6" style="font-size:0.85em; font-style:italic; opacity:0.8;">"Think of premium models as senior consultants — bring them in for the hard problems."</p>

Note: The five action items are ordered by effort — #1 is a single toggle, #5 is an ongoing habit. Encourage the team to start with the easy wins and build from there.
