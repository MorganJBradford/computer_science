---
id: memory
aliases: []
tags:
  - flashcards/memory
---

#flashcards/memory/intro
Memory::The faculty of the brain by which data or information is encoded, stored, and retrieved when needed -- Wikipedia

#flashcards/memory/intro
Primary Memory:
?
- It is the main memory of the computer.
- It is volatile memory.
- It is used to store data and instructions that are currently being executed by the CPU.
- It is also known as RAM (Random Access Memory) - Actually called DRAM (Dynamic RAM).
- It is faster than secondary memory.
- It is directly accessed by the CPU.

#flashcards/memory/intro
Secondary Memory:
?
- It is non-volatile memory (retains data even when the computer is turned off).
- It is slower than primary memory.
- Bigger in size.
- Cost-effective.
- Semi-Random Accessibility.
- It is used to store data and instructions that are not currently being executed by the CPU.
- It is not directly accessed by the CPU.
- It is also known as hard disk.
    - Slower because it is a mechanical device.
        - It has:
            - a spinning disk.
            - a read/write head.
        - The read/write head moves to the location of the data that needs to be read or written.
        - This movement takes time (seek time).

#flashcards/memory/intro
Cache Memory:
?
- It is a small block of memory that is used to store frequently accessed data.
- It is volatile memory.
- It is faster than primary memory.
- It is directly accessed by the CPU.
- It is also known as SRAM (Static RAM).

#flashcards/memory/intro
Memory Mapping Table:
?
| | | | Cache Memorry Mapping | | Virtual Memory Mapping | |
|-|-|-|-|-|-|-|
| Processor | $\leftrightarrow$ | Cache | $\leftarrow$Words (or blocks)$\rightarrow$ | Main Memory | $\leftarrow Pages \rightarrow$ | Secondary Memory |
| Processor | $\leftarrow$ | -------- | $\rightarrow$ | Main Memory | $\leftarrow Pages \rightarrow$ | Secondary Memory |

#flashcards/memory/cache
L1 Cache (Primary Cache) facts
?
- Embedded in the processor chip.
- Fastest cache memory.
- Smallest in size.

#flashcards/memory/cache
L2 Cache (Secondary Cache) facts
?
- Initially incorporated in the motherboard.
- Now embedded in the processor chip.
- Different processor cores have their own L2 caches.
- Used to store data that is frequently accessed which are second in priority and which cannot be incorporated in L1 due to space limitation.

#flashcards/memory/cache
L3 Cache (Shared Cache) facts
?
- Embedded in the processor.
- Shared by all cores.
- Largest in size.
- Used to store data that is least frequently accessed.

#flashcards/memory/cache
Types of Cache misses and some bullet points
?
- Compulsory Miss (a.k.a Cold Start Miss)
    - First access to a block
    - Occurs when a memory block is brought into the cache for the first time
    - Cannot be avoided unless the block has been pre-fetched
    - Increasing the block size reduces the number of compulsory misses by exploiting spatial locality
- Conflict Miss (a.k.a. Collision Miss/Interference Miss)
    - Occurs when two or more memory blocks map to the same cache block
    - Information was present in the cache previously but was replaced by another block
- Capacity Miss
    - Occurs due to the limited size of the capacity, not the due to the mapping principle being implemented
    - Occurs when the cache is full and a new block must be brought in
    - When the working set is bigger than the cache itself, these misses occur frequently
    - Hardest to identify
- Coherence Miss
- Coverage Miss
- System related Miss

#flashcards/memory/terms/cache
What is the term for when data is found in the cache memory?::Cache Hit
What is the term for the time taken to access data from cache memory?::Hit Latency
What data structure does the processor use to determine if data is present in the cache memory?::Tag Directory (Data Structure)
What is the term for when data is not found in the cache memory?::Cache Miss
What is the term for the time taken to access data from the main memory?::Miss Latency
What are the 3 Cs?::Compulsory Miss (Cold Start Miss), Conflict Miss (Collision/Interference Miss), Capacity Miss

#flashcards/memory/terms/other
What is the term for when data is not found in the main memory?::Page fault
What is the term for the time taken to access data from the secondary memory?::Page fault service time
What is the term for when data is found in the main memory?::Page hit

#flashcards/memory/locality
Locality Reference::The data that is accessed once is likely to be accessed again in the near future.
Pinciple of Locality::States that the data that is accessed once is likely to be accessed again in the near future.
Spacial Locality::States that the data that is accessed once is likely to be accessed again in the near future.
Temporal Locality::States that the data that is accessed once is likely to be accessed again in the near future.


#flashcards/memory/mapping/direct
- Direct Memory Mapping - Secondary Memory to Main Memory
    - Secondary Memory
    ?
- Permanent programs are stored here.
- During execution, programs are turned into processes.
- Every process is subdivided into equal size pages.

#flashcards/memory/mapping/direct
- Direct Memory Mapping - Main Memory to Cache Memory
    - Main Memory
    ?
- Subdivided into equally sized frames.

#flashcards/memory/mapping #flashcards/memory/mapping/direct
What piece of software is responsible for subdividing processes into pages and bringing them into the main memory?::Operating System
Frame size is equal to what?::Page size?
Page size is equal to what?::Frame size?
What is the smallest addressable unit of memory?::Word
What is the term for when 1 word is equal to 1 byte?::Byte-Addressable Memory
Natural Log equivalent to Log base 2::$ln(n)\div ln(2) = log_2\ n$\
Natural Log 64 word Calculation::$ln(64)\div ln(2) = 6$\
Log2 64 word Calculation::$log_2\ 64\ = log_2\ 2^6 = 6$

#flashcards/memory/mapping/direct
Direct Memory Mapping - Main Memory to Cache Memory
?
- The main memory is divided into equally sized blocks.
- These cache memory slots are called cache lines.
- Line size = Block size.

#flashcards/memory/mapping/direct
P.A. bits
?
- Physical Address bits
[^Main Memory is sometimes referred to as physical address space]

#flashcards/memory/direct/examples
Given the following values, how many bits are needed to address each line?
- Cache Size: 16 words
- Block size: 4 words
- Line size: 4 words
- No. of Lines in Cache: 16/4 = 4
?
$log_2\ 4 = log_2\ 2^2 = 2\ bits$

#flashcards/memory/direct/examples
PA Bit Split (6 bit example)
?
4 bits for the block number, 2 bits for the block/line offset.
The block number can be further split into 2 bits for the tag bits and line number.

#flashcards/memory/mapping #flashcards/memory/mapping/direct
The bits that are used to identify the block in the cache memory.::Tag Bits
The bits that are used to identify the line in the cache memory.::Line Number
The bits that are used to identify the word in the block.::Block/Line Offset

#flashcards/memory/mapping/direct
What is a Tag Directory?
?
- A data structure that helps the processor find out whether the data is present in the cache memory or not.
- Primarily keeps the record of the Tag bits, cache line-wise.
- No. of entries = No. of Cache lines.

#flashcards/memory/mapping/direct
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
In this example we have 64 words, or $log_2\ 64 = log_2\ 2^6 = 6\ bits$ to address each block.

#flashcards/memory/direct/examples
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
In this example we have 16 blocks, or $log_2\ 16 = log_2\ 2^4 = 4\ bits$ to address each block.

#flashcards/memory/direct/examples
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

#flashcards/memory/direct/examples
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
#flashcards/memory/direct/examples
Given the following values, what is the P.A. bits split?
MM Size: 4GB
Cache Size: 1MB
Block Size: 4 KB
?
MM Size = $4\ GB = 2^2 \cdot 2^{30}\ B = 2^{2+30} B = 2^{32}\ B$
- No. of P.A. bits = $log_2\ 2^{32} = 32\ bits$
- Block Size = $4\ KB = 2^2 \cdot 2^{10}\ B = 2^{2+10} B = 2^{12}\ B$
- Block Offset = $log_2\ 2^{12} = 12\ bits$
- No. of Blocks in MM = $\frac{2^{32}}{2^{12}} = 2^{32-12} = 2^{20}$
- Block number bits = $log_2\ 2^{20} = 20\ bits$
- Cache Size = $1\ MB = = 1 \cdot 2^{20}\ B = 2^{20}\ B$
- No. of Lines in Cache = $\frac{2^{20}}{2^{12}} = 2^{20-12} = 2^8$
- No. of Tag Bits: P.A. bits - (Line no. bits + offset) = $32 - (8 + 12) = 32 - 20 = 12\ bits$


#flashcards/memory/direct/examples
Given the following values, what is the tag directory size?
MM Size: 4GB
Cache Size: 1MB
Block Size: 4 KB
?
- Tag Directory Size = No. of entries $\cdot$ Tag bits = $2^8 \cdot 12 = 3072\ bits$

#flashcards/memory/direct/examples
Given the following values, what is the number of tag bits?
MM Size: 256 MB
Cache Size: 512 KB
Block Size: 256 B
Word Size: 1 Byte
?
- Tag bits: Identifies the MM block residing in the Cache Line.
- MM Size = $256\ MB = 2^8 \cdot 2^{20}\ B = 2^{8+20} B = 2^{28}\ B$
- Cache Size = $512\ KB = 2^9 \cdot 2^{10}\ B = 2^{9+10} B = 2^{19}\ B$
- No of Tag Bits: $log_2({2^{28}}\div{2^{19}}) = 9\ bits$

#flashcards/memory/direct/examples
Given the following values, what is the cache size?
Byte-Addressable MB Size: 16 GB
Block Size: 16 KB
No. of Tag bits: 10
?
MM Size = 16 GB = $2^4 \cdot 2^{30}\ B = 2^{4+30} B = 2^{34}\ B$
No. of P.A. bits = $log_2\ 2^{34} = 34\ bits$
Block Size = 16 KB = $2^4 \cdot 2^{10}\ B = 2^{4+10} B = 2^{14}\ B$
Block Offset = $log_2\ 2^{14} = 14\ bits$
No. of Line Number Bits: P.A. Bits - (tag bits + offset) = 34 - (10 + 14) = 34 - 24 = 10 bits
No. of Cache Lines = 2^10
Line Size = 2^14 B
Cache Size = 2^10 $\cdot$ 2^14 B = 2^24 B = 16 MB

#flashcards/memory/hierarchy_and_interfacing
# Memory Interfacing:
?
- Part of Computer Organization.
  - Deals with the way of connecting various level of Memory units to Processor & I/O peripherals.
  - The speed of the processor is counted using the unit MIPS.

#flashcards/memory/hierarchy_and_interfacing
What does MIPS stand for?::Million Instructions Per Second

#flashcards/memory/hierarchy_and_interfacing
If our CPU is connected to multiple levels of memory simultaneously, how would we calculate the average memory access time for the following?
?
- If we have memory units: M1, M2, M3
- Acces Time:
    - T1, T2, T3
        - T1 < T2 < T3
- Hit Ratio:
    - H1, H2, H3
        - H1 > H2 > H3
        ?
$H_1 T_1 + ((1-H_1)\cdot H_2) T_2 + ((1-H_1) \cdot (1-H_2))T_3$\
        [^Because the memory units are connected to the CPU simultaneously, which is why these checks will run in parallel]
- So, the time taken to access the data will be the time taken to access the data from the memory unit which has the highest hit ratio.
     - Total no. of Instructions = 100
     - No. of Instructions found in nth level = 80
     - MM's Hit Ratio = 80/100 = 0.8 = 80%


#flashcards/memory/hierarchy_and_interfacing
If our CPU is connected to only one level of memory at a time, how would we calculate the average memory access time for the following?
?
$H_1T_1 + ((1-H_1) \cdot H_2) (H_1+T_2) + ((1-H_1) \cdot (1-H_2)) (H_1+T_2+T_3)$

#flashcards/memory/hierarchy_and_interfacing
A cache memory needs an access time of 30 ns and main memore of 150 ns, what is the average access time of CPU (assume hit ration = 80%)?
- Parallel Organization
?
Assume both the cache and main memory are simultaneously connected to the proccesor.
| Access Time | Hit Ratio |
|-------------|-----------|
| $T_{cache} = 30 \ ns$ | $H_{cache}$ = 80% = 0.8 |
| $T_{MM} = 150 \ ns$ |
| $T_{avg} = H_{cache}T_{cache} + (1-H_{cache})T_{MM} \\ = 0.8 \cdot 30 + (1-0.8)\cdot150 \ ns \\ = 24 + 0.2 \cdot 150 = 54\ ns$ |

#flashcards/memory/hierarchy_and_interfacing
A cache memory needs an access time of 30 ns and main memore of 150 ns, what is the average access time of CPU (assume hit ration = 80%)?
- Level wise organization
?
Assume only one memory unit is connected to the CPU at a time.
- Level wise organization
| Access Time | Hit Ratio |
|-------------|-----------|
| $T_{cache} = 30 \ ns$ | $H_{cache}$ = 80% = 0.8 |
| $T_{MM} = 150 \ ns$ |
| $T_{avg} = H_{cache}T_{cache} + (1-H_{cache})(T_{cache}+T_{MM})$ |
| $= 0.8 \cdot 30 + (1-0.8)(30+150) \ ns$ |
| $= 24 + 0.2 \cdot 180 = 24 + 36 = 60\ ns$ |

#flashcards/memory/hierarchy_and_interfacing
Assume that for a certain processor, a read request takes 50 ns on a cache miss and 5 ns on a cache hit.
- Suppose while running a program, it was observed that 80% of the processor's read requests result in a cache hit.
- The average read access time in ns is:
?
| Access Time | Hit Ratio |
|-------------|-----------|
| $T_{cache}+T_{MM} = 50\ ns$ | $H_{cache}$ = 80% = 0.8 |
| $T_{cache} = 5\ ns$ |
| $T_{avg} = H_{cache}T_{cache} + (1-H_{cache})(T_{cache}+T_{MM})$ |
| $= 0.8 \cdot 5 + (1-0.8)\cdot 50\ ns$ |
| $= 4 + 0.2 \cdot 50 = 4 + 10 = 14\ ns$ |

#flashcards/memory/hierarchy_and_interfacing
Memory Hierarchy: Access Time | Size
?
1. Registers
2. S.R.A.M
3. Main Memory (D.R.A.M)
4. Secondary Memory

#flashcards/memory/hierarchy_and_interfacing
Memory Hierarchy: Cost | Usage Frequency
?
1. Secondary Memory
2. Main Memory D.R.A.M
3. S.R.A.M
4. Registers

#flashcards/memory/mapping/direct/pyqs
A direct mapped cache memory of 1 MB has a block size of 256 bytes.
The cache has an access time of 3 ns and a hit rate of 94%. During a cache miss, it takes 20 ns to bring the first word of a block from the main memory, while each subsequent word takes 5 ns.
The word size is 64 bits. The average memory access time in ns (round of to 1 decimal place) is:
?
Block Size = 256 B
Word Size = 64 bits = $8 \cdot 8 bits = 8 B$\
No of words per Block = $256\ B \div 8\ B = 2^8 \div 2^3 = 2^{8-3} = 2^5$
<br/>
$H_{cache} = 94\% = 0.94$\
$T_{cache} = 3\ ns$\
$T_{MM} = 20 ns for the 1st word, 5\ ns for the rest (for every block)$\
$T_{avg} = H_{cache}T_{cache} + (1-H_{cache})(T_{cache} + T_{MM})$\
$= 0.94 \cdot 3 + (1 - 0.94)(3+((20 \cdot 1) + ((2^5 - 1) \cdot 5)))\ ns$\
$= 2.82 + 0.06(3 + 20 + 155)\ ns = 2.82 + 0.06(178)\ ns$\
$= 2.82 + 10.68 = 13.5\ ns$\
<br/>
Answer: 13.5 ns

#flashcards/memory/mapping/direct/pyqs
Consider a machine with byte addressable main memory of $2^{20}\ bytes$, lock size of 16 bytes and a direct mapped cache having $2^{12}$ cache lines.
Let the addresses of two consecutive bytes in main memory be $(E201F)_{16}$ and $(E2020)_{16}$.
The cache index for the memory address $(E201F)_{16}$.
What are the tag and cache line address (in hex) for main memory address $(E201F)_{16}$?
?
Main Memory Size = $2^{20}\ bytes$\
No. of P.A. bits = $log_2\ 2^{20} = 20\ bits$\
<br/>
Block Size = 16 bytes\
Block Offset = $log_2\ 16 = 4\ bits$\
<br/>
No. of Cache Lines = $2^{12}$\
No of Line number bits= $log_2\ 2^{12} = 12\ bits$\
<br/>
No of Tag bits = P.A. bits - (Line no. bits + offset) = $20 - (12 + 4) = 20 - 16 = 4\ bits$
<br/>
$E201F_{16} = 1110\ 0010\ 0000\ 0001\ 1111_2$\
<br/>
Tag in Hex = $1110 = E$\
Cache line address in hex = $0010\ 0000\ 0001 = 201$\

#flashcards/memory/mapping/direct/pyqs
Consider a machine with byte addressable memory of $2^{32}\ bytes$ divided into blocks of size 32 bytes. Assume a direct mapped cache having 512 cache lines is used with this machine. The size of tag field bits is:
?
Main Memory Size = $2^{32}\ bytes$\
No. of P.A. bits = $log_2\ 2^{32} = 32\ bits$\
<br/>
Block Size = 32 B = $2^5\ bytes$\
<br/>
No. of cache lines = 512 = $2^9$\
No of Line number bits = $log_2\ 2^9 = 9\ bits$
<br/>
No of Tag bits = P.A. bits - (Line no. bits + offset) = $32 - (9 + 5) = 32 - 14 = 18\ bits$

#flashcards/memory/mapping/direct/pyqs
An 8 KB direct-mapped write-back cache is organized as multiple blocks, each of size 32 bytes.
The processor generates 32 bit addresses.
The cache controller maintains the tag information for each cache block comprising of the following.
1 Valid bit, 1 Modified bit.
As many bits as the minimum needed to identify the memory block mapped in the cache.
What is the total size of memory needed at the cache controller to store meta-data (tags) for the cache?
?
Cache size = 8 KB = $2^3 \cdot 2^{10} = 2^{3+10} = 2^{13}\ bytes$\
<br/>
Block size = 32 bytes = $2^5\ bytes$\
Block offset = $log_2\ 32 = 5\ bits$\
<br/>
No. of cache lines = $\frac{2^{13}}{2^5} = 2^{13-5} = 2^8$\
No of Line number bits = $log_2\ 2^8 = 8\ bits$\
<br/>
No. of P.A. bits = $log_2\ 2^{32} = 32\ bits$\
No of Tag bits = P.A. bits - (Line no. bits + offset) = $32 - (8 + 5) = 32 - 13 = 19\\ bits$\
<br/>
Tag directory entriy $= 1 + 1 + 19 = 21\ bits$\
Tag directory size $= 21 \cdot 2^8 = 21 \cdot 256 = 5376\\ bits$
<br/>
Total size of memory needed at the cache controller to store meta-data (tags) for the cache = 5376 bits

#flashcards/memory/mapping/direct/pyqs
Consider a machine with a byte adressable main memory of $2^{16}$ bytes. Assume that a direct mapped data cache consisting of 32 lines of 64 bytes each is used in the system.
A 50 x 50 two-dimensional array is stored in the main memory starting from memory location 1100H.
Assume that the data cache is initially empty. The complete array is accessed twice.
Assume that the contents of the data cache do not change in between the two accesses.
<br/>
- How many cache misses will occur in total?
a) 40
5) 50
c) 56
d) 59
<br/>
- Which of the following line of the data cache wil be replaced by new blocks in accessing the array for the second time?
a) line 4 to 11
b) line 4 to line 7
c) line 0 to line 7
d) line 0 to line 8
?
Main Memory Size = $2^{16}\ bytes$\
No. of P.A. bits = $log_2\ 2^{16} = 16\ bits$\
<br/>
Block Size = 64 B = $2^6\ bytes$\
Block offset = $log_2\ 64 = 6\ bits$\
<br/>
No. of cache lines = 32\
No of Line number bits = $log_2\ 32 = 5\ bits$\
<br/>
No of Tag bits = P.A. bits - (Line no. bits + offset) = $16 - (5 + 6) = 16 - 11 = 5\ bits$\
<br/>
Total number. of elements in the array = $50 \cdot 50 = 2500$\
Element size = 1 byte
Array size = 2500 bytes
No. of blocks to store in the array = $\frac{2500}{64} = 39.0625$\
Blocks are divided equally and we can't use 39.0625 blocks, so we use 40 blocks
No. of blocks = 40
<br/>
P.A. Split
| | $\leftarrow 16\ bits \rightarrow$ | |
|-|-|-|
| 5 bits | 5 bits | 6 bits |
| Tag | Line | Offset |
<br/>
<br/>
Array is stored in the main memory starting from 1100H (H denotes a hexidecimal number) which is 0001 0001 0000 0000 in binary
<br/>
Tag bits = 0001 0
Line bits = 00100
Offset bits = 000000
Line number is 4
<br/>
From this we know that the array is stored starting at line 4 onward.
40 blocks are required to store the entire array.
Let's call them $b_0, b_1, b_2, ..., b_{39}$
The following table represents the cache memory after the first access of the array.
<br/>
| Block | First Access | |
|-|-|-|
| 0 | $b_{28}$ | |
| 1 | $b_{29}$ | |
| 2 | $b_{30}$ | |
| 3 | $b_{31}$ | |
| 4 | ~~$b_0$~~ $b_{32}$ | |
| 5 | ~~$b_1$~~ $b_{33}$ | |
| 6 | ~~$b_2$~~ $b_{34}$ | |
| 7 | ~~$b_3$~~ $b_{35}$ | |
| 8 | ~~$b_4$~~ $b_{36}$ | |
| 9 | ~~$b_5$~~ $b_{37}$ | |
| 10 | ~~$b_6$~~ $b_{38}$ | |
| 11 | ~~$b_7$~~ $b_{39}$ | |
| 12 | $b_8$ | |
| ... | ... | ... |
| 30 | $b_{26}$ | |
| 31 | $b_{27}$ | |
- First iteration cache misses is 40 because the cache is empty.
<br/>
| Block | First Access | Second Access |
|-|-|-|
| 0 | $b_{28}$ | |
| 1 | $b_{29}$ | |
| 2 | $b_{30}$ | |
| 3 | $b_{31}$ | |
| 4 | ~~$b_0$~~ ~~$b_{32}$~~ | ~~$b_0$~~ $b_{32}$ |
| 5 | ~~$b_1$~~ ~~$b_{33}$~~ | ~~$b_1$~~ $b_{33}$ |
| 6 | ~~$b_2$~~ ~~$b_{34}$~~ | ~~$b_{2}$~~ $b_{34}$ |
| 7 | ~~$b_3$~~ ~~$b_{35}$~~ | ~~$b_{3}$~~ $b_{35}$ |
| 8 | ~~$b_4$~~ ~~$b_{36}$~~ | ~~$b_{4}$~~ $b_{36}$ |
| 9 | ~~$b_5$~~ ~~$b_{37}$~~ | ~~$b_{5}$~~ $b_{37}$ |
| 10 | ~~$b_6$~~ ~~$b_{38}$~~ | ~~$b_{6}$~~ $b_{38}$ |
| 11 | ~~$b_7$~~ ~~$b_{39}$~~ | ~~$b_{7}$~~ $b_{39}$ |
| 12 | $b_8$ | |
| ... | ... | ... |
| 30 | $b_{26}$ | |
| 31 | $b_{27}$ | |
- Second iteration cache misses is 16 because the cache is full.
<br/>
- No. of cache misses = 40 + 16 = 56
- line 4 to line 11

#flashcards/memory/mapping/direct/hardware_implementation
Tag directory contains as many entries as the number of lines in the cache (true/false)::True
P.A. bits are the same for all organizations (true/false)::False
What is the most important part of the tag directory and why is it not the only important part?
?
- Tag bits.
    - Most, not only, because sometimes a few extra bits are added to the tag bits to store additional information.
        - Such as the pyq mentioning 1 valid bit and 1 modified bit.

#flashcards/memory/mapping/direct/hardware_implementation
What generates tag bits and how do they work?
?
1. With each cache line their are tag bits, specified by the processor, associated to it.
2. Generally the generated P.A. bits tag portion is match with the tag bits associate with the cache line in that particular instance.
3. If they're equal it a hit, if not it's a miss.


#flashcards/memory/mapping/direct/hardware_implementation
In the following P.A. split how many multiplexers and comparators are needed, and what type are they?
Tag bits = 2
Line bits = 2
Block/Line offset bits = 2
?
- 2 4x1 multiplexers
- 1 2-bit comparator

#flashcards/memory/mapping/direct/hardware_implementation
What type of component is the comparator?
?
- XOR Gate
    - If the generated tag bits and the cache's tag bits are equal, the output of the XOR gate will be 0 (cache miss).
    - If they're not equal, the output will be 1 (cache hit).


#flashcards/memory/mapping/direct/hardware_implementation
![[DMM HWI - Hit Latency Question.png]]::![[DMM HWI - Hit Latency Answer.png]]

#flashcards/memory/mapping/direct/hardware_implementation
What is the biggest disadvantage of direct memory mapping and why?
?
- Conflict miss.
    - Because the cache is divided into equally sized blocks, if two blocks are mapped to the same cache line, the second block will overwrite the first block.
    - This is a disadvantage because the first block may be needed again in the near future.
    - Worst case scenario is that the cache is full and the first block is overwritten, then the second block is needed again, and the first block is needed again, but the cache is full so the first block is overwritten again.
        - Shown in bottom example image:
        ![[DMM HWI - Disadvantage of DMM.png]]

#flashcards/memory/mapping/associative
MM Size = 2 GB
Block Size = 4 KB
Comparator Delay = 15n nanoseconds
Delay of Multi-input OR gate = 7 nanoseconds (Fully associative mapping)
What is the hit latency?
?
- MM Size = $2^1 \cdot 2^{30} = 2^{31} B$
- P.A. bits = $log_2\ 2^{31} = 31\ bits$
- Block Size = $2^{11} B$
- Block Offset = $log_2\ 2^{11} = 11\ bits$
- No. of Tag bits = (31 - 11) = 20 bits
Hit Latency = $(15 \cdot 20) + 7 = 307\ ns$

#flashcards/memory/mapping/associative
What are the restrictions regarding assigning blocks to cache lines in associtive mapping::None. Any block can be assign to any of the cache lines

#flashcards/memory/mapping/associative
Types of associative memory mapping and bullet point:
?
- Fully Associative Mapping
    - Any block can be placed in any cache line
    - P.A. bits are split into tag bits and block offset bits
        - The entire P.A. is used as the tag
        - The block offset bits are used to identify the word in the block
    - Disadvantages:
        - Many to many relationship
            - No clue where to look for the block
            - During retrieval all of the tags associated to all of the cache lines are judged to find the block
                - Increases hit latency
        - Having as many comparators as the cache line working in parallel can be a solution
            - But this is not practical as it will increase the hardware cost exponentially
            - Also will increase the heat of the circuitry as well
- Set Associative Mapping
    - A compromise between direct and fully associative mapping
    - Cache is divided into a number of sets
    - Each set contains a number of lines
    - A block can be placed in any line of a specific set
    - P.A. bits are split into tag bits, set bits, and block offset bits
        - The tag bits are used to identify the block in the cache
        - The set bits are used to identify the set in the cache
        - The block offset bits are used to identify the word in the block

#flashcards/memory/mapping/associative/fully/hardware_implementation
Conceptual Hardware Implementation
- Assuming there are 4 lines in the cache suppose the generated physical address is 8 bits, and the least significant 2 bits are the block offset.
- Therefore the remaining 6 bits are being used as the block number. Because in associative mapping the entire P.A. is used as the tag, the 6 bits are the tag bits.
?
All 4 lines will be connected to a 6 bit comparator each to which the tag bits of the P.A. bits will be fed parallely.
The outputs of the comparators will be given as input to a multi-input OR gate so it can indicate a cache hit if any of the lines have the required block.
Only one cache line will have the block if it is present.
Cache is very expensive and limited in size.
Having more than one copy of the same data is not a smart way to utilize the cache.
One may argue why use an or gate instead of an xor gate.
It would be more expensive to use a multi-input xor gate and we already spent too much on the comparators.
- Hit Latency = $T_{n-bit\ comparator} + T_{OR}$
