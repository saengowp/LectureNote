# Control Flow

## Expression

Smallest execution that produce value.

## Precedence and Associativity

- **Precedence** Priority that binary operator is applied.
- **Associativity** Parentheses rule when the precedence are equal. (LTR or RTL)

### Evaluation Order is not determined by this rule

The precedence and associativity rules only define which binary operator will apply to which value.
The actual order of evaluating for value is not defined.
This is especially important when evaluating a value has side-effect.

## Assignment 

Change value in the memory. This caused side-effect ie. affect later expression.

### Semantic

#### Value model

- **l-value**: refer to location
- **r-value** refer to value

```
a = b + c // a is l-value; b, c are r-value
```

#### Reference model

Both side are l-value. The l-value will be dereference accordingly eg. Haskell. Java Object

## Short-Circuit Evaluation

Language that short-circuit will skip boolean term immediately once the result is known

```
a && b

if a is false. b won't be evaluated
```

## Sequencing

Order of side-effect. eg. top-to-bottom. braces.

## Selection

Allow different code-path to be choosen

if ... else ...

### Short-circuit in selection

Instruction-level optimisation where we store result of term of boolean expression implictly in the control flow instead of in registers.

### Case/Switch statement

Use jump table (map term to line) to immediately goto appropriate instructions.

If the value is to sparse, Binary search may be generated instead

## Iteration

- **Enumeration Controlled** Iterate over a finite set
	- `for _ in 1, 2 ... 9`
- **Logically Controlled** Use bool expr to iterate
	- Pre-test, Post-test, Mid-test Loop
	- ex. `while`

- **True Iterator**: Resumable execution context that will yield loop indices ex. python's generator. This decouple generation of indices of iteration. In fact, it can even be a separate thread.
- **Iterator as object**: Iterator is just a plain object. Manually call `it.next()`. Or maybe syntaxtic sugar like C++

> C For-Loop is a combination loop where we use logically controlled loop (test condition)
> but make the syntax suits for easy enumeration.

## Recursion

Function calling themselves

Loop and Recursion are interchangable. But recursion may cause stack-oveflow

> **Unrelated:** Function is tail-recursive if it immediately return result of another function
> without additionally computing it. Optimizing Complier will be able to optimize this
> kind of function into a stack-less iteration.
> One may use `acc` trick to make function tail-recursive.
