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
