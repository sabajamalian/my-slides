---
title: "Better Unit Tests with GitHub Copilot"
theme: black
revealOptions:
  transition: slide
  backgroundTransition: fade
---

<!-- .slide: data-background="linear-gradient(135deg, #0d1117 0%, #161b22 40%, #1a1a4e 100%)" -->

# Better Unit Tests

### with GitHub Copilot

<br>

*Stop writing tests by hand — start testing smarter* <!-- .element: style="opacity:0.6; font-size:0.75em" -->

Note: This talk covers practical techniques, features, and workflows for using GitHub Copilot to write higher-quality unit tests faster. Whether you're generating tests for existing code or doing TDD, there's something here for you.

---

<!-- .slide: data-background="#1a1a2e" -->

## Why This Matters

<div class="two-col" style="margin-top:1em;">

<div>

<div class="big-number fragment fade-up" data-fragment-index="1">98%<small>of orgs have tried AI for test generation</small></div>

</div>

<div>

<div class="big-number fragment fade-up" data-fragment-index="2">92%<small>of US devs use AI for testing regularly</small></div>

</div>

</div>

<br>

<div class="callout fragment fade-up" data-fragment-index="3">
Source: GitHub 2024 Developer Survey — 2,000 respondents across US, Brazil, India, Germany
</div>

Note: Testing with AI isn't a nice-to-have anymore — it's mainstream. The question isn't whether to use Copilot for tests, but how to use it well.

---

<!-- .slide: data-background="#16213e" -->

## Your Testing Toolkit 🧰

<div class="three-col" style="margin-top:1em;">

<div>

### Quick

**Inline Suggestions**

✅ Tab-complete test patterns

✅ TDD: name → body

✅ Repetitive assertions

<br>

**`Cmd+I` Inline Chat** <!-- .element: style="font-size:0.8em; opacity:0.7" -->

</div><!-- .element: class="fragment fade-right" -->

<div>

### Conversational

**Copilot Chat**

✅ `/tests` slash command

✅ `/fix` broken tests

✅ Iterative refinement

<br>

**Side panel or inline** <!-- .element: style="font-size:0.8em; opacity:0.7" -->

</div><!-- .element: class="fragment fade-up" -->

<div>

### Autonomous

**Agent Mode**

✅ Runs tests in terminal

✅ Self-corrects failures

✅ Multi-file test suites

<br>

**Coding Agent for PRs** <!-- .element: style="font-size:0.8em; opacity:0.7" -->

</div><!-- .element: class="fragment fade-left" -->

</div>

Note: Think of these as three gears. Use inline for speed, chat for depth, and agent mode for heavy lifting. Pick the right gear for the task.

--

<!-- .slide: data-background="#16213e" -->

### Feature Quick Reference

| Feature | Command | Best For |
|---------|---------|----------|
| Generate tests | **`/tests`** | Full test suite from file or selection |
| Fix failing tests | **`/fix`** | Debug test failures |
| Explain test code | **`/explain`** | Understand generated tests |
| File context | **`#file:path`** | Reference specific implementation |
| Workspace context | **`@workspace`** | Cross-file awareness |
| Plan first | **Plan agent** | Discover edge cases before coding |

<br>

> Copilot does **best** at: writing tests, repetitive code, debugging, regex, and boilerplate <!-- .element: style="font-size:0.75em; opacity:0.7" -->

---

<!-- .slide: data-background="#0f3460" -->

## The `/tests` Workflow ⚡

<div class="icon-text fragment fade-up" data-fragment-index="1">
<span class="icon">1️⃣</span>
<span><strong>Open</strong> the source file you want to test</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="2">
<span class="icon">2️⃣</span>
<span><strong>Open</strong> an existing test file in an adjacent tab (pattern matching)</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="3">
<span class="icon">3️⃣</span>
<span>Type <strong><code>/tests</code></strong> in Copilot Chat — or highlight specific code first</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="4">
<span class="icon">4️⃣</span>
<span><strong>Review</strong> the generated tests — verify they'd catch real bugs</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="5">
<span class="icon">5️⃣</span>
<span>Ask: <em>"What additional tests should be included to ensure full coverage?"</em></span>
</div>

<div class="callout fragment fade-up" data-fragment-index="6">
💡 <strong>Pro tip:</strong> Copilot uses neighboring open tabs for context — keep related files open, close irrelevant ones.
</div>

Note: The adjacent-tab trick is underrated. If you have a well-structured test file open, Copilot will match your framework, naming conventions, and patterns.

---

<!-- .slide: data-background="#1a1a2e" -->

## TDD with Copilot 🔄

The proven cycle from a real-world case study:

<div class="ladder">
<div class="step step-1 fragment fade-up" data-fragment-index="1">
📋<br>Plan<br><strong>DISCOVER</strong><br><span style="font-size:0.75em">Edge cases</span>
</div>
<div class="step step-2 fragment fade-up" data-fragment-index="2">
🔴<br>Red<br><strong>WRITE TESTS</strong><br><span style="font-size:0.75em">All fail</span>
</div>
<div class="step step-1 fragment fade-up" data-fragment-index="3">
🟢<br>Green<br><strong>IMPLEMENT</strong><br><span style="font-size:0.75em">Make pass</span>
</div>
<div class="step step-2 fragment fade-up" data-fragment-index="4">
🔁<br>Repeat<br><strong>NEXT FEATURE</strong><br><span style="font-size:0.75em">New cycle</span>
</div>
</div>

<br>

> *"TDD with Copilot works. Write tests first. Let them fail. Implement to pass."* <!-- .element: class="fragment fade-in" data-fragment-index="5" style="font-size:0.8em; opacity:0.8" -->

Note: This workflow comes from Chris Reddington at GitHub DevRel (January 2026). A year-rollover edge case was caught by tests that would have been embarrassing on Dec 31st. The Plan agent is key — it asks clarifying questions that reveal edge cases you may not have considered.

--

<!-- .slide: data-background="#1a1a2e" -->

### TDD in Practice — Step by Step

<div class="two-col" style="font-size:0.9em;">

<div>

**1. Plan with the Plan Agent**

> *"I need a countdown timer that handles time zones, DST transitions, and year rollover"*

Copilot asks clarifying questions → reveals edge cases you missed <!-- .element: class="fragment fade-up" data-fragment-index="1" -->

</div>

<div>

**2. Write Failing Tests First**

```typescript
describe('countdown', () => {
  it('handles year rollover', () => {
    // Dec 31 → Jan 1 transition
    expect(getCountdown(dec31)).toBe(...)
  })
  it('handles DST transition', () => {
    // Spring forward / fall back
    expect(getCountdown(dstDate)).toBe(...)
  })
})
```
<!-- .element: class="fragment fade-up" data-fragment-index="2" -->

</div>

</div>

<br>

<div class="callout fragment fade-up" data-fragment-index="3">
💡 <strong>Key insight:</strong> Agent mode runs the tests in-terminal, spots failures, and self-corrects the implementation — no manual intervention needed.
</div>

---

<!-- .slide: data-background="#16213e" -->

## Prompting for Better Tests 🎯

### The 3 Core Principles

<div class="icon-text fragment fade-up" data-fragment-index="1">
<span class="icon">🎯</span>
<span><strong>Set the stage</strong> — give a high-level goal before diving into details</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="2">
<span class="icon">🔍</span>
<span><strong>Be specific</strong> — ask for short, focused outputs step by step</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="3">
<span class="icon">📝</span>
<span><strong>Give examples</strong> — provide sample inputs and expected outputs</span>
</div>

Note: These three principles are the foundation of effective prompting for test generation. The more specific you are about scope, edge cases, and expected behavior, the better the tests.

--

<!-- .slide: data-background="#16213e" -->

### Good vs Bad Prompts

<div class="two-col do-dont" style="margin-top:1em;">

<div>
<h4><span class="do">✅ Good Prompt</span></h4>

*"Develop a comprehensive suite of unit tests for the `BankAccount` class in Python. Write multiple test methods covering:*
- *edge cases (zero balance, overdraft)*
- *exception handling (invalid amounts)*
- *data validation (negative deposits)"*

</div>

<div>
<h4><span class="dont">❌ Bad Prompt</span></h4>

*"Write tests for BankAccount"*

<br>

This produces basic happy-path tests only — missing edge cases, error handling, and boundary conditions.

</div>

</div>

--

<!-- .slide: data-background="#16213e" -->

### Iterative Refinement

Don't try to get everything in one prompt. Build up:

<div class="icon-text fragment fade-up" data-fragment-index="1">
<span class="icon">1️⃣</span>
<span><em>"Write unit tests for the deposit function"</em></span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="2">
<span class="icon">2️⃣</span>
<span><em>"Add a test for invalid deposit amounts that verifies the correct exception is raised"</em></span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="3">
<span class="icon">3️⃣</span>
<span><em>"Add integration tests using mocks for the NotificationService"</em></span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="4">
<span class="icon">4️⃣</span>
<span><em>"What additional tests should be included to ensure full coverage?"</em></span>
</div>

<br>

<div class="callout fragment fade-up" data-fragment-index="5">
💡 That last prompt is a <strong>power move</strong> — Copilot identifies gaps you haven't thought of.
</div>

---

<!-- .slide: data-background="#0f3460" -->

## Context Optimization Tips 📂

<div class="two-col" style="margin-top:1em;">

<div>
<h4><span class="do">✅ Do</span></h4>
<ul>
<li>Open implementation files <strong>alongside</strong> tests</li>
<li>Set <strong>imports manually</strong> — signal your framework</li>
<li>Use <strong>meaningful names</strong> — <code>calculateAverageGrade()</code></li>
<li>Add <strong>top-level comments</strong> describing the module</li>
<li>Use <strong><code>#file</code></strong> references for targeted context</li>
</ul>
</div><!-- .element: class="fragment fade-right" -->

<div>
<h4><span class="dont">❌ Don't</span></h4>
<ul>
<li>Leave <strong>irrelevant files</strong> open in tabs</li>
<li>Let Copilot <strong>guess</strong> your test framework</li>
<li>Use vague names — <code>calc()</code>, <code>foo()</code></li>
<li>Rely on <strong>stale chat context</strong> from old tasks</li>
<li>Dump the <strong>entire repo</strong> as context</li>
</ul>
</div><!-- .element: class="fragment fade-left" -->

</div>

<br>

<div class="callout fragment fade-up">
💡 <strong>Start a new chat session</strong> when switching tasks — stale context degrades output quality.
</div>

Note: Context window management is a skill. It's context engineering, not just prompt engineering. The quality of your tests is directly proportional to the quality of context you provide.

---

<!-- .slide: data-background="#1a1a2e" -->

## Custom Instructions — The Force Multiplier 🔧

Three levels, each building on the last:

| Level | File | Scope |
|-------|------|-------|
| **Repo-wide** | `.github/copilot-instructions.md` | All Copilot interactions |
| **Path-specific** | `.github/instructions/*.instructions.md` | Files matching glob patterns |
| **Agent-specific** | `AGENTS.md` / `CLAUDE.md` / `GEMINI.md` | Per-agent behavior |

<br>

<div class="callout fragment fade-up">
💡 Write them once → every future test generation benefits → entire team benefits
</div>

Note: Custom instructions are a one-time investment with compound returns. They persist context between sessions without polluting the chat window.

--

<!-- .slide: data-background="#1a1a2e" -->

### Example: Path-Specific Test Instructions

```yaml
---
applyTo: "**/*.test.ts,**/*.spec.ts"
---
## Test Requirements
- Use table-driven tests when possible
- Always test edge cases and error handling
- Follow AAA pattern (Arrange, Act, Assert)
- Use descriptive test names: "should [expected] when [condition]"
- Mock external services — never hit real APIs
- Target >80% branch coverage
```

Save as `.github/instructions/testing.instructions.md`

Note: The `applyTo` glob pattern means these instructions automatically apply whenever Copilot works with test files. No need to repeat yourself in every prompt.

--

<!-- .slide: data-background="#1a1a2e" -->

### What to Include in Your Instructions

<div class="icon-text fragment fade-up" data-fragment-index="1">
<span class="icon">🏃</span>
<span>Exact <strong>commands</strong> to run tests: <code>npm test</code>, <code>pytest</code>, <code>make test</code></span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="2">
<span class="icon">📦</span>
<span><strong>Framework & version</strong>: Jest 29, Vitest, pytest 8, etc.</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="3">
<span class="icon">📐</span>
<span><strong>Naming conventions</strong>: <code>*.spec.ts</code>, <code>test_*.py</code>, folder structure</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="4">
<span class="icon">🎨</span>
<span><strong>Patterns & style</strong>: AAA, Page Object Model, test factories</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="5">
<span class="icon">⚠️</span>
<span><strong>Gotchas</strong>: environment setup, JSDOM config, unusual build steps</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="6">
<span class="icon">✅</span>
<span><strong>Validation steps</strong>: <em>"Always run lint before committing tests"</em></span>
</div>

---

<!-- .slide: data-background="#16213e" -->

## Common Pitfalls ⚠️

<div class="two-col" style="margin-top:0.5em; font-size:0.9em;">

<div>

**🔍 The Problem**

- Tests don't cover all scenarios
- Tests pass but are semantically wrong
- Copilot defaults to wrong framework
- Vague prompts → basic happy-path only
- Tests trusted without verification

</div><!-- .element: class="fragment fade-right" -->

<div>

**✅ The Fix**

- Ask *"What's missing?"* to find gaps
- **Run the tests** + review logic manually
- Set imports manually; use custom instructions
- Be explicit: edge cases, errors, validation
- Always run + lint + scan generated code

</div><!-- .element: class="fragment fade-left" -->

</div>

<br>

<div class="callout warn fragment fade-up">
⚠️ <strong>Golden rule:</strong> Copilot is a tool, not a replacement. A passing test that doesn't catch real bugs is worse than no test.
</div>

Note: The most dangerous pitfall is a test that looks correct, passes, but wouldn't actually catch a real bug. Always ask yourself: if I introduced a bug, would this test fail?

---

<!-- .slide: data-background="#0f3460" -->

## The Coding Agent for Testing 🤖

<div class="icon-text fragment fade-up" data-fragment-index="1">
<span class="icon">📝</span>
<span>Assign a GitHub Issue: <em>"Improve test coverage for the payments module"</em></span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="2">
<span class="icon">🤖</span>
<span>Coding Agent <strong>autonomously</strong> creates a PR on a <code>copilot/</code> branch</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="3">
<span class="icon">✅</span>
<span>Validates with your <strong>tests and linters</strong> in an ephemeral environment</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="4">
<span class="icon">🔒</span>
<span>Built-in security: <strong>CodeQL</strong>, secret scanning, dependency checks</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="5">
<span class="icon">💬</span>
<span>Review the PR → iterate via comments → merge when satisfied</span>
</div>

<br>

<div class="callout fragment fade-up" data-fragment-index="6">
💡 Works best in <strong>well-tested codebases</strong> — the agent learns from your existing test patterns.
</div>

Note: The coding agent excels at low-to-medium complexity tasks. It consumes GitHub Actions minutes plus Copilot premium requests. You can also create a custom "Testing Specialist" agent in `.github/agents/` that focuses exclusively on test quality.

--

<!-- .slide: data-background="#0f3460" -->

### Custom Testing Agent

Define a specialized agent in `.github/agents/testing-specialist.md`:

```markdown
# Testing Specialist Agent

You are a Senior QA Engineer focused on test coverage.

## Guidelines
- Generate comprehensive unit tests with edge cases
- Use table-driven tests when possible
- Follow the AAA pattern (Arrange, Act, Assert)
- Mock all external dependencies
- Target >80% branch coverage
- Flag untested code paths

## Tools
- Read and search the codebase
- Edit test files only (not production code)
- Run test commands
```

<br>

> *"Custom agents are specialized helpers — they capture expertise that persists across conversations."* <!-- .element: style="font-size:0.75em; opacity:0.8" -->

---

<!-- .slide: data-background="#1a1a2e" -->

## Copilot Spaces for Testing 🔬

Organize task-specific context for better suggestions:

<div class="icon-text fragment fade-up" data-fragment-index="1">
<span class="icon">📁</span>
<span>Create a Space including: the module being tested + current test suite + coverage reports</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="2">
<span class="icon">💬</span>
<span><em>"What test cases are missing in payments.test.js based on the logic in payments.js?"</em></span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="3">
<span class="icon">🎯</span>
<span><em>"Write a unit test for the refund logic, following the structure in the existing test suite."</em></span>
</div>

<br>

<div class="callout fragment fade-up" data-fragment-index="4">
💡 Spaces let you curate <strong>exactly</strong> the context Copilot needs — no noise, no guessing.
</div>

Note: This is the evolution of "open relevant tabs." Spaces formalize context curation so you get consistent, high-quality test suggestions every time.

---

<!-- .slide: data-background="#16213e" -->

## Framework Tips 🔧

<div class="three-col" style="margin-top:1em; font-size:0.9em;">

<div>

### Python

**pytest / unittest**

- Generates `TestCase` with `setUp()`
- `assertRaises()` for exceptions
- `unittest.mock.Mock` for deps
- Open existing tests in adjacent tab

</div><!-- .element: class="fragment fade-right" -->

<div>

### TypeScript

**Jest / Vitest**

- Matches project test patterns
- JSDOM env auto-detection
- Self-corrects config issues
- `describe` / `it` / `expect` style

</div><!-- .element: class="fragment fade-up" -->

<div>

### E2E

**Playwright**

- Stable locators: `getByRole()`
- Page Object Model
- `*.spec.ts` naming
- MCP server built-in

</div><!-- .element: class="fragment fade-left" -->

</div>

<br>

<div class="callout fragment fade-up">
💡 <strong>Universal tip:</strong> Set your imports manually at the top of the test file — this signals your framework preference to Copilot.
</div>

---

<!-- .slide: data-background="#1a1a2e" -->

## Context Engineering 🧠

The meta-skill that makes everything else work

<br>

<div class="icon-text fragment fade-up" data-fragment-index="1">
<span class="icon">🧹</span>
<span><strong>Start fresh</strong> — new chat session for each task. Stale context = bad tests.</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="2">
<span class="icon">📋</span>
<span><strong>Custom instructions</strong> persist context between sessions without polluting the chat.</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="3">
<span class="icon">🤖</span>
<span><strong>Custom agents</strong> capture specialized testing expertise that persists across conversations.</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="4">
<span class="icon">🗂️</span>
<span><strong>Copilot Spaces</strong> organize the exact context Copilot needs for each task.</span>
</div>

<br>

<div class="callout fragment fade-up" data-fragment-index="5" style="font-size:1.05em; text-align:center;">
It's <strong>context engineering</strong>, not just prompt engineering.
</div>

Note: The quality of your tests is directly proportional to the quality of context you provide. Master this and everything else falls into place.

---

<!-- .slide: data-background="linear-gradient(135deg, #1a1a4e 0%, #2d1b69 50%, #0d1117 100%)" -->

## Key Takeaways 🚀

<ol class="action-plan">
<li class="fragment fade-up" data-fragment-index="1">Use <strong><code>/tests</code></strong> + open relevant files — start generating tests today</li>
<li class="fragment fade-up" data-fragment-index="2">Try <strong>TDD with Copilot</strong> — write tests first, let agent mode implement</li>
<li class="fragment fade-up" data-fragment-index="3">Craft <strong>specific prompts</strong> — scope, edge cases, error handling, validation</li>
<li class="fragment fade-up" data-fragment-index="4">Set up <strong>custom instructions</strong> — invest once, benefit forever</li>
<li class="fragment fade-up" data-fragment-index="5"><strong>Always verify</strong> — run tests, review logic, check for real bug-catching ability</li>
</ol>

--

<!-- .slide: data-background="linear-gradient(135deg, #1a1a4e 0%, #2d1b69 50%, #0d1117 100%)" -->

## The Mindset Shift

<br>

<div style="font-size:1.1em; text-align:center;" class="fragment fade-up">

Copilot is not a replacement for testing discipline

It's a **force multiplier** for developers who already care about quality

</div>

<br>

> *"Just like us developers, AI-assisted tools produce bugs. We need the same practices for checking quality — builds, linters, and tests — to catch issues before users do."* <!-- .element: class="fragment fade-in" style="font-size:0.8em; opacity:0.8" -->

---

<!-- .slide: data-background="linear-gradient(135deg, #0d1117 0%, #161b22 40%, #1a1a4e 100%)" -->

## Thank You!

### Questions?

<br>

*Resources:* <!-- .element: style="opacity:0.5; font-size:0.7em" -->

- [Writing tests with GitHub Copilot](https://docs.github.com/en/copilot/using-github-copilot/guides-on-using-github-copilot/writing-tests-with-github-copilot) <!-- .element: style="font-size:0.65em" -->
- [Custom instructions for Copilot](https://docs.github.com/en/copilot/customizing-copilot/adding-repository-custom-instructions-for-github-copilot) <!-- .element: style="font-size:0.65em" -->
- [Copilot Coding Agent](https://docs.github.com/en/copilot/using-github-copilot/coding-agent/best-practices-for-using-copilot-to-work-on-tasks) <!-- .element: style="font-size:0.65em" -->
