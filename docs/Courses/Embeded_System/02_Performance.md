# Performance Issue

## Design for Performance

[TODO]

## Microprocessor Speed

Technique for speed:

- Pipelining
	- Perform all stage simultanaeusly
	- eg. fetch the next instruction while decoding current instruction
- Branch Prediction [TODO]
- Superscalar execution
	- execute multiple instruction that are independent simulutaneously rather just a single
- Data flow analysis [TODO]
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


[TODO time command]
