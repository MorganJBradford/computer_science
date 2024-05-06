---
id: direct_memory_mapping
aliases: []
tags: []
---

# Direct Memory Mapping - Secondary Memory to Main Memory
## Secondary Memory
- Permanent programs are stored here.
- During execution, programs are turned into processes.
- Every process is subdivided into equal size pages.
## Main Memory
- Subdivided into equally sized frames.

The process of subdividing processes into pages and then bring them into the main memory is done by the operating system.

Frame size = Page size.

## Direct Memory Mapping - Main Memory to Cache Memory
- The main memory is divided into equally sized blocks.
- These cache memory slots are called cache lines.
- Line size = Block size.

Word: Smallest Addressable Unit of Memory

Byte-Addressable Memory: 1 word = 1 Byte

## Example:
### Main Memory
- Main Memory Size: 64 words i.e. (0, 1, ..., 63)
- Block size: 4 words
- No. of Blocks in MM: 64/4 = 16

| | | | | |
|-|-|-|-|-|
| __1:__ | 0 | 1 | 2 | 3 |
| __2:__ | 4 | 5 | 6 | 7 |
| __3:__ | 8 | 9 | 10 | 11 |
| __...__ | ... | ... | ... | ... |
| __15:__ | 60 | 61 | 62 | 63 |

Natural Log equivalent to Log base 2: $ln(n)\div ln(2) = log_2\ n$\
Natural Log 64 word Calculation: $ln(64)\div ln(2) = 6$\
Log2 64 word Calculation: $log_2\ 64\ = log_2\ 2^6 = 6$

P.A. bits
Physical Address bits
Main Memory is sometimes referred to as physical address space

In this example we have 16 blocks, or $log_2\ 16 = log_2\ 2^4 = 4$ bits to address each block.

If the processor generates the following address: 011111, which word of which block is being addressed?: Block 7, Word 3

If we consider all of the bit places' magnitudes and add up all of the values, we get the following:

$2^5 + 2^4 + 2^3 + 2^2 + 2^1 + 2^0 = 0 + 16 + 8 + 4 + 2 + 1 = 31$

### Cache Memory

- Cache Size: 16 words
- Block size: 4 words
- Line size: 4 words
- No. of Lines in Cache: 16/4 = 4

How many bits are needed to address each line?: $log_2\ 4 = log_2\ 2^2 = 2$ bits

All the main memory blocks can't be assigned to the all the cache lines at once.
Therefore we have to perform mapping, in this case round-robin mapping

#### __Round Robin Mapping (Direct Memory Mapping):__

| Main Memory | | | | | | | | | | Cache Memory |
|-|-|-|-|-|-|-|-|-|-|-|
| __0:__| 0 | 1 | 2 | 3 | $\rightarrow$ | __0:__| 0 | 1 | 2 | 3 |
| __1:__| 4 | 5 | 6 | 7 | $\rightarrow$  |__1:__| 4 | 5 | 6 | 7 |
| __2:__| 8 | 9 | 10 | 11 | $\rightarrow$  |__2:__| 8 | 9 | 10 | 11 |
| __3__| 12 | 13 | 14 | 15 | $\rightarrow$ |__3:__| 12 | 13 | 14 | 15 |
| __4:__| 16 | 17 | 18 | 19 | $\rightarrow$ | __0:__ | 0 | 1 | 2 | 3 |
| __...__| ... | ... | ... | ... | $\rightarrow$ | __...__| ... | ... | ... | ... |

PA Bit Split (6 bit example)

4 bits for the block number, 2 bits for the block/line offset.
The block number can be further split into 2 bits for the tag bits and line number.

Tag Bits: The bits that are used to identify the block in the cache memory.
Line Number: The bits that are used to identify the line in the cache memory.
Block/Line Offset: The bits that are used to identify the word in the block.

# Hardware Implementation
Lesson refers to last question in PYQs part 3.

Tag directory contains as many entries as the number of lines in the cache.
The most important part of the tag directory is the tag bits.
Most, not only, because sometimes a few extra bits are added to the tag bits to store additional information.
Such as the pyq mentioning 1 valid bit and 1 modified bit.
With each cache line their are tag bits, specified by the processor, associated to it.
Generally the generated P.A. bits tag portion is matche with the tag bits associate with the cache line in that particular instance.
If they're equal it a hit, if not it's a miss.

Example:

P.A. bits: 6
Cache has $2^2$ lines
Line bits: 2 bits
Block ofset: 2 bits
Tag bits: 2 bits
P.A. bits are specific to each organization

![[DMM Hardware Implementation (HWI).png]]

Our goal is to compare the generated P.A's tag bits with the cache's tag bits to see if the data is in the cache or not.
In order to do so we need two types of combinational circuits:
- Comparator: Compares the generated tag bits with the cache's tag bits
- Multiplexer: Selects the data from the cache if the data is present
    - The line number bits are used as select lines for the multiplexer
    - All of the tag bits of the same bit place will be given to the corresponding multiplexers as input
    - The number of multiplexers needed will be determined by the number of tag bits
    - Type of the multiplexer (2:1, 4:1, 8:1, etc.) will be determined by the number of lines in the cache
    - The output of the multiplexer will be fed into the comparator which is again chosen based on the tag bits
In this scenario we need a 2 bit comparator and two 4:1 multiplexers working in parallel
Why?
As 2 bits are specified for the tag field, each multiplexer can only read a single bit place.

![[DMM HWI - 6 bit.png]]

The comparator is essentially an XOR gate.
If the generated tag bits and the cache's tag bits are equal, the output of the XOR gate will be 0 (cache miss).
If they're not equal, the output will be 1 (cache hit).

![[DMM HWI - P.A. bits.png]]

If there are:
$n$ tag bits and $l$ lines in the cache
$n(l\cdot 1)$ multiplexers will be used which will work in parallel
Also, a single $n$ bit comparator will be needed.
Therefore, time to find out whether it is a cache hit or miss, or hit latency, is:
Hit Latency = $T_{mux} + T_{n-bit\ comparator}$
Why one? Why not all multiplexers?
The multiplexers are working in parallel, so the time taken by the multiplexer that is the slowest will be the time taken by the entire system.
In numerical problems, $T_{mux}$ is neglected as the time taken by the _n-bit comparator_ is much larger than the time taken by the multiplexer.

Question:
![[DMM HWI - Hit Latency Question.png]]

In the comparator delay, the n stands for the tag bits.
Hit Latency = $8 \cdot 11 = 88 ns$ neglecting the multiplexer delay.

Answer:
![[DMM HWI - Hit Latency Answer.png]]

In direct mapping P.A. bits are divided into three parts:
- Block Number
    - Tag bits
    - Line bits
- Block/Line offset bits

If $b$ bits are assigned for block number.
Main memory has $2^b$ blocks.
Having $l$ line bits means there are $2^l$ lines in the cache.
From the $b$ bits the least significant $l$ bits are the remainder if block number is divided by $2^l$.
If $x$ is the block number than $x \mathbin{\%} 2^l$ is the line number.

![[DMM - P.A. bit Diagram.png]]

For example, suppose we have a cache with 4 lines and these are the block requests made by the processer in the specific order:
"7, 8, 6, 10, 11, 14"

Conflict miss is the biggest disadvantage of direct memory mapping as show cased in the second example in the following image.

![[DMM HWI - Disadvantage of DMM.png]]
