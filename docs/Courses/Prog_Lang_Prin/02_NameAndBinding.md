# Binding, Storage and Scopes

## Names and Binding

- **Name** symbol respresenting address, function, type, variable etc.
- **Binding** Association between name and thing it names
- **Binding Time**
	- **Static Binding** Bound before runtime eg. compiled language. greater efficiency due to compile time optimization.
	- **Dynamic Binding** Bound at runtime. more flexibility.

## Object Lifetime and Storage Management

### Memory Segment

- **Text Segment** Instructions. Fixed size
- **Data segment** Global, Static, Const variable. Fixed size
- **Stack** Store local variable used by function call. Grows downward
- **Heap** Store dynamically allocated objects. Grows upward

### Stack-based Allocation

When subroutine is called, **Stack frame** (or activation record) is formed consisting of

- Argument
- Return address
- Bookkeeping: save register to be restore later
- Local variables
- Temporaries

**Stack pointer** register storing address of the stack's top. note that stack pointer will move as new local variable is allocated

**Frame pointer** store the frame's reference address so that variable within the frame can be referenced with an offset.

#### Stack Maintainance

1. Caller push argument
2. Caller call subroutine. (push return address)
3. Callee save register and fp
4. Callee execute tasks
5. Callee restore register, fp. deallocate stack (shrink sp)
6. Callee jump to return address
7. Caller deallocate argument it pushed and shrink sp

> **Can SP moves without calling subroutine?**
> Yes. rSP can be moved for several reasons such as when using `alloca()` or variable-length array


### Heap-based allocation

Dynamically allocate by the programmger eg. `malloc()` and cleared manually or by *Garbage Collector*

#### Fragmentation

- **Internal Fragmentation** The size requested is smaller than the block size of the system. So the entire block must be allocate wasting memory.
- **External Fragmentation** Free space is not contiguous to be allocated. Fix by compaction

#### Problem with manual allocation

When binding lifetime and object lifetime are not equal

- **Dangling reference** use after free
- **Memory leak** forget to free

#### Garbage collection

Some language use garbage collection to automatically deallocate unreachable object.

## Scopes

**Scopes** is a program region where no binding change. eg. scope of a variable

**Referencing environment**  is set of binding visible in that statement.

### Static scoping (or Lexical Scoping) 

Static scoping is when scope can be determined at compile-time. usually by curry braces.

To access parent's local variable. we use static link in our stack frame containing parent frame's address and dereference from there. this is called *static chaining*.

> **Note** function declaration's scope is visible in parent scope. otherwise how would we call such function?

### Dynamic scope

In dynamic scoping, the name is resolve at runtime and bind to the most recently executed variable binding. This may be done by storing
each variable's binding as a stack. example of dynamic language are Bash, and C Preprocessor.
