# Programming Languages Principles

## Introduction

###Objective

- Structure of programming language
- Declarative programming language
- Building complier

### Material

- In-class exercise every two weeks (scored)
- Zoom for class
- Discord for discussion


### Evolution of Programming Language

1. Machine Language: Sequence of raw instructions
2. Assembly language: 1-1 correspondant to (1) but with mnemonic
3. Machine independent language:
	- Natural language and mathematical formula

### Many choices of language

Each language contains different features such as

- structured programming
- OOP

Some are design for special purpose eg. Lisp, C, Prolog

#### Factor affecting popularity

Popularity depends on

- Expressive power: Can the algorithm be easily expressed
- Ease of use: Easy to learn?
- Ease of implementation: Cost, Compatibility
- Standardization: Interpolability of the components
- Open Source
- Complier and tools
- Economic, Patronage, Inertia

### Classification of Programming Language

- Imperative
	- Von Neumann: Variable assignment
	- Scripting: Ran the input as-is. No compilation step
	- Object-Oriented: Object manages state and logic. Use interactio between objects
- Declarative
	- Rather than defining step-by-step instructions. The rules are defined and the runtime resolve the rules

### Program Translation

- Compiler
	- generate machine code once which can then be run
	- fast due to no compilation
- Interpreter
	- Read the code line by line and execute
	- Runtime type
	- Slower due to runtime translation
- Combination of compiler and interpreter
	- Translate source code into intermediate, machine-indepentent program
	- Interprete the intermediate code in virtual machine
- Just-in-Time Translation
	- compilation cost time but frequent bytecode translation also cost time
	- JIT will analyse bytecode that are frequently ran and precompile it
	- From analysing the running program, Machine code can be rearrange to obtain better performance.
	- Why not pre-compile it? because that would defeat portability.
	- How about precompile it on user's machine? they would be upset at startup time

### Extra

How does single-stepping work in compiled language (eg. GDB)? 
The debugger insert an invalid instruction at the target breakpoint.
When the execution reach the breakpoint, it will trigger an interupt.
The debugger can then restore the instruction.

