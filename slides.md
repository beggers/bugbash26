---
theme: seriph
title: Nothing has changed about software development
info: |
  ## Nothing has changed about software development
class: text-left
drawings:
  persist: false
duration: 25min
mdc: true

- How software development historically worked
  - Writing code was never just typing
  - It was where a huge amount of design thinking happened
  - As we wrote, we discovered names, data shapes, boundaries, sequencing, error cases, and invariants
  - Code review worked because the diff contained both the implementation and much of the thinking
- The process was always stochastic
  - It felt deterministic when you were deep in the implementation weeds
  - Zoom out far enough and software was always probabilistic: humans made guesses, missed context, introduced regressions, and learned from feedback
  - Reliability always came from preserving codebase invariants, not from every individual change being obviously correct
  - I did not understand this when I was mostly focused on getting my own code to work
- What the uber tech lead was already doing
  - Historically you might have one very senior tech lead for 50 more junior engineers
  - That person could not think through every line themselves
  - They thought through interfaces, contracts, ownership boundaries, failure modes, observability, and rollout safety
  - They made the system hard to misuse and easy to verify
- What changed in the last year
  - Models crossed a usefulness threshold
  - They can generate whole changes, not just snippets
  - Code became cheap enough to generate, reject, regenerate, and throw away
  - The workflow moved from writing the implementation to specifying, generating, evaluating, and iterating
- What that does to cognition
  - Less thinking happens while manually laying out the code
  - More thinking has to happen before generation: what do I mean, what is allowed, what is forbidden?
  - More thinking has to happen after generation: did the result preserve the intent?
- The game
  - I describe the prompt
  - I describe the system the human had in mind
  - The audience guesses what the AI generated
  - The reveal is funny; the lesson is what the prompt, interface, test, or monitor failed to constrain
- Game examples
  - Pando/turtle KV thing: wrong system shape
  - Rebar tests: tests matched the form but not the intent
  - Contrafact UUID soft-linking: plausible abstraction, broken identity model
- What stayed the same
  - Correctness is still expensive
  - Intent is still hard to communicate
  - Interfaces still determine what changes are easy, safe, and obvious
  - Tests still encode what we care about
  - Monitoring still catches what review and tests miss
- How to think about AI-generated code
  - Treat the model like a very fast, context-limited junior engineer
  - Do not try to scale by reviewing every generated line
  - Scale by designing better prompts, APIs, types, invariants, evals, dashboards, and rollback paths
- Closing claim
  - Software development has not meaningfully changed
  - What changed is that everyone now has to do the tech lead parts
  - For the average engineer, the job feels very different
  - But the important process is the same: specify intent, preserve invariants, verify behavior, operate safely

---

# Nothing has changed about software development

Reliability lessons for an era of agentic AI tools

<div class="mt-12 text-xl opacity-80">
Ben Eggers

BugBash 2026
</div>

---
layout: statement
---

# An entertaining anecdote to start the talk

A recent story of an AI being dumb.

---
layout: two-cols
layoutClass: gap-12 items-center
---

<!--
Replace this placeholder with an image when ready, for example:
<img src="/me.jpg" alt="Ben speaking" class="h-110 w-full object-cover rounded-2xl shadow-xl" />
-->

<div class="h-110 w-full rounded-2xl border border-black/15 bg-white/45 shadow-xl flex items-center justify-center">
  <div class="text-center opacity-60">
    <div class="text-4xl font-bold">Photo</div>
    <div class="mt-3 text-lg">your picture goes here</div>
  </div>
</div>

::right::

# Hello I am Ben

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>SRE Extraordinaire</li>
  <li v-click>Infrastructure @ OpenAI</li>
  <li v-click>Former translator, former therapist, PCT hiker, trumpet player</li>
</ul>

---

# A disclaimer: the economics of working at a frontier lab

---

# What I'm going to tell you

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>How software development actually used to work</li>
  <li v-click>something something AI models</li>
  <li v-click>Why software development has not changed</li>
</ul>

---

# Game: Pando

---

# Part 1: How software development used to work

---

# Game: Rebar

---


# Part 2: What's different now

---

# AI models are better than they were a year ago

<div class="mt-12 grid grid-cols-2 gap-10">
  <ul class="space-y-4 text-2xl leading-normal">
    <!-- Left-column bullets -->
  </ul>

  <ul class="space-y-4 text-2xl leading-normal">
    <!-- Right-column bullets -->
  </ul>
</div>

---
layout: statement
---

# Game: Contrafact

---

# Part 3: Nothing new under the sun

---

# What I told you

---
layout: statement
---

# Questions?


<style>
:global(:root) {
  --slidev-theme-primary: #b84e37;
}

:global(.slidev-layout) {
  background:
    radial-gradient(circle at 12% 15%, rgba(184, 78, 55, 0.16), transparent 30%),
    radial-gradient(circle at 88% 85%, rgba(37, 85, 124, 0.14), transparent 35%),
    #f8f1e8;
  color: #24201b;
}

:global(.slidev-layout.cover) {
  background:
    radial-gradient(circle at 12% 15%, rgba(184, 78, 55, 0.16), transparent 30%),
    radial-gradient(circle at 88% 85%, rgba(37, 85, 124, 0.14), transparent 35%),
    #f8f1e8 !important;
  color: #24201b !important;
}

:global(.slidev-layout h1) {
  color: #3f342b;
}

:global(.slidev-layout.cover h1) {
  color: #3f342b !important;
}

:global(.slidev-layout strong) {
  color: #b84e37;
}

:global(.slidev-layout pre) {
  border: 1px solid rgba(63, 52, 43, 0.16);
}

:global(.slidev-layout .rounded) {
  background: rgba(255, 255, 255, 0.46);
  border-color: rgba(63, 52, 43, 0.18);
}
</style>
