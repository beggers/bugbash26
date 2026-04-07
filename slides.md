---
theme: seriph
title: Informal Methods
info: |
  ## Informal Methods

  A BugBash 2026 talk about which traditional SRE reliability tools still
  work in an era of agentic AI, and which human-review habits stop scaling.
class: text-left
drawings:
  persist: false
duration: 25min
mdc: true
---

# Informal Methods

Reliability lessons for an era of agentic AI tools

<div class="mt-12 text-xl opacity-80">
BugBash 2026
</div>

<!--
The framing: this is not a talk about replacing formal methods. It is about the
informal engineering controls SRE already uses when correctness is too large to
prove locally and too important to leave to vibes.
-->

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

# About me

<ul class="mt-10 space-y-5 text-2xl leading-normal">
  <li v-click>Your name / role</li>
  <li v-click>The reliability scar tissue you bring to this talk</li>
  <li v-click>Why agentic tools are now part of your workflow</li>
  <li v-click>The thing you want the audience to remember about you</li>
</ul>

<!--
These bullet points are placeholders. Each li has v-click so the bullets appear
one at a time while the rest of the deck remains transition-free.
-->

---

# What I'm going to tell you

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
  color: #3f342b;
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
