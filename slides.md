---
theme: seriph
title: Congratulations, you are now a tech lead
info: |
  ## Congratulations, you are now a tech lead
class: text-left
drawings:
  persist: false
duration: 25min
mdc: true

- Junior vs senior engineers
  - Junior engineers write code that works
  - Senior engineers define the sandbox and interfaces etc
- Things are different now
  - Models are better
  - Token economics are different
- This changes software development and management:
  - We no longer do the cognitive effort that historically came with writing code
  - But we still have to do cognitive effort!
  - But where is the bedrock upon which we can do that cognitive effort?
    - Well, it's still code. But the interfaces and types are much much more important, and the implementation is much much less important.
    - Models are still very bad at interface and API design.
- Game
  - Pando/turtle kv thing
  - Rebar tests
  - Contrafact UUID soft-linking
  - 
- Hot takes
  - Code review is half-dead: only review interfaces and schemas.
  - Really good test harnesses are much more important now. Correctness is stochastic, which has always been true for engineering leaders.

---

# Informal Methods

Reliability lessons for an era of agentic AI tools

<div class="mt-12 text-xl opacity-80">
Ben Eggers

BugBash 2026
</div>

---
layout: statement
---

# The robot and the service.

A recent story of an AI being dumb.

<!--
-->

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

# What I'm going to tell you

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>Why this talk is interesting now but previously wasn't</li>
  <li v-click>The strange token economics of working at an AI lab</li>
  <li v-click>Some other things</li>
</ul>

---



# Formal methods: an informal definition

---

# Informal methods: an informal definition

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

# The token economics of working at an AI lab

Maybe the future, maybe tulip madness

---
layout: statement
---

# Good news: We are no longer code-scarce

---

# Bad news: We are still human-attention-scarce

---

# Accessible bedrock truth is no longer code

---

# Some informal methods still work. Some don't.


---

# Code review is dead

---

# Monitoring is not dead

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
