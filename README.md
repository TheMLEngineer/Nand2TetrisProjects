# Nand2Tetris Projects

My implementation of the **Nand to Tetris** course — building a modern computer from scratch, starting with a single NAND gate.

Based on the book [The Elements of Computing Systems](https://www.nand2tetris.org/) by Nisan and Schocken.

---

## The Core Idea

Every logic gate, every chip, every computer ultimately reduces to one primitive: the **NAND gate**.

```
NAND truth table:
a=0, b=0 → out=1
a=0, b=1 → out=1
a=1, b=0 → out=1
a=1, b=1 → out=0
```

From this single gate, everything else is built — layer by layer.

---

## Project 1 — Boolean Logic

Building the fundamental logic gates using only NAND as the primitive.

| File | Chip | How it works |
|------|------|-------------|
| `Not.hdl` | NOT gate | `NAND(x, x)` — NAND a signal with itself |
| `And.hdl` | AND gate | `NOT(NAND(a, b))` — invert the NAND output |
| `Or.hdl` | OR gate | `NAND(NOT(a), NOT(b))` — De Morgan's law |
| `xor.hdl` | XOR gate | `OR(AND(a, NOT(b)), AND(NOT(a), b))` — one but not both |
| `Mux.hdl` | Multiplexer | `OR(AND(a, NOT(sel)), AND(b, sel))` — select between two inputs |

### Gate Hierarchy

Each gate builds on the ones below it:

```
NAND (primitive — given)
 └── Not
      ├── And
      │    └── Xor
      │    └── Mux
      └── Or
           └── Xor
           └── Mux
```

---

## How to Run

1. Download the [Nand2Tetris software suite](https://www.nand2tetris.org/software)
2. Open the **Hardware Simulator**
3. Load any `.hdl` file
4. Load the corresponding `.tst` test script
5. Run the test and compare output against the `.cmp` file

---

## What I Learned

- **NAND is functionally complete** — any Boolean function can be built from NAND alone
- **De Morgan's Law** in practice: `NOT(a AND b) = NOT(a) OR NOT(b)`
- **Abstraction** — once a chip is built, use it as a black box in the next layer
- **Mux is everywhere** — the select pattern is fundamental to how CPUs choose between operations

---

## Resources

- [nand2tetris.org](https://www.nand2tetris.org/) — official course site
- [Coursera Course](https://www.coursera.org/learn/build-a-computer) — video lectures
- Book: *The Elements of Computing Systems* — Nisan & Schocken
