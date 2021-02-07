# Memory System

## Characteristic

- Location
	- Internal: Register, Main Memory
	- External: Need I/O eg. Hard Disk
- Capacity
- Unit of transfer
	- Word: Natural unit eg. interger length, instruction lenghth, but with many exception such as x86's variable length instruction
	- Addressable Unit: how fine-grain is addressing
	- Unit of transfer: Maybe larger than Word. For external memory, it's block size.
- Method of accessing
	- Sequential access eg. tape
	- Direct access: Access block first, then do sequential searching eg. disk
	- Random access: Main memory
	- Associative: Use comparison and matching eg. cache
- Performance
	- Access time: time from request for address to read/write available eg. seeking time for disk
	- Memory cycle time: time between accesses eg. for DRAM refreshing and system bus signal to be stable
	- Transfer Rate: Time to transfer data (exclude access time)
- Physical characteristic
	- Volatile: lost when power off
	- Nonvolatile: data is still kept when power off
	- Readonly: RO


## Memory Hierachy

Memory has trade-off between speed, capacity and cost so we use them in hierachy.
Hierachy is possible because memory tends to be accessed in cluster (locality of reference), so we can use slower memory in low access frequency region.

- Inboard Memory: Register, Cache, Main Memory; Fast but low capacity
- Outboard Memory: Hard drive, CD
- Off-line Storage: Magnetic Tape

## Virtual Memory

Virtual Memory is a technique where each application doesn't access physical memory directly but
through virtual memory. This hides fragmentation and make it possible use larger than available memory though swapping.

These virtual to physical mapping are translated by Memory Management Unit (MMU).

Cache may be put before MMU translation or after MMU. putting it before MMU make it faster but
one may need to flush cache for each context switch or add application tag to cache line.


## Cache

Cache sit between CPU and memory to alleviate slow memory problem that caused bottle-neck.

When cache-miss occur, The memory block will be transfered to the cache.

Cache may have multiple hierachy (L1, L2, ...) similar to above.

Each cache line contains *tag* (what address it currently cache) and *data* in the block it cached.

### Mapping

#### Direct Mapping

We view main memory address as follows. let say our cache block size is $2^w$, we will store the entire block in the cache.

```
Main memory Address

| Tag        | Line  | Word |
```

If our cache line count is $2^r$ then that line has width of $r$.

If the memory fetch came, we will go to the line specified and check if tag matched.

We can see that each physical block address has a fixed mapping to a line of cache. that's why it's called direct mapping.
It's not flexible as the mapping is fixed and we may use two address with the same cache-line causing frequent eviction
but it's fast and easy to implement.


#### Associative

```
Main memory address

| Tag                | Word |
```

Each lines of cache can store any block of memory. The cache must be able to compare the tag against all cache line's tag
to find cache line location

This causes comparison circuit to be larger but allows any address to be store along each other without restriction.

#### k-way set-associative


Cache lines are divided into multiple sets, each with k lines. 

Address are first directly mapped to a sets. then the tag is
used to find the appropriate cache-line.

```
Main memory address

| Tag  | Set       |  Word |
```

This reduce tag width and allow for fewer comparison of tags (only k comparison).
