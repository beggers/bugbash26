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

<!--
Working spine:
- Main claim: code got cheap; correctness did not.
- The talk is not "AI is dumb." The talk is "the missing constraint still matters."
- Each game should reveal one reliability lesson:
  1. Pando: the prompt/interface allowed the wrong system shape.
  2. Rebar: the tests matched the form but not the intent.
  3. Contrafact: a plausible abstraction broke the identity model.
- Closing move: agentic coding makes more engineers responsible for tech-lead work:
  specifying intent, preserving invariants, verifying behavior, and operating safely.
-->

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
  <li v-click>Former translator, former therapist, PCT hiker, trumpet player</li>
</ul>

---

# Disclaimer: The economics of working at a frontier lab

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>Frontier labs are a massively leveraged bet on AI model quality.</li>
  <li v-click>Therefore it is ~always rational to add more leverage.</li>
  <li v-click>This is not true of every software business.</li>
</ul>

---

# What I am going to tell you

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
  <div class="rounded-lg border border-black/15 bg-white/50 p-6">
    <div class="text-sm uppercase tracking-wider opacity-60">Step 1</div>
    <div class="mt-4 text-2xl font-bold">I show the prompt</div>
  </div>

  <div class="rounded-lg border border-black/15 bg-white/50 p-6">
    <div class="text-sm uppercase tracking-wider opacity-60">Step 2</div>
    <div class="mt-4 text-2xl font-bold">You guess the failure</div>
  </div>

  <div class="rounded-lg border border-black/15 bg-white/50 p-6">
    <div class="text-sm uppercase tracking-wider opacity-60">Step 3</div>
    <div class="mt-4 text-2xl font-bold">We name the missing constraint</div>
  </div>
</div>

<div v-click class="mt-12 text-3xl leading-normal">
The reveal is funny. The lesson is what the system failed to constrain.
</div>

---

# Game 1: Pando

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

<!--
This is the "wrong system shape" example.
Keep the setup short. The audience does not need every implementation detail.
They need enough context to see that the prompt/interface allowed the wrong shape.
-->

---
layout: statement
---

# Lesson 1: prompts are interfaces

---

# The model did not violate the interface

<div class="mt-10 text-3xl leading-normal">
The interface allowed the wrong system.
</div>

<ul class="mt-10 space-y-4 text-2xl leading-normal">
  <li v-click>Names and examples are part of the API.</li>
  <li v-click>File ownership and data ownership are part of the API.</li>
  <li v-click>"Do the obvious thing" is not a constraint.</li>
</ul>

---
layout: statement
---

# Part 1

How software development used to work

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

# Software was always stochastic

<div class="mt-10 text-3xl leading-normal">
It felt deterministic when we were deep in the implementation weeds.
</div>

<ul class="mt-10 space-y-4 text-2xl leading-normal">
  <li v-click>Humans made guesses.</li>
  <li v-click>Humans missed context.</li>
  <li v-click>Humans introduced regressions.</li>
  <li v-click>Reliability came from layered feedback, not individual certainty.</li>
</ul>

---

# The tech lead pattern

<div class="mt-10 text-3xl leading-normal">
A senior tech lead was never scaling by personally reasoning through every line.
</div>

<ul class="mt-10 space-y-4 text-2xl leading-normal">
  <li v-click>They shaped interfaces and ownership boundaries.</li>
  <li v-click>They protected contracts and invariants.</li>
  <li v-click>They made failure visible through tests, monitors, and rollout plans.</li>
  <li v-click>They made the system hard to misuse and easy to verify.</li>
</ul>

---

# Game 2: Rebar

<div class="mt-8 grid grid-cols-2 gap-8 text-xl leading-normal">
  <div class="rounded-lg border border-black/15 bg-white/50 p-6">
    <div class="text-sm uppercase tracking-wider opacity-60">Prompt</div>
    <div class="mt-4 text-2xl">Paste the request that produced tests which looked right.</div>
  </div>

  <div class="rounded-lg border border-black/15 bg-white/50 p-6">
    <div class="text-sm uppercase tracking-wider opacity-60">Human intent</div>
    <div class="mt-4 text-2xl">Describe the behavior the tests were supposed to protect.</div>
  </div>
</div>

<div v-click class="mt-10 text-4xl font-bold">
Audience question: what did the tests actually reward?
</div>

<!--
This is the "tests matched the form but not the intent" example.
The punchline should be about the evaluation target, not merely "bad generated tests."
-->

---
layout: statement
---

# Lesson 2: tests can pass the wrong thing

---

# Tests encode what we care about

<div class="mt-10 text-3xl leading-normal">
If they encode syntax, the model optimizes for syntax.
If they encode behavior, the model has to preserve behavior.
</div>

<ul class="mt-10 space-y-4 text-2xl leading-normal">
  <li v-click>Good tests make intent executable.</li>
  <li v-click>Weak tests make plausibility executable.</li>
  <li v-click>Generated code is only as good as the feedback loop it is inside.</li>
</ul>

---
layout: statement
---

# Part 2

Why it feels like everything changed

---

# Models crossed a usefulness threshold

<div class="mt-12 grid grid-cols-2 gap-10">
  <ul class="space-y-4 text-2xl leading-normal">
    <li v-click>They generate whole changes, not snippets.</li>
    <li v-click>They can navigate unfamiliar code faster than a human can type.</li>
    <li v-click>They can produce many plausible approaches cheaply.</li>
  </ul>

  <ul class="space-y-4 text-2xl leading-normal">
    <li v-click>Rejecting code became cheap.</li>
    <li v-click>Regenerating code became cheap.</li>
    <li v-click>Throwing code away became cheap.</li>
  </ul>
</div>

---

# The cognition moved

<div class="mt-10 grid grid-cols-3 gap-6 text-xl leading-normal">
  <div class="rounded-lg border border-black/15 bg-white/50 p-6">
    <div class="text-sm uppercase tracking-wider opacity-60">Before</div>
    <div class="mt-4 text-2xl">Thinking while manually laying out the code</div>
  </div>

  <div class="rounded-lg border border-black/15 bg-white/50 p-6">
    <div class="text-sm uppercase tracking-wider opacity-60">During</div>
    <div class="mt-4 text-2xl">Specifying what is allowed, forbidden, and important</div>
  </div>

  <div class="rounded-lg border border-black/15 bg-white/50 p-6">
    <div class="text-sm uppercase tracking-wider opacity-60">After</div>
    <div class="mt-4 text-2xl">Checking whether the result preserved the intent</div>
  </div>
</div>

<div v-click class="mt-12 text-3xl leading-normal">
The thinking did not disappear. It moved out of the typing loop.
</div>

---

# This is why it feels so different

<div class="mt-10 text-4xl leading-normal">
You can now skip the part of the process that used to reveal your own ambiguity.
</div>

<div v-click class="mt-12 text-3xl leading-normal">
The ambiguity is still there. It just lands in code faster.
</div>

---
layout: statement
---

# Part 3

Nothing new under the sun

---

# Reliable software has always needed the same loop

<div class="mt-10 grid grid-cols-2 gap-6 text-2xl leading-normal">
  <div class="rounded-lg border border-black/15 bg-white/50 p-6">
    <strong>Specify intent</strong>
    <div class="mt-3 opacity-80">What are we actually trying to preserve?</div>
  </div>

  <div class="rounded-lg border border-black/15 bg-white/50 p-6">
    <strong>Preserve invariants</strong>
    <div class="mt-3 opacity-80">What must remain true across changes?</div>
  </div>

  <div class="rounded-lg border border-black/15 bg-white/50 p-6">
    <strong>Verify behavior</strong>
    <div class="mt-3 opacity-80">What feedback tells us we are right?</div>
  </div>

  <div class="rounded-lg border border-black/15 bg-white/50 p-6">
    <strong>Operate safely</strong>
    <div class="mt-3 opacity-80">How do we see, contain, and reverse failure?</div>
  </div>
</div>

---

# Game 3: Contrafact

<div class="mt-8 grid grid-cols-2 gap-8 text-xl leading-normal">
  <div class="rounded-lg border border-black/15 bg-white/50 p-6">
    <div class="text-sm uppercase tracking-wider opacity-60">Prompt</div>
    <div class="mt-4 text-2xl">Paste the request that produced the UUID soft-linking abstraction.</div>
  </div>

  <div class="rounded-lg border border-black/15 bg-white/50 p-6">
    <div class="text-sm uppercase tracking-wider opacity-60">Human intent</div>
    <div class="mt-4 text-2xl">Describe the identity model the code needed to preserve.</div>
  </div>
</div>

<div v-click class="mt-10 text-4xl font-bold">
Audience question: which identity was real?
</div>

<!--
This is the "plausible abstraction, broken identity model" example.
The lesson should land on invariants: the abstraction was attractive because it
looked cleaner than the domain, but the domain identity model was the real constraint.
-->

---
layout: statement
---

# Lesson 3: plausible abstractions are dangerous

---

# The abstraction looked cleaner than the domain

<div class="mt-10 text-3xl leading-normal">
But the domain was where the invariant lived.
</div>

<ul class="mt-10 space-y-4 text-2xl leading-normal">
  <li v-click>AI is very good at making plausible shapes.</li>
  <li v-click>Plausible shapes are not the same thing as correct models.</li>
  <li v-click>The review question is not "does this look like software?"</li>
  <li v-click>The review question is "what invariant did this preserve or destroy?"</li>
</ul>

---

# How to think about AI-generated code

<div class="mt-10 text-3xl leading-normal">
Treat the model like a very fast, context-limited junior engineer.
</div>

<ul class="mt-10 space-y-4 text-2xl leading-normal">
  <li v-click>Do not try to scale by reviewing every generated line.</li>
  <li v-click>Scale by improving prompts, APIs, types, tests, evals, dashboards, and rollback paths.</li>
  <li v-click>The leverage is in the constraints around generation.</li>
</ul>

---

# A practical checklist

<div class="mt-10 grid grid-cols-2 gap-8 text-xl leading-normal">
  <div class="rounded-lg border border-black/15 bg-white/50 p-6">
    <div class="text-2xl font-bold">Before generation</div>
    <ul class="mt-5 space-y-3">
      <li>Name the invariant.</li>
      <li>Name the allowed files and ownership boundary.</li>
      <li>Give one negative example.</li>
      <li>Define what evidence will count as done.</li>
    </ul>
  </div>

  <div class="rounded-lg border border-black/15 bg-white/50 p-6">
    <div class="text-2xl font-bold">After generation</div>
    <ul class="mt-5 space-y-3">
      <li>Read shape before lines.</li>
      <li>Check changed interfaces and data models.</li>
      <li>Run the feedback loop.</li>
      <li>Know how to observe and roll back.</li>
    </ul>
  </div>
</div>

---

# What I told you

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
