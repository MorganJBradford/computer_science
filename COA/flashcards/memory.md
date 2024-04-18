---
id: memory
aliases: []
tags:
  - flashcards/memory
---

#flashcards/memory/intro
Memory::The faculty of the brain by which data or information is encoded, stored, and retrieved when needed -- Wikipedia

#flashcards/memory/intro
Unit Table
?
| Prefix | Units | Add Expressions  | Final Expressions         |
|--------|-------|------------------|----------------------------|
| 1 Kilo Unit    | 1000 Unit        | $10^3 <Unit>$ | $10^3 <Unit>$  |
| 1 Mega <Unit>  | 1000 Kilo <Unit> | $10^3 \cdot 10^3$ | $10^6 <Unit>$  |
| 1 Giga <Unit>  | 1000 Mega <Unit> | $10^6 \cdot 10^3$ | $10^9 <Unit>$  |
| 1 Tera <Unit>  | 1000 Giga <Unit> | $10^9 \cdot 10^3$ | $10^{12} <Unit>$ |

#flashcards/memory/intro
# Primary Memory:
?
## It is the main memory of the computer.
## It is volatile memory.
## It is used to store data and instructions that are currently being executed by the CPU.
## It is also known as RAM (Random Access Memory) - Actually called DRAM (Dynamic RAM).
## It is faster than secondary memory.
## It is directly accessed by the CPU.

#flashcards/memory/intro
# Secondary Memory:
?
## It is non-volatile memory | It retains data even when the computer is turned off.
## It is slower than primary memory.
## Bigger in size.
## Cost-effective.
## Semi-Random Accessibility.
## It is used to store data and instructions that are not currently being executed by the CPU.
## It is not directly accessed by the CPU.
## It is also known as hard disk.
### Slower because it is a mechanical device.
#### It has:
##### a spinning disk.
##### a read/write head.
#### The read/write head moves to the location of the data that needs to be read or written.
#### This movement takes time (seek time).

#flashcards/memory/intro
# Cache Memory:
?
## It is a small block of memory that is used to store frequently accessed data.
## It is volatile memory.
## It is faster than primary memory.
## It is directly accessed by the CPU.
## It is also known as SRAM (Static RAM).

#flashcards/memory/intro
Memory Mapping Table:
?
| | | | Cache Memorry Mapping | | Virtual Memory Mapping | |
|-|-|-|-|-|-|-|
| Processor | $\leftrightarrow$ | Cache | $\leftarrow$Words (or blocks)$\rightarrow$ | Main Memory | $\leftarrow Pages \rightarrow$ | Secondary Memory |
| Processor | $\leftarrow$ | -------- | $\rightarrow$ | Main Memory | $\leftarrow Pages \rightarrow$ | Secondary Memory |

#flashcards/memory/cache_memory
## L1 Cache
?
- Embedded in the processor chip.
- Fastest cache memory.
- Smallest in size.

#flashcards/memory/cache_memory
## L2 Cache
?
- Initially incorporated in the motherboard.
- Now embedded in the processor chip.
- Different processor cores have their own L2 caches.
- Used to store data that is frequently accessed which are second in priority and which cannot be incorporated in L1 due to space limitation.

#flashcards/memory/cache_memory
## L3 Cache (Shared Cache)
?
- Embedded in the processor.
- Shared by all cores.
- Largest in size.
- Used to store data that is least frequently accessed.

#flashcards/memory/cache_terms
What is the term for when data is found in the cache memory?::Cache Hit
What is the term for the time taken to access data from cache memory?::Hit Latency
What data structure does the processor use to determine if data is present in the cache memory?::Tag Directory (Data Structure)
What is the term for when data is not found in the cache memory?::Cache Miss
What is the term for the time taken to access data from the main memory?::Miss Latency

#flashcards/memory/other_terms
What is the term for when data is not found in the main memory?::Page fault
What is the term for the time taken to access data from the secondary memory?::Page fault service time
What is the term for when data is found in the main memory?::Page hit

#flashcards/memory/locality
Locality Reference::The data that is accessed once is likely to be accessed again in the near future.
Pinciple of Locality::States that the data that is accessed once is likely to be accessed again in the near future.
Spacial Locality::States that the data that is accessed once is likely to be accessed again in the near future.
Temporal Locality::States that the data that is accessed once is likely to be accessed again in the near future.


#flashcards/memory/direct_memory_mapping
# Direct Memory Mapping - Secondary Memory to Main Memory
## Secondary Memory
?
- Permanent programs are stored here.
- During execution, programs are turned into processes.
- Every process is subdivided into equal size pages.

#flashcards/memory/direct_memory_mapping
# Direcet Memory Mapping - Main Memory to Cache Memory
## Main Memory
?
- Subdivided into equally sized frames.

#flashcards/memory/direct_memory_mapping
What piece of software is responsible for subdividing processes into pages and bringing them into the main memory?::Operating System

#flashcards/memory/direct_memory_mapping
Frame size is equal to what?::Page size?
Page size is equal to what?::Frame size?
What is the smallest addressable unit of memory?::Word
What is the term for when 1 word is equal to 1 byte?::Byte-Addressable Memory

#flashcards/memory/direct_memory_mapping
## Direct Memory Mapping - Main Memory to Cache Memory
?
- The main memory is divided into equally sized blocks.
- These cache memory slots are called cache lines.
- Line size = Block size.

#flashcards/memory/direct_memory_mapping
Given the following values please provide the calculation for determining the number of bits required to address each block.
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
?
In this example we have 64 words, or $log_2\ 64 = log_2\ 2^6 = 6$ bits to address each block.

#flashcards/memory/direct_memory_mapping
Natural Log equivalent to Log base 2::$ln(n)\div ln(2) = log_2\ n$\
Natural Log 64 word Calculation::$ln(64)\div ln(2) = 6$\
Log2 64 word Calculation::$log_2\ 64\ = log_2\ 2^6 = 6$

#flashcards/memory/direct_memory_mapping
P.A. bits
?
Physical Address bits
Main Memory is sometimes referred to as physical address space

#flashcards/memory/direct_memory_mapping #flashcards/memory/dmm_examples
Given the following values, how many bits are required to address each block?
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
?
In this example we have 16 blocks, or $log_2\ 16 = log_2\ 2^4 = 4$ bits to address each block.

#flashcards/memory/direct_memory_mapping #flashcards/memory/dmm_examples
If the processor generates the following address: 011111, which word of which block is being addressed?
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
?
Block 7, Word 3

#flashcards/memory/direct_memory_mapping #flashcards/memory/dmm_examples
If we consider all of the bit places' magnitudes and add up all of the values, we get the following:
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
?
$2^5 + 2^4 + 2^3 + 2^2 + 2^1 + 2^0 = 0 + 16 + 8 + 4 + 2 + 1 = 31$

#flashcards/memory/direct_memory_mapping #flashcards/memory/dmm_examples
Given the following values, how many bits are needed to address each line?
- Cache Size: 16 words
- Block size: 4 words
- Line size: 4 words
- No. of Lines in Cache: 16/4 = 4
?
$log_2\ 4 = log_2\ 2^2 = 2$ bits

#flashcards/memory/direct_memory_mapping
All the main memory blocks can't be assigned to all the cache lines at once.
Therefore we have to perform mapping, in this case round-robin mapping.
?
| Main Memory | | | | | | | | | | Cache Memory |
|-|-|-|-|-|-|-|-|-|-|-|
| __0:__| 0 | 1 | 2 | 3 | $\rightarrow$ | __0:__| 0 | 1 | 2 | 3 |
| __1:__| 4 | 5 | 6 | 7 | $\rightarrow$  |__1:__| 4 | 5 | 6 | 7 |
| __2:__| 8 | 9 | 10 | 11 | $\rightarrow$  |__2:__| 8 | 9 | 10 | 11 |
| __3__| 12 | 13 | 14 | 15 | $\rightarrow$ |__3:__| 12 | 13 | 14 | 15 |
| __4:__| 16 | 17 | 18 | 19 | $\rightarrow$ | __0:__ | 0 | 1 | 2 | 3 |
| __...__| ... | ... | ... | ... | $\rightarrow$ | __...__| ... | ... | ... | ... |

#flashcards/memory/direct_memory_mapping #flashcards/memory/dmm_examples
PA Bit Split (6 bit example)
?
4 bits for the block number, 2 bits for the block/line offset.
The block number can be further split into 2 bits for the tag bits and line number.

#flashcards/memory/direct_memory_mapping
The bits that are used to identify the block in the cache memory.::Tag Bits
The bits that are used to identify the line in the cache memory.::Line Number
The bits that are used to identify the word in the block.::Block/Line Offset

#flashcards/memory/direct_memory_mapping
Byte Chart
?
|        |              |        |
|--------|--------------|--------|
| 1 Byte | 8 bits       |        |
| 1 KB   | 1024 B(ytes) | 2^10 B |
| 1 MB   | 1024 KB      | 2^20 B |
| 1 GB   | 1024 MB      | 2^30 B |


#flashcards/memory/direct_memory_mapping
Given the following values, what is the P.A. bits split?
MM Size: 4GB
Cache Size: 1MB
Block Size: 4 KB
?
MM Size = $4\ GB = 2^2 \cdot 2^{30}\ B = 2^{2+30} B = 2^{32}\ B$
- No. of P.A. bits = $log_2\ 2^{32} = 32$ bits
- Block Size = $4\ KB = 2^2 \cdot 2^{10}\ B = 2^{2+10} B = 2^{12}\ B$
- Block Offset = $log_2\ 2^{12} = 12$ bits
- No. of Blocks in MM = $\frac{2^{32}}{2^{12}} = 2^{32-12} = 2^{20}$
- Block number bits = $log_2\ 2^{20} = 20$ bits
- Cache Size = $1\ MB = = 1 \cdot 2^{20}\ B = 2^{20}\ B$
- No. of Lines in Cache = $\frac{2^{20}}{2^{12}} = 2^{20-12} = 2^8$
- No. of Tag Bits: P.A. bits - (Line no. bits + offset) = $32 - (8 + 12) = 32 - 20 = 12$ bits

#flashcards/memory/direct_memory_mapping
What is a Tag Directory?
?
- A data structure that helps the processor find out whether the data is present in the cache memory or not.
- Primarily keeps the record of the Tag bits, cache line-wise.
- No. of entries = No. of Cache lines.

#flashcards/memory/direct_memory_mapping
Given the following values, what is the tag directory size?
MM Size: 4GB
Cache Size: 1MB
Block Size: 4 KB
?
- Tag Directory Size = No. of entries $\cdot$ Tag bits = $2^8 \cdot 12 = 3072$ bits

#flashcards/memory/direct_memory_mapping
Given the following values, what is the number of tag bits?
MM Size: 256 MB
Cache Size: 512 KB
Block Size: 256 B
Word Size: 1 Byte
?
- Tag bits: Identifies the MM block residing in the Cache Line.
- MM Size = $256\ MB = 2^8 \cdot 2^{20}\ B = 2^{8+20} B = 2^{28}\ B$
- Cache Size = $512\ KB = 2^9 \cdot 2^{10}\ B = 2^{9+10} B = 2^{19}\ B$
- No of Tag Bits: $log_2({2^{28}}\div{2^{19}}) = 9$ bits

#flashcards/memory/direct_memory_mapping
Given the following values, what is the cache size?
Byte-Addressable MB Size: 16 GB
Block Size: 16 KB
No. of Tag bits: 10
?
MM Size = 16 GB = $2^4 \cdot 2^{30}\ B = 2^{4+30} B = 2^{34}\ B$
No. of P.A. bits = $log_2\ 2^{34} = 34$ bits
Block Size = 16 KB = $2^4 \cdot 2^{10}\ B = 2^{4+10} B = 2^{14}\ B$
Block Offset = $log_2\ 2^{14} = 14$ bits
No. of Line Number Bits: P.A. Bits - (tag bits + offset) = 34 - (10 + 14) = 34 - 24 = 10 bits
No. of Cache Lines = 2^10
Line Size = 2^14 B
Cache Size = 2^10 $\cdot$ 2^14 B = 2^24 B = 16 MB

#flashcards/memory_and_interfacing
# Memory Interfacing:
?
- Part of Computer Organization.
  - Deals with the way of connecting various level of Memory units to Processor & I/O peripherals.
  - The speed of the processor is counted using the unit MIPS.

#flashcards/memory_and_interfacing
What does MIPS stand for?::Million Instructions Per Second

#flashcards/memory_and_interfacing
Method 1 of interfacing:
?
## CPU is connected to all levels of memory simultaneously.
## When the CPU wants to access the data, it will check in all levels of memory.

### If we have memory units: M1, M2, M3
### Acces Time:
#### T1, T2, T3
##### T1 < T2 < T3
### Hit Ratio:
#### H1, H2, H3
##### H1 > H2 > H3
This is know as what?
?
### Effective/Average Memory Acces Time (T_{avg}):
#### $H_1 T_1 + ((1-H_1)\cdot H_2) T_2 + ((1-H_1) \cdot (1-H_2))T_3$
^ Because the memory units are connected to the CPU simultaneously, which is why these checks will run in parallel.
- So, the time taken to access the data will be the time taken to access the data from the memory unit which has the highest hit ratio.
     > Total no. of Instructions = 100
     > No. of Instructions found in nth level = 80
     > MM's Hit Ratio = 80/100 = 0.8 = 80%


#flashcards/memory_and_interfacing
Method 2 of interfacing:
?
## CPU is connected to only one level of memory at a time.
## When the CPU wants to access the data, it will check in the memory unit which is connected to the CPU.
### Effective Memory Access Time (T avg):
#### $H_1T_1 + ((1-H_1) \cdot H_2) (H_1+T_2) + ((1-H_1) \cdot (1-H_2)) (H_1+T_2+T_3)$

#flashcards/memory_and_interfacing
### A cache memory needs an access time of 30 ns and main memore of 150 ns, what is the average access time of CPU (assume hit ration = 80%)?
?
#### Solution 1:
Assume both the cache and main memory are simultaneously connected to the proccesor.
| Access Time | Hit Ratio |
|-------------|-----------|
| $T_{cache} = 30 \ ns$ | $H_{cache}$ = 80% = 0.8 |
| $T_{MM} = 150 \ ns$ |
| $T_{avg} = H_{cache}T_{cache} + (1-H_{cache})T_{MM} \\ = 0.8 \cdot 30 + (1-0.8)\cdot150 \ ns \\ = 24 + 0.2 \cdot 150 = 54\ ns$ |
#### Solution 2:
Assume only one memory unit is connected to the CPU at a time.
- Level wise organization
| Access Time | Hit Ratio |
|-------------|-----------|
| $T_{cache} = 30 \ ns$ | $H_{cache}$ = 80% = 0.8 |
| $T_{MM} = 150 \ ns$ |
| $T_{avg} = H_{cache}T_{cache} + (1-H_{cache})(T_{cache}+T_{MM})$ |
| $= 0.8 \cdot 30 + (1-0.8)(30+150) \ ns$ |
| $= 24 + 0.2 \cdot 180 = 24 + 36 = 60\ ns$ |

#flashcards/memory_and_interfacing
### Assume that for a certain processor, a read request takes 50 ns on a cache miss and 5 ns on a cache hit.
Suppose while running a program, it was observed that 80% of the processor's read requests result in a cache hit.
The average read access time in ns is:
?
| Access Time | Hit Ratio |
|-------------|-----------|
| $T_{cache}+T_{MM} = 50\ ns$ | $H_{cache}$ = 80% = 0.8 |
| $T_{cache} = 5\ ns$ |
| $T_{avg} = H_{cache}T_{cache} + (1-H_{cache})(T_{cache}+T_{MM})$ |
| $= 0.8 \cdot 5 + (1-0.8)\cdot 50\ ns$ |
| $= 4 + 0.2 \cdot 50 = 4 + 10 = 14\ ns$ |


## Memory Hierarchy: Access Time | Size
?
1. Registers
2. S.R.A.M
3. Main Memory (D.R.A.M)
4. Secondary Memory

## Memory Hierarchy: Cost | Usage Frequency
?
1. Secondary Memory
2. Main Memory D.R.A.M
3. S.R.A.M
4. Registers
