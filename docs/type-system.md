This document explains how Dhātu-Bhāṣā thinks about types, safety, and correctness.
As before, below is the entire file written end-to-end, ready for you to download, save, and commit.

# Type System

Dhātu-Bhāṣā is a **statically typed systems programming language**.
Its type system is designed to provide **clarity, predictability, and safety**
without hiding the underlying machine.

This document describes the guiding principles and core concepts of the type system.

---

## 🎯 Design Goals

The type system aims to:

- detect errors at compile time
- make data representation explicit
- prevent common memory and logic bugs
- avoid runtime overhead
- remain understandable to systems programmers

Dhātu-Bhāṣā prioritizes **explicitness over convenience**.

---

## 📌 Static Typing

All values in Dhātu-Bhāṣā have a type that is known at compile time.

```sanskrit
चरः संख्या : सङ्ख्या = १०;


Types are checked during compilation

Type mismatches are compile-time errors

There is no dynamic typing

🔢 Primitive Types

The language provides a small set of primitive types.

Type	Description
सङ्ख्या	integer (machine-word sized by default)
द्रव्य	floating-point number
बूलियम्	boolean
अक्षरम्	character
सूत्र	pointer / reference

These types map directly to low-level machine representations.

🧩 Explicit Type Annotations

Type annotations are explicit and mandatory in the core language.

चरः x : सङ्ख्या = ५;


This ensures:

predictable memory layout

simple compiler implementation

readable intent

Limited type inference may be introduced later as an optional convenience, not a requirement.

🧠 User-Defined Types

Complex data structures are defined using वर्गः.

वर्गः बिन्दु {
    x : सङ्ख्या;
    y : सङ्ख्या;
}


Fields have fixed types

Memory layout is deterministic

No hidden padding unless explicitly defined

🔁 Mutability

By default, values are immutable.

Mutability must be explicitly requested (syntax to be finalized).

This rule:

prevents accidental state changes

improves reasoning about code

aligns with ownership-based safety

🧭 Ownership Model (Conceptual)

Dhātu-Bhāṣā follows an ownership-based model inspired by modern systems languages.

Key ideas:

every value has a single owner

ownership can be transferred

references may borrow data temporarily

invalid memory access is prevented at compile time

This model avoids:

garbage collection

reference counting

hidden runtime costs

Detailed borrowing and lifetime rules are defined in the memory model documentation.

🔗 References and Pointers

The सूत्र type represents a pointer or reference.

चरः p : सूत्र = &x;


Rules:

dereferencing is explicit

null pointers are not allowed by default

optional references must be explicitly wrapped

Unsafe pointer operations require explicit syntax and intent.

⚠️ Unsafe Operations

Some low-level operations cannot be fully verified by the compiler.

Examples:

raw memory access

hardware register manipulation

manual pointer arithmetic

Such operations will require explicit unsafe blocks
(to be defined in later documentation).

The goal is to:

isolate unsafety

make risk visible

preserve overall program safety

🧮 Type Conversions

Implicit type conversions are not allowed.

All conversions must be explicit:

चरः y : द्रव्य = परिवर्तनम्(x);


This avoids:

silent precision loss

unexpected behavior

platform-specific surprises

🛑 Error Handling Philosophy

Dhātu-Bhāṣā does not use exceptions.

Instead:

errors are represented explicitly in types

control flow remains visible

failure paths are handled deliberately

Exact error-handling constructs will be defined later.

📌 Summary

The Dhātu-Bhāṣā type system emphasizes:

static verification

explicit intent

predictable layout

minimal runtime cost

It is designed to support safe systems programming
without sacrificing control or performance.

Further details are covered in:

memory model

ownership and lifetimes

unsafe semantics