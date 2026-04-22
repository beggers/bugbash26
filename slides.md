---
theme: seriph
title: Nothing has changed about software development
info: |
  ## Nothing has changed about software development
  Reliability lessons for an era of agentic AI tools
class: text-left
drawings:
  persist: false
duration: 20min
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

<img src="/bugbash2026.jpg" alt="Ben speaking" class="h-110 w-full object-cover rounded-lg shadow-xl" />

::right::

# Hello I am Ben

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>SRE Extraordinaire</li>
  <li v-click>Infrastructure @ OpenAI</li>
  <li v-click>Prev. 8th-highest 7d token user @ OpenAI</li>
  <li v-click>PCT hiker, trumpet player, former translator, former therapist</li>
</ul>

---

# But first a word from our sponsors

<div class="mt-8 grid grid-cols-6 gap-4">
  <div>
    <img src="/carl.jpeg" alt="Carl" class="aspect-square w-full rounded-lg object-cover shadow-md" />
    <div class="mt-3 rounded border border-black/20 bg-white/55 px-3 py-1.5 text-center text-lg font-semibold">Carl Ross</div>
  </div>

  <div>
    <img src="/friel.jpeg" alt="Friel" class="aspect-square w-full rounded-lg object-cover shadow-md" />
    <div class="mt-3 rounded border border-black/20 bg-white/55 px-3 py-1.5 text-center text-lg font-semibold">Aaron Friel</div>
  </div>

  <div>
    <img src="/gueandre.jpeg" alt="Gueandre" class="aspect-square w-full rounded-lg object-cover shadow-md" />
    <div class="mt-3 rounded border border-black/20 bg-white/55 px-3 py-1.5 text-center text-lg font-semibold">Andrew Guenther</div>
  </div>

  <div>
    <img src="/mario.jpeg" alt="Mario" class="aspect-square w-full rounded-lg object-cover shadow-md" />
    <div class="mt-3 rounded border border-black/20 bg-white/55 px-3 py-1.5 text-center text-lg font-semibold">Mario Camacho</div>
  </div>

  <div>
    <img src="/noah.jpeg" alt="Noah" class="aspect-square w-full rounded-lg object-cover shadow-md" />
    <div class="mt-3 rounded border border-black/20 bg-white/55 px-3 py-1.5 text-center text-lg font-semibold">Noah Lindner</div>
  </div>

  <div>
    <img src="/robbie_bb.jpeg" alt="Robbie" class="aspect-square w-full rounded-lg object-cover shadow-md" />
    <div class="mt-3 rounded border border-black/20 bg-white/55 px-3 py-1.5 text-center text-lg font-semibold">Robbie Ostrow</div>
  </div>
</div>

---

# What I am going to tell you

<div v-click class="mt-12 text-3xl leading-relaxed">
<strong>All the hard parts of building software are still there and are still hard.</strong>
</div>

<ul class="mt-10 space-y-4 text-2xl leading-normal">
  <li v-click>Writing code was always the hard part because it included design work.</li>
  <li v-click>The hard part is still there today.</li>
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

# Game: Rebar


<div class="relative mt-4 h-[430px]">
  <div v-click class="rebar-shot rebar-shot-json">
    <div class="rebar-sticker">Hard-coded JSON!</div>
    <img src="/rebar_json.png" alt="Rebar generated JSON screenshot" />
  </div>

  <div v-click class="rebar-shot rebar-shot-wc">
    <div class="rebar-sticker">A single 24,000-line Rust crate!</div>
    <img src="/rebar_rust.png" alt="Rebar 24k-line crate" />
  </div>

  <div v-click class="rebar-shot rebar-shot-languages">
    <div class="rebar-sticker">Surprise Python!</div>
    <img src="/rebar_languages.png" alt="Rebar language report screenshot" />
  </div>

  <div v-click class="rebar-shot rebar-shot-report">
    <div class="rebar-sticker">Tiny little report!</div>
    <img src="/rebar_report.png" alt="Rebar report screenshot" />
  </div>
</div>

---
layout: statement
---

# Part 1: Writing code was reliability work

---

# What writing code used to force

<ol class="mt-10 space-y-4 text-2xl leading-normal">
  <li v-click>Decide intent.</li>
  <li v-click>Painstaking implementation.</li>
  <li v-click>Discover the shape of the problem.</li>
  <li v-click>Turn boundaries into interfaces and contracts.</li>
  <li v-click>Human care as first-pass QA.</li>
  <li v-click>External feedback: review, tests, rollout, production signals.</li>
</ol>

---

# Humans thought about intent and implementation

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>Someone knew what success was supposed to mean.</li>
  <li v-click>Someone had to reconcile the code with the existing system.</li>
  <li v-click>Someone was accountable for the awkward edge cases.</li>
</ul>

---
layout: statement
---

# Writing code was never just typing

---

# The slowness was load-bearing

<ul class="mt-10 space-y-4 text-2xl leading-normal">
  <li v-click>You wrote tests comprehensively against interfaces wherever you could.</li>
  <li v-click>You noticed bad boundaries because you had to cross them.</li>
  <li v-click>You noticed missing cases because you had to wire the path end to end.</li>
</ul>

---
layout: statement
---

# Writing code was always the hard part

But not because of the typing.

---

# For a tech lead, software development was always stochastic

<ul class="mt-10 space-y-4 text-2xl leading-normal">
  <li v-click>You don't know how a team will implement a service.</li>
  <li v-click>You don't have to know exactly how the monitoring works.</li>
  <li v-click>You don't have to manually review every database query for efficiency.</li>
</ul>

---

# TODO boxes and stochastic movement graphic

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

# Part 2: Agents move the work but do not obviate the need for it

---

# Models crossed a usefulness threshold

---

# Models write better code when you do the lead work

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>Tell it what success means.</li>
  <li v-click>Show it the parts of the system that matter.</li>
  <li v-click>Give it the shape of the solution.</li>
  <li v-click>Determine up-front how you will know if the change worked.</li>
</ul>

---

# Intent: make the decision first

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>Say what behavior should change.</li>
  <li v-click>Say what must keep working.</li>
  <li v-click>Say which tradeoff you want.</li>
  <li v-click>In the limit, prompts become math-like.</li>
</ul>

Bad: "Add soft linking."
Good: "Users can rename objects, but old UUID links must still resolve."

---

# Context: do not hand it the whole world

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>Point to the files that define the pattern.</li>
  <li v-click>Name the code it should copy.</li>
  <li v-click>Call out the weird thing that is there on purpose.</li>
  <li v-click>Tell it what part of the system is off limits.</li>
</ul>

---

# Design pressure: give it rails

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>Define the interface before it invents one.</li>
  <li v-click>Say where the logic belongs.</li>
  <li v-click>Say what data model cannot change.</li>
  <li v-click>Give it as comprehensive a test harness as possible.</li>
</ul>

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

# Code got cheap

Correctness did not.

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

:global(.rebar-shot) {
  position: absolute;
  border: 10px solid #fff8ee;
  border-radius: 14px;
  background: #fff8ee;
  box-shadow: 0 18px 34px rgba(63, 52, 43, 0.28);
}

:global(.rebar-shot img) {
  display: block;
  width: 100%;
  border-radius: 6px;
}

:global(.rebar-sticker) {
  position: absolute;
  top: -1.3rem;
  right: 1.1rem;
  z-index: 2;
  transform: rotate(5deg);
  border: 2px solid rgba(63, 52, 43, 0.24);
  border-radius: 999px;
  background: #ffd95a;
  color: #3f342b;
  font-size: 1.05rem;
  font-weight: 800;
  white-space: nowrap;
  padding: 0.28rem 0.78rem;
  box-shadow: 0 6px 12px rgba(63, 52, 43, 0.18);
}

:global(.rebar-shot-json) {
  left: 0.2rem;
  top: 1.1rem;
  z-index: 1;
  width: 72%;
  transform: rotate(-4deg);
}

:global(.rebar-shot-wc) {
  right: 1.1rem;
  top: 4.9rem;
  z-index: 2;
  width: 56%;
  transform: rotate(7deg);
}

:global(.rebar-shot-languages) {
  left: 1.2rem;
  top: 14.2rem;
  z-index: 3;
  width: 42%;
  transform: rotate(8deg);
}

:global(.rebar-shot-report) {
  right: 3.8rem;
  top: 12.7rem;
  z-index: 4;
  width: 48%;
  transform: rotate(-3deg);
}
</style>
