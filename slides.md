---
theme: default
# background: https://source.unsplash.com/collection/94734566/1920x1080
highlighter: shiki
lineNumbers: false
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
drawings:
  persist: false
transition: slide-left
title: 'Reactive JavaScript: Unveiling the Magic of Signals'
layout: image
image: https://media.tenor.com/v9sdELSzVw4AAAAC/nyan-cat-kawaii.gif
---

---
layout: statement
---

# 2020

---
layout: image
image: /intro-by-solid.svg
---

---
layout: center
class: text-center
---

<img src="/knockoutjs-logo.png" alt="ko js" width="500" />

---
layout: center
class: text-2xl
---
<img src="/knockoutjs-logo.png" alt="ko js" width="200" />

`Observable` (state)

`Computed` (side-effect)

`PureComputed` (derived state)

---
layout: statement
---

# Fine-Grained Reactivity

---
layout: cover
---

<h1 class="bg-teal c-gray-900 p-2">
  Reactive JavaScript: Unveiling the Magic of Signals
</h1>

<div class="absolute bottom-10">
  <span class="c-gray-500 dark:c-white">
    kalwabed @ jogjajs, 17 June 2023
  </span>
</div>

---
layout: two-cols
---

<div class="mt-8">
  <h1 class="!text-5xl !pt-8 font-bold">
    Kalwabed Rizki
  </h1>

  <div class="dark:c-gray-400 c-gray-500">
    <p>
      Software Engineer, VNT
    </p>
    <p>
      Instructor, Alterra Academy
    </p>
  </div>

  <div class="flex gap-4 items-center mt-10">
    <ph-globe class="c-gray-500" />
    <a href="https://www.kalwabed.xyz">kalwabed.xyz</a>
  </div>
  <div class="flex gap-4 items-center my-4">
    <ph-instagram-logo class="c-gray-500" />
    <a href="https://www.instagram.com/kalwabed">kalwabed</a>
  </div>
  <div class="flex gap-4 items-center">
    <ph-twitter-logo class="c-gray-500" />
    <a href="https://twitter.com/kalwabedrzk">kalwabedrzk</a>
</div>

</div>

::right::

<img src="/kalwabed.jpeg" alt="profile" class="rd-full w-52 mt-10 ml-auto ring-4 ring-yellow-500" />

---
layout: statement
---

# Signals is reactive

---
layout: section
---

# What is Reactive Programming?

---
layout: quote
---

> # "The essence of functional reactive programming is to specify the dynamic behavior of a value completely at the time of declaration"
> Heinrich Apfelmus, via Michel Weststrate

---
layout: quote
---

> # "Reactive Programming is a declarative programming paradigm built on data-centric event emitters."
> Ryan Carniato, in "What the hell is Reactive Programming anyway?"

---
layout: center
class: text-center text-sm
---

![paul reative blog](/paul-reactive-blog.png)

[https://paulstovell.com/reactive-programming](https://paulstovell.com/reactive-programming)


---
layout: statement
---

# Imagine we're in 2051

---

# Analyze the code

```js
var foo = 10;
var bar = foo + 1;
foo = 11;
bar = foo + 1;
```

`foo` and `bar` are brothers. `bar` is dependent on `foo` for support.

When `foo` changes, `bar` does not.

`foo` had to stabilize the relationship between them again, and it wouldn't be for long.

<style>
  code {
    @apply text-xl
  }
</style>

---
layout: statement
---

# We are still in 2051
and someone has discovered something called **destiny operator**.

---

# What if we can write code like this?
with **destiny operator**.

```javascript
var foo = 10;
var bar <== foo + 1;
foo = 20;
Assert.AreEqual(21, bar);
```

Some say that when the compiler encounters code that changes `foo`, it inserts the corresponding change for `bar`, such that they are always in sync.

<style>
  code {
    @apply text-xl
  }
</style>

---
layout: section
---

# In simple terms
"I have no time. Please explain it to me like I'm five."

---
layout: center
---

# Reactive programming

```javascript
a = b + c
```

The value of `a` will change every time the value of `b` or `c` variable changes.

<style>
  code {
    @apply text-xl
  }
</style>


---
layout: section
---

# So, what does this have to do with Signals?

---

# Signals
Signals are the main players in what is called the reactive system.

It consists of a:
- getter
- setter
- value

---
layout: statement
---

# Some say that at its core, Signals is an event emitter.
But the key difference is how it manages its subscriptions.

---
layout: section
---

# Signals are not built alone
We have partner in crime called **Reactions** and **Derivations**.

---
layout: center
---

# Reactions
Reactions are functions that are called when a signal changes.

---
layout: center
---

# Derivations
Derivations are signals that are derived from other signals.

---
layout: center
---

![signals eco](/signals-eco.png)

[source](https://dev.to/this-is-learning/the-evolution-of-signals-in-javascript-8ob)

---
layout: section
---

# What are problems want to solve?

---
layout: center
class: text-2xl
---

Things that are often discussed in the frontend world are usually about performance and rendering.

One of the issues that often comes up when discussing these two things is **how to manage the state**.

---

# How do we manage the state
Traditional global state with React.

<img src="/react-global-state.png" alt="global state tree in react" width="650" />

<!--
Manajemen global state di React umumnya sederhana. Tetapi dengan berjalannya waktu, jumlah komponen semakin banyak maka ini akan menjadi kesulitan tersendiri.
Bisa diakalin dengan memo dan useMemo.
Lagi-lagi, ketika ukuran codebase semakin berkembang maka akan semakin sulit untuk menentukan dimana optimizations harus diterapkan.
 -->

---

# How do we manage the state
Global state with React context.

<img src="/react-with-context.png" alt="global state tree in react with context" width="650" />

<!--
Dengan context yang awalnya prinsipnya betul sederhana tetapi akan chaos ketika ukuran dan jumlah component bertamabah besar.
 -->

---
layout: statement
---
# How do we manage the state with Signals?
It's simple, we don't.

---

# How do we manage the state
with Signals.

<img src="/signals-flow.png" alt="global state tree with signals" width="650" />

<!--
Dengan signal kita memiliki flow dari state yang lebih sederhana. Daripada kita oper sebuah nilai ke component tree, kita oper signal object yang mengandung nilai tersebut.
Cara seperti ini membuat kita bisa mengubah nilai tanpa melakukan re-rendering komponen-komponen yang membawa nilai tersebut.
 -->
