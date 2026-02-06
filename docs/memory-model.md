This document explains how Dhātu-Bhāṣā interacts with memory, which is the defining feature of any systems programming language.

As requested, below is the entire file written in one go, ready to download, save, and commit.

# Memory Model

Dhātu-Bhāṣā is a **systems programming language**, and its memory model is designed
to be **explicit, predictable, and safe by default**.

There is **no garbage collector** and **no hidden runtime**.
Every memory-related operation is intentional and visible.

---

## 🎯 Design Goals

The memory model aims to:

- provide direct control over memory
- prevent common memory errors at compile time
- keep runtime overhead at zero
- remain understandable to systems programmers
- make unsafe behavior explicit and isolated

---

## 🧱 Memory Regions

Dhātu-Bhāṣā recognizes the following conceptual memory regions:

### Stack
- Automatically managed
- Used for local variables and function call frames
- Fast allocation and deallocation
- Lifetime is tied to scope

### Heap
- Explicitly managed
- Used for long-lived or dynamically sized data
- Allocation and deallocation are programmer-controlled

### Static / Global Memory
- Fixed location
- Exists for the entire program lifetime
- Used for constants and global state

---

## 📦 Stack Allocation

By default, values are allocated on the **stack**.

```sanskrit
कार्य मुख्यः() {
    चरः x : सङ्ख्या = १०;
}


x exists only within the scope of मुख्यः

Memory is reclaimed automatically when the scope ends

Stack allocation is deterministic

🗄️ Heap Allocation

Heap allocation must be explicit.

Exact syntax will be finalized later, but conceptually:

चरः p : सूत्र = आवंटनम्(सङ्ख्या);


Rules:

All heap allocations must be paired with explicit deallocation

The compiler enforces ownership rules

Memory leaks are treated as compile-time errors where possible

🔗 Ownership

Each value has a single owner responsible for its lifetime.

Rules:

Only the owner may free memory

Ownership can be transferred

Once ownership is moved, the previous owner can no longer access the value

Ownership ensures:

no double free

no use-after-free

no dangling references

🤝 Borrowing and References

Values may be borrowed via references.

चरः r : सूत्र = &x;


Borrowing rules:

Borrows do not outlive the owner

Mutable and immutable borrows cannot conflict

Borrowing is enforced at compile time

Borrowing allows:

safe sharing

zero-cost abstraction

efficient access without copying

🚫 Null and Invalid Memory

Null pointers are not allowed by default.

If optional references are needed, they must be explicit:

चरः p : विकल्प<सूत्र> = शून्य;


This eliminates an entire class of runtime errors.

⚠️ Unsafe Memory Operations

Some operations cannot be statically verified.

Examples:

raw pointer arithmetic

direct hardware register access

memory-mapped I/O

casting between unrelated types

Such operations must be wrapped in unsafe blocks:

असुरक्षित {
    // low-level memory operation
}


Rules:

Unsafe blocks are explicit and visually distinct

Safety boundaries are clear

Unsafe code is isolated and auditable

🧮 Memory Layout and Alignment

Memory layout is:

deterministic

platform-specific but predictable

explicitly controllable when required

Alignment rules follow the target architecture.

Padding is never hidden.
If padding exists, it is documented or explicitly requested.

🔌 Hardware Interaction

Dhātu-Bhāṣā supports:

memory-mapped I/O

direct register access

bare-metal programming

Example (conceptual):

असुरक्षित {
    स्मृति[0x80000000] = १;
}


Such code maps directly to machine instructions with no abstraction overhead.

🛑 Lifetime Guarantees

The compiler enforces:

values are not accessed after their lifetime ends

references do not outlive their owners

memory is released exactly once

Lifetime checking occurs entirely at compile time.

📌 Summary

The Dhātu-Bhāṣā memory model provides:

explicit allocation and deallocation

ownership-based safety

zero-cost abstractions

clear separation of safe and unsafe code

full control over hardware interaction

This model enables safe systems programming
without sacrificing performance or transparency.