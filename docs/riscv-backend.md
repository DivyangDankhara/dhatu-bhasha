This document makes Dhātu-Bhāṣā real at the hardware level.
It explains why RISC-V is the first target and how the language maps to it.

As requested, below is the entire file written end-to-end, ready for you to download, save, and commit.

# RISC-V Backend

Dhātu-Bhāṣā is designed as a **RISC-V–first systems programming language**.

This document explains:
- why RISC-V is the primary target
- what assumptions the language makes about the hardware
- how Dhātu-Bhāṣā maps to RISC-V concepts
- how future architectures will be supported

---

## 🎯 Why RISC-V?

RISC-V is an ideal first target for Dhātu-Bhāṣā because it is:

- open and royalty-free
- clean and orthogonal in design
- minimal yet extensible
- widely used in research, embedded systems, and education
- well-suited for bare-metal and OS-level programming

RISC-V’s simplicity aligns naturally with Dhātu-Bhāṣā’s goals of **explicitness and clarity**.

---

## 🧭 Target Profile

Initial target:

- Architecture: **RISC-V**
- Mode: **64-bit**
- Base ISA: `RV64I`
- Extensions:
  - `M` (integer multiplication/division)
  - Optional future support for `A`, `F`, `D`

This profile may evolve, but early development assumes a **simple, well-defined core**.

---

## 🧱 Execution Model

Dhātu-Bhāṣā assumes a **bare-metal–friendly execution model**.

- No operating system is required
- No runtime initialization is hidden
- Startup code is explicit
- The programmer controls memory layout

OS-hosted execution will be supported later as a layer on top of this model.

---

## 📦 Registers

Dhātu-Bhāṣā exposes RISC-V registers conceptually but safely.

Key principles:
- Registers are not implicitly manipulated
- Register usage is deterministic
- Inline access is explicit and marked unsafe

Conceptual mapping:

| RISC-V Register | Purpose |
|---------------|--------|
| x0 | constant zero |
| x1 | return address |
| x2 | stack pointer |
| x10–x17 | argument / return registers |
| x5–x7, x28–x31 | temporaries |
| x8–x9, x18–x27 | saved registers |

Direct register manipulation requires explicit unsafe context.

---

## 🔌 Memory-Mapped I/O (MMIO)

Dhātu-Bhāṣā fully supports memory-mapped I/O.

Example (conceptual):

```sanskrit
असुरक्षित {
    स्मृति[0x80000000] = १;
}


Rules:

MMIO access is always unsafe

Addresses are explicit

No abstraction hides the underlying load/store

This allows:

device drivers

embedded firmware

hardware experimentation

🧮 Instruction Mapping

Dhātu-Bhāṣā does not attempt to expose assembly directly by default.

Instead:

high-level constructs map predictably to RISC-V instructions

there is no hidden control flow

instruction selection is deterministic

For example:

arithmetic → ADD, SUB, MUL

branching → BEQ, BNE, BLT

memory access → LW, SW, LD, SD

Advanced users may opt into inline assembly later.

⚠️ Unsafe Hardware Operations

Hardware-level operations require explicit intent.

Examples:

CSR access

interrupt configuration

register manipulation

direct memory writes

These must be wrapped in:

असुरक्षित {
    // hardware operation
}


This makes low-level code:

visible

auditable

isolated from safe logic

🧠 Calling Convention

Dhātu-Bhāṣā follows the standard RISC-V calling convention:

arguments passed via registers when possible

stack used when registers are exhausted

return values in designated registers

caller/callee-save rules respected

This ensures:

interoperability with other RISC-V code

predictable performance

compatibility with existing toolchains

🛠️ Backend Strategy

The compiler backend strategy is:

Parse Dhātu-Bhāṣā source

Lower into an intermediate representation (IR)

Generate RISC-V code directly or via LLVM

Emit:

ELF binaries

or raw binaries for bare-metal use

Early versions may rely on LLVM for correctness and speed of development.

🔮 Future Architectures

RISC-V is the reference architecture.

Future backends may include:

ARM (AArch64)

x86_64

WASM (experimental)

The front-end language design is architecture-agnostic.
Only the backend changes.

📌 Summary

The RISC-V backend provides:

a clean, open hardware target

direct access to memory and registers

predictable code generation

a foundation for bare-metal systems programming

By targeting RISC-V first, Dhātu-Bhāṣā stays true to its goal:
clarity, control, and openness from grammar down to silicon.