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

# Reactions

```javascript {all|3,4,13|6,7,14,15|9,16,10|7,17|all}
import { ref, watchEffect } from 'vue'

console.log("1. Create Signal");
const count = ref(0);

console.log("2. Create Reaction");
watchEffect(() => console.log("The count is", count.value))

console.log("3. Set count to 10");
count.value = 10

/* outputs
1. Create Signal
2. Create Reaction
The count is 0
3. Set count to 10
The count is 10
/*
```
<!--
Reactions atau biasa disebut juga dengan side-effects adalah fungsi yang akan dipanggil ketika sebuah signal berubah.
 -->

---
layout: center
---

# Derivations
Derivations are signals that are derived from other signals.

---

# Derivations

<div class="flex gap-8">

```javascript {all|3,4,5|12|13,15|13,7,8,9,10|15,7,8,9,10|17,18|13,7,8,9,10|15,7,8,9,10|all}
import { ref, watchEffect } from 'vue'

console.log("1. Create Signals");
const firstName = ref("John");
const lastName = ref("Smith");

const fullName = () => {
  console.log("Creating/Updating fullName");
  return `${firstName.value} ${lastName.value}`
};

console.log("2. Create Reactions");
watchEffect(() => console.log("My name is", fullName()))

watchEffect(() => console.log("Your name is not", fullName()));

console.log("3. Set new firstName");
firstName.value = "Jacob";
```

```javascript
/* outputs
1. Create Signals
2. Create Reactions

Creating/Updating fullName
My name is John Smith

Creating/Updating fullName
Your name is not John Smith

3. Set new firstName

Creating/Updating fullName
My name is Jacob Smith

Creating/Updating fullName
Your name is not Jacob Smith
*/
```
</div>

---
layout: center
---

```javascript {7,8,9,10|all}
import { ref, watchEffect, computed } from 'vue'

console.log("1. Create Signals");
const firstName = ref("John");
const lastName = ref("Smith");

const fullName = computed(() => {
  console.log("Creating/Updating fullName");
  return `${firstName.value} ${lastName.value}`
});

console.log("2. Create Reactions");
watchEffect(() => console.log("My name is", fullName()))

watchEffect(() => console.log("Your name is not", fullName()));

console.log("3. Set new firstName");
firstName.value = "Jacob";
```

---
layout: center
---

![signals eco](/signals-eco.png)

[source](https://dev.to/this-is-learning/the-evolution-of-signals-in-javascript-8ob)
