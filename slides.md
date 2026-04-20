---
theme: seriph
title: Nothing has changed about software development
info: |
  ## Nothing has changed about software development
  Reliability lessons for an era of agentic AI tools
class: text-left
drawings:
  persist: false
duration: 25min
mdc: true
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

# A poll

<!--
- Who has used an LLM to write some code?
- Who has been frustrated with the code an LLM wrote?
- Who has felt that LLMs are bad at understanding intent?
-->

---
layout: two-cols
layoutClass: gap-12 items-center
---

<!--
Replace this placeholder with an image when ready, for example:
<img src="/me.jpg" alt="Ben speaking" class="h-110 w-full object-cover rounded-lg shadow-xl" />
-->

<div class="h-110 w-full rounded-lg border border-black/15 bg-white/45 shadow-xl flex items-center justify-center">
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
  <li>Prev. 8th-highest 7d token user @ OpenAI</li>
  <li v-click>Former translator, former therapist, PCT hiker, trumpet player</li>
</ul>

---

# TODO But first a word from our sponsors

Shout outs to colleagues who helped me sharpen these ideas or from whom I stole anecdotes.

---

# Disclaimer: The economics of working at a frontier lab

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>Frontier labs are a massively leveraged bet on AI model quality.</li>
  <li v-click>Therefore it is ~always rational to add more leverage.</li>
  <li v-click>This is not true of every software business.</li>
</ul>

---

# TODO What I am going to tell you

<div class="mt-12 text-3xl leading-relaxed">
AI changes <strong>where the work happens</strong>.
It does not change <strong>what reliability requires</strong>.
</div>

<ul class="mt-10 space-y-4 text-2xl leading-normal">
  <li v-click>Writing code was always doing design work.</li>
  <li v-click>Agentic tools move that work before and after generation.</li>
  <li v-click>The important job is still: specify intent, preserve invariants, verify behavior, operate safely.</li>
</ul>

---

# The game

<div class="mt-10 grid grid-cols-3 gap-6 text-xl leading-normal">
  <div v-click class="rounded-lg border border-black/15 bg-white/50 p-6">
    <div class="text-sm uppercase tracking-wider opacity-60">Step 1</div>
    <div class="mt-4 text-2xl font-bold">I tell you about the system</div>
  </div>

  <div v-click class="rounded-lg border border-black/15 bg-white/50 p-6">
    <div class="text-sm uppercase tracking-wider opacity-60">Step 2</div>
    <div class="mt-4 text-2xl font-bold">I tell you the prompt</div>
  </div>

  <div v-click class="rounded-lg border border-black/15 bg-white/50 p-6">
    <div class="text-sm uppercase tracking-wider opacity-60">Step 3</div>
    <div class="mt-4 text-2xl font-bold">You guess what I got</div>
  </div>
</div>

---

# Game: Rebar

<div class="mt-10 grid grid-cols-3 gap-6 text-xl leading-normal">
  <div v-click class="rounded-lg border border-black/15 bg-white/50 p-6">
    <div class="text-sm uppercase tracking-wider opacity-60">Step 1</div>
    <div class="mt-4 text-2xl font-bold">The goal: create a drop-in Rust replacement for Python's re module which was demonstrably faster</div>
  </div>

  <div v-click class="rounded-lg border border-black/15 bg-white/50 p-6">
    <div class="text-sm uppercase tracking-wider opacity-60">Step 2</div>
    <div class="mt-4 text-2xl font-bold">The prompt: "Move closer to your goal."</div>
  </div>

  <div v-click class="rounded-lg border border-black/15 bg-white/50 p-6">
    <div class="text-sm uppercase tracking-wider opacity-60">Step 3</div>
    <div class="mt-4 text-2xl font-bold">So: what did I end up with?</div>
  </div>
</div>

---

# TODO Game: Rebar

TODO rebar results

---
layout: statement
---

# Part 1: What writing code used to force

---

# What writing code used to force

<ol class="mt-10 space-y-4 text-2xl leading-normal">
  <li v-click>Decide intent.</li>
  <li v-click>Own the implementation.</li>
  <li v-click>Discover the shape of the problem.</li>
  <li v-click>Turn boundaries into interfaces and contracts.</li>
  <li v-click>Use human care as first-pass QA.</li>
  <li v-click>Add external feedback: review, tests, rollout, production signals.</li>
</ol>

---

# Humans thought about intent and implementation

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>Someone knew what success was supposed to mean.</li>
  <li v-click>Someone had to reconcile the code with the existing system.</li>
  <li v-click>Someone was accountable for the awkward edge cases.</li>
</ul>

---

# Writing code was never just typing

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>We discovered names.</li>
  <li v-click>We discovered data shapes.</li>
  <li v-click>We discovered sequencing, error cases, and invariants.</li>
  <li v-click>We discovered what the existing system was trying to protect.</li>
</ul>

---

# The slowness was load-bearing

<div class="mt-10 text-3xl leading-normal">
When code was expensive to produce, the act of producing it forced a lot of review to happen before review.
</div>

<ul class="mt-10 space-y-4 text-2xl leading-normal">
  <li v-click>You noticed awkward names because you had to use them.</li>
  <li v-click>You noticed bad boundaries because you had to cross them.</li>
  <li v-click>You noticed missing cases because you had to wire the path end to end.</li>
</ul>

---

# For a tech lead, software development was always stochastic

<div class="mt-10 text-3xl leading-normal">
It only felt deterministic because the uncertainty was spread across people and feedback loops.
</div>

<ul class="mt-10 space-y-4 text-2xl leading-normal">
  <li v-click>Design guesses became code.</li>
  <li v-click>Review caught some missing context.</li>
  <li v-click>Tests caught some broken behavior.</li>
  <li v-click>Rollouts and production signals caught what escaped.</li>
</ul>

---
layout: statement
---

# TODO Game: Database-y thing

<div class="mt-8 grid grid-cols-2 gap-8 text-xl leading-normal">
  <div class="rounded-lg border border-black/15 bg-white/50 p-6">
    <div class="text-sm uppercase tracking-wider opacity-60">Prompt</div>
    <div class="mt-4 text-2xl">Paste the smallest exact prompt that sets up the turtle KV example.</div>
  </div>

  <div class="rounded-lg border border-black/15 bg-white/50 p-6">
    <div class="text-sm uppercase tracking-wider opacity-60">Human intent</div>
    <div class="mt-4 text-2xl">Describe the system shape you thought was obvious.</div>
  </div>
</div>

<div v-click class="mt-10 text-4xl font-bold">
Audience question: what system did the model build instead?
</div>

---
layout: statement
---

# Part 2: But models are good now

---

# Models crossed a usefulness threshold

---
layout: statement
---

# What models need to write good software

---

# What models need to write good software

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click><strong>Intent:</strong> what are we actually trying to preserve or change?</li>
  <li v-click><strong>Context:</strong> what existing shapes, constraints, and conventions matter?</li>
  <li v-click><strong>Design pressure:</strong> what boundaries, interfaces, and invariants should guide the change?</li>
  <li v-click><strong>Feedback:</strong> how do we know it worked, got faster, stayed safe, and can be rolled back?</li>
</ul>

<div v-click class="mt-10 text-3xl leading-normal">
Humans used to discover much of this by slowly writing the code.
Models need it made explicit before and after generation.
</div>

---

# Intent: give it decisions

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>State the behavior change, not just the code change.</li>
  <li v-click>Name what must not change.</li>
  <li v-click>Declare the tradeoff you want it to make.</li>
  <li v-click>Include one or two examples that make the desired behavior unambiguous.</li>
</ul>

<div v-click class="mt-10 text-3xl leading-normal">
Bad: “Add soft linking.”<br />
Good: “Users may rename objects, but existing external references by UUID must keep resolving.”
</div>

---

# Context: point at the relevant world

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>Tell it which files are canonical.</li>
  <li v-click>Tell it which existing pattern to copy.</li>
  <li v-click>Tell it which abstraction is load-bearing.</li>
  <li v-click>Tell it what historical weirdness is intentional.</li>
</ul>

<div v-click class="mt-10 text-3xl leading-normal">
Do not dump the repo and hope. Curate the part of the system that explains the change.
</div>

---

# Design pressure: narrow the shape

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>Give it the interface you want to exist.</li>
  <li v-click>Give it the data model it should preserve.</li>
  <li v-click>Give it constraints on where logic belongs.</li>
  <li v-click>Tell it which tempting solution is wrong.</li>
</ul>

<div v-click class="mt-10 text-3xl leading-normal">
The model is very good at filling in a shape. It is much less reliable at inventing the right shape.
</div>

---

# Feedback: make rejection cheap

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>Give it the exact test command.</li>
  <li v-click>Give it the benchmark or eval that matters.</li>
  <li v-click>Ask it to explain what would prove the change wrong.</li>
  <li v-click>Make rollback, dashboards, and production signals part of the work.</li>
</ul>

<div v-click class="mt-10 text-3xl leading-normal">
The model can generate candidates cheaply. Your job is to make bad candidates die quickly.
</div>

---

# Game: Contrafact

---

# TODO What I told you

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>Code got cheap. Correctness did not.</li>
  <li v-click>Writing code used to force a lot of design thinking to happen implicitly.</li>
  <li v-click>Agentic coding makes that thinking explicit: before generation and after generation.</li>
  <li v-click>Everyone now has to do more of the tech lead parts.</li>
  <li v-click>The loop is still the same: specify intent, preserve invariants, verify behavior, operate safely.</li>
</ul>

---
layout: statement
---

# This is easy for simple software systems

This is really really hard for complicated infrastructure systems

---
layout: statement
---

# Questions?


<style>
:global(:root) {
  --slidev-theme-primary: #b84e37;
}

:global(.slidev-layout) {
  background: #f8f1e8;
  color: #24201b;
}

:global(.slidev-layout.cover) {
  background: #f8f1e8 !important;
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
