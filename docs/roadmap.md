# Roadmap

This document outlines the planned evolution of **Dhātu-Bhāṣā (धातु-भाषा)**.

The roadmap is intentionally **incremental and realistic**.
Clarity, correctness, and learning take priority over speed.

---

## 🟢 Phase 0: Language Design (Current)

**Status: In progress / mostly complete**

Goals:
- define language philosophy
- specify grammar inspiration
- document syntax and semantics
- design type system and memory model
- define RISC-V backend strategy
- document compiler architecture

This phase establishes a stable conceptual foundation.

---

## 🟡 Phase 1: Compiler Bootstrap

Goals:
- choose implementation language (likely Rust)
- implement lexer
- implement parser
- build basic AST
- support minimal programs
- emit intermediate representation

Deliverables:
- `dhatu` compiler executable
- parse-only mode
- clear compiler errors

---

## 🟠 Phase 2: Semantic Analysis

Goals:
- type checking
- scope resolution
- ownership and lifetime validation
- meaningful diagnostics

Deliverables:
- compile-time error detection
- well-formed program validation

---

## 🔵 Phase 3: Code Generation (RISC-V)

Goals:
- IR lowering
- RISC-V instruction selection
- register allocation
- ELF binary emission
- bare-metal execution support

Deliverables:
- runnable RISC-V binaries
- QEMU-based execution
- simple hardware interaction examples

---

## 🟣 Phase 4: Core Runtime & Examples

Goals:
- minimal core library
- memory utilities
- basic I/O abstractions
- documented examples

Deliverables:
- example programs
- embedded / firmware demos
- clear learning path

---

## ⚪ Phase 5: Tooling & Ecosystem

Goals:
- formatter
- linter
- improved diagnostics
- editor support (basic)

Deliverables:
- developer-friendly tooling
- stable formatting rules

---

## 🔮 Phase 6: Additional Architectures

Goals:
- ARM backend
- x86_64 backend
- WASM exploration

Deliverables:
- architecture-agnostic frontend
- multiple backend support

---

## 📌 Non-Goals (For Now)

Dhātu-Bhāṣā explicitly does NOT aim to:
- replace C or Rust
- compete with production languages
- prioritize adoption over correctness
- hide low-level details

---

## 🤝 Community Growth

As the project matures:
- good-first-issue labels will be added
- contribution guidelines expanded
- design discussions documented openly

---

## 📎 Living Document

This roadmap will evolve as:
- implementation progresses
- contributors join
- lessons are learned

Changes will always favor **clarity and transparency**.
