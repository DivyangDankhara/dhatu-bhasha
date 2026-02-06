This document explains how Dhātu-Bhāṣā is compiled, end to end.
It’s essential for contributors and sets you up for future implementation work.

As requested, here is the entire file written in one go, ready to download, save, and commit.

# Compiler Design

This document describes the overall **compiler architecture** of
**Dhātu-Bhāṣā (धातु-भाषा)**.

The compiler is designed to be:
- simple to understand
- modular and extensible
- suitable for experimentation
- friendly to new contributors

The goal is correctness and clarity first, performance second.

---

## 🎯 Design Principles

The compiler follows these principles:

- **Design before optimization**
- **Explicit stages with clear responsibilities**
- **Readable intermediate representations**
- **Minimal magic**
- **Easy backend extensibility**

The compiler is not intended to be a monolithic black box.

---

## 🧱 High-Level Pipeline

The Dhātu-Bhāṣā compiler follows a traditional multi-stage pipeline:



Source (.sk)
↓
Lexer
↓
Parser
↓
Semantic Analysis
↓
Intermediate Representation (IR)
↓
Backend (RISC-V / LLVM)
↓
Binary Output


Each stage operates on well-defined input and output structures.

---

## 🔤 Lexer

The lexer is responsible for:

- reading UTF-8 source files
- recognizing tokens
- handling Devanagari characters correctly
- identifying keywords, identifiers, literals, and symbols

### Lexer Characteristics

- Unicode-aware
- Whitespace-insensitive (except where required)
- No grammar logic
- Produces a token stream for the parser

The lexer does **not** enforce grammatical correctness beyond token boundaries.

---

## 🌳 Parser

The parser consumes tokens and produces an **Abstract Syntax Tree (AST)**.

Responsibilities:
- enforce syntactic rules
- recognize program structure
- produce meaningful error messages

### Grammar Style

- deterministic
- context-free
- inspired by structured languages (C / Rust)
- grammar rules are explicit and minimal

Paninian inspiration applies to **structure and ordering**, not literal reproduction.

---

## 🧠 Semantic Analysis

Semantic analysis validates **meaning**, not syntax.

This stage is responsible for:
- type checking
- name resolution
- scope management
- ownership and borrowing validation
- lifetime checking
- mutability rules

Errors detected here include:
- type mismatches
- invalid memory access
- use-after-move
- lifetime violations

This stage ensures the program is **safe and well-formed**.

---

## 🧩 Intermediate Representation (IR)

The compiler lowers the AST into an **Intermediate Representation (IR)**.

### IR Goals

- simple
- explicit
- close to machine concepts
- easy to analyze and transform

The IR:
- has explicit control flow
- represents memory operations clearly
- avoids hidden abstractions

Multiple IR forms may exist:
- high-level IR
- lowered IR
- backend-specific IR

---

## 🛠️ Backend Architecture

The backend is responsible for:
- instruction selection
- register allocation
- calling convention adherence
- binary emission

### RISC-V Backend

Initial backend targets RISC-V directly or via LLVM.

Responsibilities:
- map IR operations to RISC-V instructions
- respect RISC-V ABI
- emit ELF or raw binaries
- support bare-metal execution

---

## 🔁 LLVM Integration (Optional)

Early versions of the compiler may use LLVM as a backend.

Benefits:
- mature optimization passes
- existing RISC-V support
- faster development
- easier experimentation

LLVM is treated as an **implementation detail**, not a dependency of the language design.

---

## 🧪 Testing Strategy

Compiler correctness is validated through:

- unit tests for lexer and parser
- semantic analysis tests
- IR-level tests
- backend code generation tests
- golden-file comparisons

Testing is essential to language stability.

---

## 🧰 Tooling

Planned tools include:
- formatter
- linter
- language server (future)
- RISC-V emulator integration

Tooling will evolve alongside the compiler.

---

## 🤝 Contributor Entry Points

New contributors can start with:
- improving documentation
- writing grammar tests
- extending error messages
- implementing small language features
- improving RISC-V backend support

Compiler internals are intentionally readable.

---

## 📌 Summary

The Dhātu-Bhāṣā compiler is designed to be:

- modular
- explicit
- approachable
- extensible

It prioritizes **understanding over cleverness** and **correctness over speed**.

This design enables Dhātu-Bhāṣā to grow as both:
- a research project
- a practical systems language