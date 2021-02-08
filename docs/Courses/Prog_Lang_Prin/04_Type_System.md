# Type System

## Why type?

- Type provides context eg. determine wheter `+` means string concat or summation
- Type restrict nonsense operation
- Type as documentation. It can be check by complier. This may be an obstacle in certain application
- Type known at compile time can be used for optimization


## Common Types

- Scalar: Hold single-valued type eg. real
	- Discrete: Countable values eg. bool, char, int
- Composite: Contruct from one or more type eg. struct, containers

## Type System

Type system consisted of method to define and associate type and *type rules*

### Type checking

**Type Checking** ensure that type rules are followed.

- **Strongly Typed**: Any operation must use appropriate type. note that Python is strongly typed
- **Statically Typed**: Types are determined and check at compile-time
- **Dynamically Type**: Types are determined at run-time

### Type rules

#### Type equivalence

##### Structural Equivalence

If the structure of the record is the same then it's equal

> In C, scalar type uses structural equivalence (think `typedef`) but composite type uses name equivalence

```
data person = {name :: Text, desc:: Text}
data places = {name :: Text, desc:: Text}

same type under structural equivalence
```

##### Name Equivalence

Even if the structure is the same, If it's name is different, it's not the same type.
Except when using inheritance then the type maybe implictly/explicty casted.

##### Type Conversion and Casting

In Explicit cast, we force retyping, depending on languages, some may do following.

- If the types are structuarally equivalence at low-level, then nothing is needed
- If the types have intersected components, then range check should be generated
- If the types are different in low-level but have some correspondance (`float`, `int`) 
then machine instruction may be generated

#### Type Compatibility

Type may need not be equivalence. Language may used implicit type conversion or **Type coersion**.
to allows type to be mixed. eg. `int` to `long`, `pointer` and `array`

##### Universal Reference Type

Type that is compatible with any type eg. `void*` in C, `Object` in Java

#### Type inference

Inference type of an expression.

Some easy cases

- In arithmetic, Infers more general type
- In assignment, Infers from destnation type
- In function call, Infers from return type
