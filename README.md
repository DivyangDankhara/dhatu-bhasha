# Dhātu-Bhāṣā (धातु-भाषा)

**Dhātu-Bhāṣā** is an experimental, open-source **systems programming language**
inspired by **Sanskrit grammar** and **Paninian linguistic principles**.

It explores how an ancient, highly formal grammatical system can inform the design
of a modern, low-level programming language.

The language aims to be:
- ⚙️ **Low-level** like C / Assembly  
- 🧱 **Structured & safe** like Rust / C++  
- 🧠 **Grammar-driven**, using Sanskrit root-based word formation  
- 🚀 **Compiled**, with direct hardware interaction  
- 🔓 **Fully open source**, community-driven  

The initial target architecture is **RISC-V**, with plans to support additional
platforms in the future.

---

## ✨ Why Dhātu-Bhāṣā?

Most programming languages borrow keywords from English and evolve organically.
Dhātu-Bhāṣā instead draws inspiration from **how Sanskrit itself constructs meaning**.

Sanskrit is not just a language — it is a **formal system**:
- Root-based word derivation (धातु / *dhātu*)
- Deterministic grammatical rules (Pāṇini’s sutras)
- Powerful composition via compounds (समास / *samāsa*)
- Clear, unambiguous structure

Dhātu-Bhāṣā applies these ideas to programming language design.

> This is **not** a novelty or localization effort.  
> It is an exploration of grammar-first language design for systems programming.

---

## 🎯 Design Goals

- Predictable, low-level performance
- Direct memory and hardware access
- No garbage collector
- Static typing
- Ownership-based memory safety
- Minimal runtime
- Grammar-driven, deterministic syntax
- Clear mapping between intent and operation
- Strong documentation-first approach

---

## 🧠 Core Concepts

### Dhātu (Root-Based Semantics)
Operations and constructs are built from **root meanings**, not arbitrary keywords.

### Samāsa (Composition)
Complex ideas are expressed by composing simpler roots into meaningful identifiers.

### Paninian Grammar
The language grammar is inspired by the rule-based, ordered, unambiguous structure
of classical Sanskrit grammar.

### Systems First
Dhātu-Bhāṣā is designed for:
- operating systems
- embedded systems
- firmware
- low-level tooling
- hardware-near software

---

## 🧱 Example

```sanskrit
कार्य मुख्यः() {
    मुद्रणम्("नमस्ते संसार!");
}

Roughly equivalent to:

int main() {
    printf("Hello, world!");
}

## 🏗️ Project Status

🚧 **Early design & compiler bootstrap phase**

Current focus:
- Language specification
- Grammar and syntax design
- Type system and memory model
- Compiler architecture
- RISC-V backend planning
- Documentation

There is no stable compiler yet.
The project is intentionally design-first to ensure long-term clarity and correctness.

This prevents confusion and unrealistic expectations.

## 🧭 Target Platforms

- ✅ **RISC-V** (primary, first-class target)
- 🔜 ARM
- 🔜 x86_64
- 🔜 WASM (exploratory)

---

## 📚 Documentation

All documentation lives in the [`docs/`](./docs) directory.

Planned documentation includes:
- Vision & philosophy
- Getting started guide
- Language basics
- Grammar mapping (Sanskrit → programming)
- Type system
- Memory model
- RISC-V backend details
- Compiler design
- Roadmap

Sanskrit knowledge is **not required**.
All concepts are explained in plain English.

---

## 🤝 Contributing

Contributions are welcome.

You do **not** need:
- prior Sanskrit knowledge
- compiler experience

You **can** contribute as:
- a systems programmer
- a compiler engineer
- a language designer
- a documentation writer
- a curious learner

Contribution guidelines will be added soon.

---

## 📜 License

This project is licensed under the **Apache License 2.0**.  
See the [`LICENSE`](./LICENSE) file for details.

---

## 🌱 Philosophy

> Ancient grammar.  
> Modern hardware.  
> Open future.
