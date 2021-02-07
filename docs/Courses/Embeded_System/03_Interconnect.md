## Computer Components

### von Neuman Architecture

In the old day, the computer were "programmed" by connecting wire and modules. Then came the idea of
stored-program computer. where the program and the data are both stored and address in the same manner.
This simplified the architecture and allow flexibility of reprogramming without redesigning the whole computer.

The idea is said to be discovered in Turing's Universal Turing Machine.

### Components

- CPU
	- Instruction interpeter
	- ALU
- Main Memory
- I/O Module: Manage IO device and multiplex
- System Bus

### Registers

- Memory Address Register (MAR): next memory address to read
- Memory Buffer Register (MBR): Data read or written to memory
- IO Address Register (I/O AR): similar to above
- IO Buffer Register (I/O BR): similar to above
- Program Counter (PC): Address of next instruction to be executed
- Instruction Register (IR): Store intruction retrieved
- Accumulator (AC): Store intermediate ALU result (so that we won't touch Main Memory)

### Instruction Cycle

1. Fetch Cycle
	1. send PC to MAR
	2. Fetch to MBR
	3. Set IR to MBR
2. Execute Cycle: perform tasks such as
	- I/O
	- Memory
	- Data Processing
	- Control

#### Instruction Format

Each instruction may consisted of

- Opcode: Action to do
- Address: Target memory address (eg. to save/load data from)

Instruction width maybe less than the memory width. In that case, we need to handle
read and PC accordingly.

### Instruction Cycle State Diagram

1. Instruction fetch
2. Instruction operation decoding
	- Operand address calculation
	- Operand fetch
3. Data Operation
	- Operand address calculation
	- Operand store
4. Instruction address calculation for next instruction

> **SIMD (Single Instruction Multiple Data)** is when single instruction can operate on many data.
> This eliminate needs to decode instruction multiple time by doing address calculation and operand fetch 
> multiple times in step 2 and 3

## Interrupts

Instead of polling we can use interrupt to wait for events

- Program: Overflow, Illegal Access
- Timer
- I/O
- Hardware failure

### Effect of I/O duration

When the I/O duration is short, using interupt completely eliminate wait time of I/O device.

When the I/O duration is long such that the user programs issued the second I/O operation
while the first I/O operation is not finished, so the second I/O operation is stalled and wait for the first operation to complete.
Using interupt still helps because user's instructions between the two I/O call are run in paralell with I/O wait.

### Prioritised interrupt

One may choose to process only single interupt at any time by disabling interupt during interupt handling,
but this may disregard priority of interupts and increase wait time.

To fix this, One can let enable interrupt while other interupt are running for interupt that have
have higher priority. Note that if lower priority interupt is issued, it must wait until the current interupt is completed.

## I/O Function

I/O modules allow connection with external devices. It can be read or written to by processor like
a memory, but I/O address will refers to device port rather than memory cell.

It may be possible to allow I/O module to communicate with Memory directly.
This is callled **Direct Memory Access(DMA)**

## Bus

A bus is a communication line shared by multiple devices.

If we connect each components point to point. there will be many wires.
So we have them share the bus instead

Bus that connects major component, **System Bus**, consists of following kind of lines

- Data Bus: Transfer data between components
- Address Bus: Select source or target address
- Control Bus: Signal timing, Bus request/grant, Operation (read/write) selection

### Bus Interconnect Scheme

Bus maybe connect in multiple layers [TODO].

#### Bus Type

- Dedicated: Real physical wire [TODO Harvard Architecture]. Usually for CPU and Cache
- Multiplexed: Shared address and data lines

#### Arbitation

Manage who can use bus

- Centralized
- Distributed

#### Timing

- Synchronous
- Asynchronous: No need to wait for clock

##### Timing Diagram

#### Bus width

#### Data Transfer Type

- Byte/Word transfer: one byte per one address request
- Block Data Transfer (Burst Mode): Multiple bytes per single request

### Typical North/South bridge

The bus is split into two major zone

- Northbridge (Fast component)
	- CPU
	- Memort slot
	- GPU (PCI-e)
- Southbridge
	- PCI
	- Hard Disk

### Point-To-Point

In modern system, Bus can get congested so we have pairwise connection
between components instead such as QPI. It has following features

- Multiple Direct Connection: Direct connection between components
- Layered Protocal: Like in TCP/IP, Layered protocal allow for routing, throttling, and error correction.
- Packetization: Data are sent in packet.
