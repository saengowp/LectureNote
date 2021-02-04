# Solving Linear System

The problem of finding the solutions to a linear system or equivalently

- finding pre-images of a transformation
- Finding $x$ that satisfy $\boldsymbol{A}x = b$

can be solved by combining following ideas

## Ideas

1. We can easily read the solution off RRE form
	1. We can find homogenous solutions
	2. We can find a particular solution for non-homogenous system
	3. A solution to non-homogenous system is a sum of particular solution and homogenous soulution
2. We can apply row-operation without changing the solution set
3. Guass-Jordan algorithm can apply row-operation to the matrix and transform it to RRE form

The idea will be explained in details below


### RRE form

**Reduced Row Echelon form** is a form of matrix that we can easily read the solution off.
It must have following properties

- **Pivot in row**: First non-zero entry in all rows is one. This element (1) is called *pivot*
- **Pivot in column**: If there's a pivot in the column, all other elements in that column must be zero
- **South-east pivot**: pivot must be arranged in south-east direction, where the lowest row contains rightmost pivot
- **Zero-sink**: Row with only zeros must be at the bottom

### Solving homogenous system using RRE

**Homogenous System** is an equation of form

$$
\boldsymbol{A}x = \boldsymbol{0} = b
$$

In RRE form, we have columns with pivot (pivot column) and columns with no pivot (free column)

We know that each output element ($b_i$) can be controlled independently by the coefficient of the pivot column ($x_j$). 
and that rows with no pivot would always be zero and doesn't need to be controlled

To make it output 0 ($b_i = 0$ for all $i$), just set the pivot column coeeficient ($x_j$) to the negative of
the linear combination of free columns. This means that if we know free column's coeeficient ($x_j$ where $j$ is free), we can uniquely determine the pivot column's coefficient ($x_j$ where j is pivot).

Let consider *any* solution for the system, we know that it free coeficient can be any value, and that pivot coefficient
is uniquely determined from the free coefficients. So to find *all* solutions, just iterate through all free coefficient.

But how can we iterate through all free coeffiecient? we just write it in term of particular solution to one-hot encoding of each free column.
that is, if we have $x = (p, f, p, p, f, f)$ where p is some solution to the pivots, we write one-hot encoding

$$
x = (p, f_1, p, p, f_2, f_3) = f_1 (p, 1, p, p, 0, 0) + f_2 (p, 0, p, p, 1, 0) + f_3 (p, 0, p, p, 0, 1) 
$$

and that's is the representation of all solutions. it is the image of $R^k \rightarrow R^n$ where $k$ is number of free columns and $n$ is the input of $A$.

### Solving for particular solution of the non-homogenous system using RRE

**Non-homogenous System** is

$$
\boldsymbol{A}x = b
$$

Let's say we have the RRE form of the **augmented matrix**, or the matrix that is formed by concatenation of $\boldsymbol{A}$ and $b$ ($[\boldsymbol{A}|b]$

We can read of the solution by setting pivot coefficient ($x_i$) to equals the output element ($b_i$) and
setting all free coefficient to zero. 
Note that this may not be possible if there is a row that have no pivot (we can't controlled its output) 
and its output is non-zero.

### Solving non-homogenous system

The solution of the non-homogenous system is the sum of a particular solution ($x_p$) and the solution of its homogenous system.

$$
\boldsymbol{A}x = b
$$

$$
b = \boldsymbol{A}(x_p + x^\prime) = b + \boldsymbol{A}x^\prime
$$

$$
0 = \boldsymbol{A}x^\prime
$$

So any solution $x$ must be one-to-one correspond to the homogenous solution $x^\prime$.

### Guass-Jordan algorithm

In order to transform any matrix in to an RRE form, we must use transformation that doesn't change the solution set.
Reversible transformations don't change the solution set
(**proof**: Let $x$ be a solution to the original matrix, we apply the transformation to both the matrix and the output, we see that the equation still holds, Let $x^\prime$ be a solution to the transformed matrix, we apply reverse transform and see that it is the solution to the original matrix. forming one-to-one correspondance)

#### Elementary Row Operation

Elementary row operation are operation of the matrix that preserve solution set because it's reversible.

- Swapping row
- Multiply row by a scalar
- Adding one row to the another

#### Guass-Jordan algorithm

Guass Jordan algorithm perform elementary row operation on the matrix to transform it into RRE form

1. Find pivot-able column. For each column from left to right
	- If all element in the column are zero or all non-zero element are above the previous pivot's row (those row are already in used by pivot) go to next column
	- otherwise swap the row that have non-zero in its column with this row.
2. Use elementary row operation to make all other element in to columns zero (both above and below the pivot)
3. Goto next column and and repeat to step 1

## Some Properties of Mapping

### One-to-one

Mapping is one-to-one if all range has atmost one pre-image. So it must not have free column. otherwise zero will have multiple pre-image. and if it doesn't have free column, then multiple pre-image is impossible. so it if and only if.

This is only possible if column <= row because row number of pivot is limited by minimum of number of row and column. converse is not true.

### Onto

Mapping is onto if all range has atleast one pre-image. So all row must have a pivot, otherwise, row without a pivot will be all zeros and the result would also be only zero making some output impossible. And if all rows have a pivot, then all output has an input. So it is if and only if.

This is only possible if column >= row by the same reason, the converse is not true

### One-to-one and Onto

This is a reversible mapping by definition and it must be a square matrix.

Not all square matrix is reversible. (ex. Zero matrix)

