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
  <li v-click>Part 1: Writing code was always the hard part.</li>
  <li v-click>Part 2: Agents move the work but do not obviate the need for it.</li>
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
    <div class="rebar-sticker">Many megabytes of report!</div>
    <img src="/rebar_report.png" alt="Rebar report screenshot" />
  </div>
</div>

---
layout: statement
---

# Part 1: Writing code was always the hard part

---

# TODO Writing code was slooow

- Maybe some math on WPM vs lines of code per day?
- Maybe the rough heuristic that an engineer can at most produce 500-1,000 lines of high-quality code in a very good day?

---

# What writing code used to force

<ol class="mt-10 space-y-4 text-2xl leading-normal">
  <li v-click>Decide intent.</li>
  <li v-click>Discover the shape of the problem while implementing.</li>
  <li v-click>Turn boundaries into interfaces and contracts.</li>
  <li v-click><strong>Human care as first-pass QA.</strong></li>
</ol>

---

# The slowness was load-bearing

<ul class="mt-10 space-y-4 text-2xl leading-normal">
  <li v-click>You wrote tests against interfaces wherever you could.</li>
  <li v-click>You noticed bad boundaries because you had to cross them.</li>
  <li v-click>You noticed missing cases because you had to wire the path end to end.</li>
  <li v-click>You noticed bad database queries because as you wrote them.</li>
</ul>

---

# TODO There was a natural equilibrium

Of implementation speed vs thought required for a task.

---

# For a tech lead, software development was always stochastic

<ul class="mt-10 space-y-4 text-2xl leading-normal">
  <li v-click>You don't know how a team will implement a service.</li>
  <li v-click>You don't know exactly how the monitoring works.</li>
  <li v-click>You don't manually review every database query for efficiency.</li>
</ul>

---

# TODO boxes and stochastic movement graphic

---

# TODO In summary

TODO a summary of the slow and stochastic process that used to be building software.

---

# Game: Data storage system

<div v-click class="h-full flex items-center justify-center">
  <img
    src="/storage_system.png"
    alt="Diagram of comprehensive tests comparing a legacy storage system to a new object storage and KV store system"
    class="max-h-[95%] max-w-full object-contain"
  />
</div>

---

# Game: Data storage system

<div v-click class="h-full flex items-center justify-center">
  <img
    src="/kv_store_results.png"
    class="max-h-[95%] max-w-full object-contain"
  />
</div>

---
layout: statement
---

# Part 2: Agents move the work but do not obviate the need for it

---

# Models crossed a usefulness threshold

<div class="threshold-images">
  <img
    v-click
    src="/41-vs-opus46.png"
    alt="Comparison of model 4.1 and Opus 4.6"
    class="threshold-shot threshold-shot-models"
  />

  <img
    v-click
    src="/arc-prize-leaderboard.png"
    alt="ARC Prize leaderboard"
    class="threshold-shot threshold-shot-arc"
  />
</div>

---

# Models write better code when you do the lead work

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>Tell it what success means.</li>
  <li v-click>Show it the parts of the system that matter.</li>
  <li v-click>Give it the shape of the solution.</li>
  <li v-click>Determine up-front how you will know if the change worked.</li>
</ul>

<div v-click><strong>These are the same things humans need to build good software. But we lost the slow process of discovery.</strong></div>

---

# Intent: make the decision first

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>Say what behavior should change.</li>
  <li v-click>Say what must keep working.</li>
  <li v-click>Say which tradeoff you want.</li>
  <li v-click>In the limit, prompts become math-like.</li>
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

# A checklist for managing ~~an army of interns~~ AI agents

---

# Game: Contrafact

---

# What I told you

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>Writing code used to force a lot of design thinking to happen implicitly.</li>
  <li v-click>Agentic coding requires that thinking to be explicit.</li>
  <li v-click>Everyone now has to do more of the tech lead parts.</li>
  <li v-click>The loop is still the same: specify intent, preserve invariants, verify behavior, operate safely.</li>
</ul>

---
layout: statement
---

# Code got cheap

<div v-click>Correctness did not.</div>

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

:global(.threshold-images) {
  position: relative;
  height: 430px;
  margin-top: 1rem;
}

:global(.threshold-shot) {
  position: absolute;
  display: block;
  left: 50%;
  top: 50%;
  max-width: 94%;
  max-height: 420px;
  transform: translate(-50%, -50%);
  border: 10px solid #fff8ee;
  border-radius: 12px;
  background: #fff8ee;
  object-fit: contain;
  box-shadow: 0 20px 38px rgba(63, 52, 43, 0.30);
}

:global(.threshold-shot-models) {
  z-index: 1;
  height: 410px;
}

:global(.threshold-shot-arc) {
  z-index: 2;
  width: 94%;
}
</style>
