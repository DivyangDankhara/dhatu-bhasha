# Language Basics

This document introduces the fundamental syntax and structure of **Dhātu-Bhāṣā (धातु-भाषा)**.

It is intended for readers with basic programming knowledge.
**No prior knowledge of Sanskrit is required.**
All Sanskrit terms are explained with clear intent and examples.

---

## 📄 Source Files

- Dhātu-Bhāṣā source files use the extension:
- Source files are UTF-8 encoded.
- Devanagari script is supported and encouraged.
- Tooling may support transliteration in the future, but Devanagari is the canonical form.

---

## 🧱 Program Structure

Every executable program defines an entry-point function named:

```sanskrit
मुख्यः

Programs are composed of:

function definitions

variable declarations

control-flow statements

expressions

Minimal Program
कार्य मुख्यः() {
    मुद्रणम्("नमस्ते संसार!");
}
This is equivalent to a traditional “Hello, World” program.

🔑 Keywords

Dhātu-Bhāṣā uses Sanskrit words as reserved keywords.
Each keyword has a precise meaning and cannot be redefined.

Keyword	Meaning	Comparable Concept
कार्य	function definition	fn, function
मुख्यः	entry point	main
चरः	variable declaration	let
यदि	conditional	if
अन्यथा	alternative branch	else
यावत्	loop (while)	while
विरामः	exit loop	break
अनुवर्तनम्	continue loop	continue
मुद्रणम्	output	print
🔢 Primitive Types

Dhātu-Bhāṣā is statically typed.
All variables have an explicit type.

Type	Meaning
सङ्ख्या	integer
द्रव्य	floating-point number
बूलियम्	boolean
अक्षरम्	character
सूत्र	pointer / reference
Boolean Literals

सत्य → true

मिथ्या → false

📦 Variables

Variables are declared using the keyword चरः.

Syntax
चरः नामः : प्रकारः = मानम्;

Example
चरः संख्या : सङ्ख्या = १०;


Notes:

Variables are immutable by default (mutability will be explicitly marked later).

Type inference may be added in future revisions, but explicit types are preferred.

🧮 Expressions and Operators

Dhātu-Bhāṣā supports standard arithmetic and comparison operators.

Arithmetic Operators
+   -   *   /   %

Comparison Operators
==   !=   <   >   <=   >=


Expressions are:

evaluated eagerly

deterministic

free of hidden side effects

🔁 Control Flow
Conditional Statements
यदि (संख्या > ५) {
    मुद्रणम्("महान्");
} अन्यथा {
    मुद्रणम्("लघु");
}

Looping
यावत् (i < १०) {
    i = i + १;
}


Loop control:

विरामः; → break

अनुवर्तनम्; → continue

🧠 Functions

Functions are declared using कार्य.

Function Definition
कार्य योगः(a : सङ्ख्या, b : सङ्ख्या) : सङ्ख्या {
    प्रतिफलः a + b;
}


(Return semantics, return keyword rules, and expression returns are defined in later documents.)

🧠 Comments

Single-line comments begin with //.

// This is a comment


Multi-line comments may be introduced later.

🛑 Statements and Blocks

Statements end with a semicolon (;)

Blocks are enclosed using { }

Whitespace is not semantically significant

⚠️ Important Notes

Dhātu-Bhāṣā has no garbage collector

Memory management is explicit

Pointer usage is allowed but controlled

Unsafe operations will require explicit syntax

There is no hidden runtime

These topics are explained in detail in:

Grammar mapping

Type system

Memory model documentation

📌 Summary

Dhātu-Bhāṣā prioritizes:

clarity over cleverness

explicit intent over convenience

grammar-driven structure over ad-hoc syntax

This document defines only the surface-level syntax.
Deeper semantics are defined in subsequent documentation.
