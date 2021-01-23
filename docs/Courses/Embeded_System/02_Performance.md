# Performance Issue

## Microprocessor Speed

Technique for speed:

- Pipelining
	- Perform all stage simultanaeusly
	- eg. fetch the next instruction while decoding current instruction
- Branch Prediction
	- Try to predict branch before condition is known then speculatively execute it
- Superscalar execution
	- execute multiple instruction that are independent simulutaneously rather just a single
- Data flow analysis
	- Compile-time optimization to find part of program values propagated
- Speculative execution

## Improvement in Chip organization and Architecture

- Increase hardware speed of processor
- Increase size and speed of cache
- Change organization and architecture

## Problem with clock speed and logic density

- Power: High density logic used more power and causes heat dissipation problem
- RC delay: Higher density logic make wire thinner and closer increasing electron delay due to RC
- Memory latency

## Many Integrated Core. Graphic Processing Core

- MIC: Multicore CPU
- GPU: High pararellism but simpler instruction

## Amdahl's Law

- Processing Time = Processor Time + Non-Processor Time (eg. I/O) 
- Improvement in number of cores can only improve the first term of the RHS by n times 
  and the second term stay the same

## Little's Law

In steady state, Average no. of item being processed in a queue equals
average rate of item ariving multiplied by average time an item spent in the system

## Processor Performance Measure

- CPU Time = CPU Cycle (for the program only) x Cycle Time
- CPI (Cycle Per Instruction) = CPU Cycle / Instruction count
- Execution Time = Time from the wall clock (which include time spent on other program)
- MIPS (Milions of Instruction Per Seconds)
- MFLOPS (Millions of Floating-Point Operation Per Seconds)

**Note:** MIPS and MFLOPS use wall time

## Choosing mean

When measuring performance, we have to choose appropriate mean for different measurement.

The reason we calculated mean is so that we can use the mean to substitute all values it represent in certain calculation.
So to choose the proper mean, the target formula that the mean will be used in must be identified. The formula will be
called *invariant*.

$$
f(x_1, x_2, ...) = f(\bar{x}, \bar{x}, ...)
$$

We then find $\bar{x}$ calculation that satisfy the invariant. This is called Chrisini Mean.

### Mean execution time; Where summation made sense

Invariant should be time, that is, if we execute it $n$ times, then it should took $n \cdot \bar{x}$ seconds.

$$
T = \bar{x} + \bar{x} + ... = x_1 + x_2 + ...
$$

$$
\rightarrow \bar{x} = \frac{\sum{x}}{n}
$$

This is the arithmetic mean

### MFLOPS; mean of rates

We might know amount of instructions (MFLOP, c) and performance (MFLOPS, r). and we want to calculate time.

$$
T = \frac{c}{\bar{r}} + \frac{c}{\bar{r}} + ... = \frac{c}{r_1} + \frac{c}{r_2} + ...
$$

$$
\bar{r} = \frac{n}{\frac{1}{r_1} + \frac{1}{r_2} + ...}
$$

This is called harmonic mean.

### Normalized time; mean of normalized number

This is a bit different. There are **NO** valid mean for normalized number except *geometric mean*

$$
\bar{x} = (x_1 \cdot x_2 \cdot ...)^{1/n}
$$

Because it would make sense that we can compare these normalized number using multiplication eg.

> C took 2 times longer than A and B took 2 times longer than A so C took the same time as A

Only geometric mean could satisfy this multiplicative property.
