# D793 — Formal Languages Overview

**Course 1 of 10** · Apr 1 – 10, 2026 · 2 performance tasks

**Time:** 10 calendar days · ~18 hours on WGU work · ~38 hours of outside courses *(from my study journal)*

**How it went:** First course. I was learning to program at the same time, so outside courses took twice as long as the tasks. Each paper went from outline to done in one or two long sessions.

## In one line

I analyzed a small legacy Fortran 90 program. Then I ported it to Python, chose the language on purpose, and validated the port.

## What the course covers

How programming languages are designed and how they differ: procedural vs. functional vs. object-oriented, compiled vs. interpreted, static vs. dynamic typing. It also covers formal semantics (how you prove what code means) and how to choose a language for a business need.

## What I did

- **Analyzed the legacy code.** I classified Fortran: procedural, compiled, array-oriented, still maintained (Fortran 2023; "202y" is next). I explained why weather and HPC shops still run it: fast floating-point math on large arrays.
- **Chose a target language and defended it.** I compared Rust, Julia, and Python. Python won on ecosystem (NumPy, SciPy), hiring pool, and maintainability. Julia was my personal favorite for raw numerical work. Its ecosystem and institutional adoption were the weak points.
- **Tried wrap-and-extend first, then rewrote.** I looked at F2PY and f90wrap to keep the Fortran and call it from Python. The original used a Fortran derived type (`type :: weather`) that carried state. Wrapping it added boilerplate and cross-language debugging. A clean rewrite was smaller and clearer.
- **Rewrote as a Python class.** Fortran derived type → Python class. Fortran `select case` → dictionary lookup. I added input validation the original didn't have, such as array-length checks.
- **Planned the validation.** Regression against the Fortran output, tolerance-based float comparison (`numpy.allclose`), and unit tests in pytest.
- **Used AI and said so.** I used ChatGPT and Codex for first-draft translation and syntax checks, then reviewed and edited every line.

## Skills used

`Python` `classes` `NumPy` `pytest` `Fortran 90 (reading)` `F2PY` `language paradigms` `regression testing` `requirements analysis`

## What I'd do differently

- **I overthought the language choice.** I spent hours on Rust and Julia for about 100 lines of code. Scope the decision to the size of the problem.
- **I'd keep the tests in the repo next to the code.** The tests are the proof the port is correct.
- My early drafts used NumPy and the final one used plain lists. At this size, NumPy wasn't needed. I'd say that out loud and explain the trade-off.

## Key ideas worth knowing

- Syntax vs. semantics
- Operational, denotational, and axiomatic semantics; Hoare triples `{P} C {Q}`; loop invariants
- Compilers: lexer → parser → abstract syntax tree (AST) → semantic analysis → optimization → code generation
- Domain-specific languages (SQL, HTML) vs. general-purpose languages
- Transpilers, and why AI code translation still introduces bugs (see Pan et al. below)

## Books and reading

No single textbook. The course ran on readings and outside courses:

- Nystrom, R. (2021). *Crafting Interpreters*. Genever Benning. ([free online](https://craftinginterpreters.com/))
- Lachaux, M.-A., et al. (2020). *Unsupervised Translation of Programming Languages*. ([arXiv:2006.03511](https://arxiv.org/abs/2006.03511))
- Pan, R., et al. (2024). *Lost in Translation: A Study of Bugs Introduced by Large Language Models while Translating Code*. ([arXiv:2308.03109](https://arxiv.org/abs/2308.03109))
- Aldrich, J. (2019). *Lecture notes: Program semantics*. Carnegie Mellon University. ([PDF](https://www.cs.cmu.edu/~aldrich/courses/17-355-19sp/notes/notes02-semantics.pdf))

## Outside courses I took for this one

I was learning to program during this course. These are the outside courses I finished. WGU students get Udemy, LinkedIn Learning, DataCamp, and Pluralsight through the student portal at no extra cost.

| Course | Platform | Length | Why |
|---|---|---|---|
| Introduction to FORTRAN | LinkedIn Learning | 2h 28m | Taken right before the term |
| How to Become a Programmer | Udemy | 6h | Basics |
| For New Joiners in IT | Udemy | 6h 30m | Apps, APIs, Git, SDLC overview |
| Programming 101 | Udemy | 4h 30m | Basics |
| [Programming Foundations: Fundamentals](https://www.linkedin.com/learning/programming-foundations-fundamentals) | LinkedIn Learning | 3h 11m | Basics |
| [Programming Foundations: Beyond the Fundamentals](https://www.linkedin.com/learning/programming-foundations-beyond-the-fundamentals) | LinkedIn Learning | 3h 6m | In the course material |
| [Parallel and Concurrent Programming with C++ Part 1](https://www.linkedin.com/learning/parallel-and-concurrent-programming-with-c-plus-plus-part-1) | LinkedIn Learning | 2h | In the course material |
| [Java Threads](https://www.linkedin.com/learning/java-threads) | LinkedIn Learning | 1h 14m | In the course material |
| [ChatGPT Masterclass for Programmers](https://www.udemy.com/course/chatgpt-masterclass-for-programmers-and-software-engineers/) | Udemy | 5h | In the course material |
| Back-end Languages | LinkedIn Learning | 2h | Language comparison |
| Artificial Intelligence Foundations: Machine Learning | LinkedIn Learning | 2h | Background |

**Total: about 38 hours.**

## Public rebuild (planned)

Port a public-domain Fortran routine from Netlib to Python, with a pytest suite that checks the Python output against the compiled Fortran. It will go in `rebuilds/` when it's done.
