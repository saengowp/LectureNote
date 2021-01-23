# Vector

## Numerical Vector

### Proving properties of scalar product

Scalar product can be represented as 1 x m multiply with m x 1 matrix.

Using matrix's properties we can then prove scalar product's. (except commutativity)


### Standard Basic Vector

A unit vector where all component is zero except the specified component.

$$
\boldsymbol{e_1} = (1, 0, 0)
$$

### Eigenvector and Eigenvalue

Because square matrix ($\textbf{A}$) maps from m-vector to m-vecotor. There're some special vectors where

$$
\boldsymbol{Ax} = \lambda \boldsymbol{x}
$$

the vector is only scaled.

- $\lambda$ is called eigenvalue
- $\boldsymbol{x}$ is called eigen vector

## Function

- domain ($X$): all allowed input
- range ($Y$): all allowed output (doesn't need to be mapped to)
- rule ($f$): output single $f(x)$ for every member of $X$

> Note: Even if the rule are the same, different range define different function
> because function is defined by all 3 properties

> Range is allow to be superset of the actual image because it is easier to find

$$
f: X \rightarrow Y
$$

*function* and *mapping* are the same but we usually use *function* for real output
and *mapping* or *transformation* for multiple dimensional ($n>1$) vector

- image of $S$ under $f$ (written $f(S)$) is set of all output resulting from inputing S
- image of $f$ is image with domain of $f$ as input


> Note: Some textbook use the word codomain for range and range/image for image


- Onto: When image fill the entire range
- Pre-image $f^{-1}(S)$: set of input that mapped to some element of $S$
- One-to-one: each point in the range has *atmost* one pre-image
- Inverse function $f^{-1}$: If $f$ is one-to-one and onto, we can define the inverse function

## Mapping and Transformation

**Mapping** or **Transformation** is a function with numerical vector as an input or as an output or both.

Some of the properties that can be asked about mapping

- What's its image?
- Is it onto?
- Is it one-to-one?
- Does it expand or contract? where distance is defined as euclidean distance.
- What's pre-image of a specific vector under this mapping? (solution to the function)

For *linear* mapping, those question can be easily answered. 

Which can be useful, for example, in multivariable calculus, mapping can be approximated as a linear mapping.

## Linearity

Mapping is linear iff

- $f(\boldsymbol{a} + \boldsymbol{b}) = f(\boldsymbol{a}) + f(\boldsymbol{b})$
- $f(k\boldsymbol{a}) = kf(\boldsymbol{a})$

Linear function determine by $\boldsymbol{a}$ is

$$
\boldsymbol{a}^*(\boldsymbol{x}) = \boldsymbol{a} \cdot x
$$

### All linear mapping can be represented by matrix multiplication

All linear mapping can be represented by

$$
f(\boldsymbol{x}) = A\boldsymbol{x}
$$

**Proof** Apply linearity properties to input vector written in form of basis vector. We see that it can be re written as a matrix.
