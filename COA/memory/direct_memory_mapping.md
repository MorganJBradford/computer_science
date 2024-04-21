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


#### __Round Robin Mapping (Direct Memory Mapping?):__

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

# Questions

When Word Size is equal to 1 Byte, this is referred to as: Byte-Addressable Memory

Byte Chart

|        |              |        |
|--------|--------------|--------|
| 1 Byte | 8 bits       |        |
| 1 KB   | 1024 B(ytes) | 2^10 B |
| 1 MB   | 1024 KB      | 2^20 B |
| 1 GB   | 1024 MB      | 2^30 B |


Given the following values, what is the P.A. bits split
MM Size: 4GB
Cache Size: 1MB
Block Size: 4 KB

MM Size = $4\ GB = 2^2 \cdot 2^{30}\ B = 2^{2+30} B = 2^{32}\ B$
- No. of P.A. bits = $log_2\ 2^{32} = 32$ bits
- Block Size = $4\ KB = 2^2 \cdot 2^{10}\ B = 2^{2+10} B = 2^{12}\ B$
- Block Offset = $log_2\ 2^{12} = 12$ bits
- No. of Blocks in MM = $\frac{2^{32}}{2^{12}} = 2^{32-12} = 2^{20}$
- Block number bits = $log_2\ 2^{20} = 20$ bits
- Cache Size = $1\ MB = = 1 \cdot 2^{20}\ B = 2^{20}\ B$
- No. of Lines in Cache = $\frac{2^{20}}{2^{12}} = 2^{20-12} = 2^8$
- No. of Tag Bits: P.A. bits - (Line no. bits + offset) = $32 - (8 + 12) = 32 - 20 = 12$ bits

What is a Tag Directory

- A data structure that helps the processor find out whether the data is present in the cache memory or not.
- Primarily keeps the record of the Tag bits, cache line-wise.
- No. of entries = No. of Cache lines.

Given the following values, what is the tag directory size
MM Size: 4GB
Cache Size: 1MB
Block Size: 4 KB

- Tag Directory Size = No. of entries $\cdot$ Tag bits = $2^8 \cdot 12 = 3072$ bits

Given the following values, what is the number of tag bits
MM Size: 256 MB
Cache Size: 512 KB
Block Size: 256 B
Word Size: 1 Byte

- Tag bits: Identifies the MM block residing in the Cache Line.
- MM Size = $256\ MB = 2^8 \cdot 2^{20}\ B = 2^{8+20} B = 2^{28}\ B$
- Cache Size = $512\ KB = 2^9 \cdot 2^{10}\ B = 2^{9+10} B = 2^{19}\ B$
- No of Tag Bits: $log_2({2^{28}}\div{2^{19}}) = 9$ bits

Given the following values, what is the cache size
Byte-Addressable MB Size: 16 GB
Block Size: 16 KB
No. of Tag bits: 10

MM Size = 16 GB = $2^4 \cdot 2^{30}\ B = 2^{4+30} B = 2^{34}\ B$
No. of P.A. bits = $log_2\ 2^{34} = 34$ bits
Block Size = 16 KB = $2^4 \cdot 2^{10}\ B = 2^{4+10} B = 2^{14}\ B$
Block Offset = $log_2\ 2^{14} = 14$ bits
No. of Line Number Bits: P.A. Bits - (tag bits + offset) = 34 - (10 + 14) = 34 - 24 = 10 bits
No. of Cache Lines = 2^10
Line Size = 2^14 B
Cache Size = 2^10 $\cdot$ 2^14 B = 2^24 B = 16 MB



A direct mapped cache memory of 1 MB has a block size of 256 bytes.
The cache has an access time of 3 ns and a hit rate of 94%. During a cache miss, it takes 20 ns to bring the first word of a block from the main memory, while each subsequent word takes 5 ns.
The word size is 64 bits. The average memory access time in ns (round of to 1 decimal place) is:
?
Block Size = 256 B
Word Size = 64 bits = $8 \cdot 8 bits = 8 B$\
No of words per Block = $256\ B \div 8\ B = 2^8 \div 2^3 = 2^{8-3} = 2^5$
$H_{cache} = 94\% = 0.94$\
$T_{cache} = 3\ ns$\
$T_{MM} = 20 ns for the 1st word, 5\ ns for the rest (for every block)$\
$T_{avg} = H_{cache}T_{cache} + (1-H_{cache})(T_{cache} + T_{MM})$\
$= 0.94 \cdot 3 + (1 - 0.94)(3+((20 \cdot 1) + ((2^5 - 1) \cdot 5)))\ ns$\
$= 2.82 + 0.06(3 + 20 + 155)\ ns = 2.82 + 0.06(178)\ ns$\
$= 2.82 + 10.68 = 13.5\ ns$\
Answer: 13.5 ns


Consider a machine with byte addressable main memory of $2^{20}\ bytes$, block size of 16 bytes and a direct mapped cache having $2^{12}$ cache lines.
Let the addresses of two consecutive bytes in main memory be $(E201F)_{16}$ and $(E2020)_{16}$.
The cache index for the memory address $(E201F)_{16}$.
What are the tag and cache line address (in hex) for main memory address $(E201F)_{16}$?

Solution:
Main Memory Size = $2^{20}\ bytes$\
Block Size = 16 bytes\
No. of P.A. bits = $log_2\ 2^{20} = 20\ bits$\
Block Offset = $log_2\ 16 = 4\ bits$\
No. of Cache Lines = $2^{12}$\
No of Line number bits= $log_2\ 2^{12} = 12\ bits$\
No of Tag bits = P.A. bits - (Line no. bits + offset) = $20 - (12 + 4) = 20 - 16 = 4\ bits$
$E201F_{16} = 1110\ 0010\ 0000\ 0001\ 1111_2$\
Tag in Hex = $1110 = E$\
Cache line address in hex = $0010\ 0000\ 0001 = 201$\


Consider a machine with byte addressable memory of $2^{32}\ bytes$ divided into blocks of size 32 bytes. Assume a direct mapped cache having 512 cache lines is used with this machine. The size of tag field bits is:

Solution:
Main Memory Size = $2^{32}\ bytes$\
No. of P.A. bits = $log_2\ 2^{32} = 32\ bits$\
Block Size = 32 B = $2^5\ bytes$\
No. of cache lines = 512 = $2^9$\
No of Line number bits = $log_2\ 2^9 = 9\ bits$
No of Tag bits = P.A. bits - (Line no. bits + offset) = $32 - (9 + 5) = 32 - 14 = 18\ bits$


An 8 KB direct-mapped write-back cache is organized as multiple blocks, each of size 32 bytes.
The processor generates 32 bit addresses.
The cache controller maintains the tag information for each cache block comprising of the following.
1 Valid bit, 1 Modified bit.
As many bits as the minimum needed to identify the memory block mapped in the cache.
What is the total size of memory needed at the cache controller to store meta-data (tags) for the cache?

Solution:
Cache size = 8 KB = $2^3 \cdot 2^{10} = 2^{3+10} = 2^{13}\ bytes$\
Block size = 32 bytes = $2^5\ bytes$\
Block offset = $log_2\ 32 = 5\ bits$\
No. of cache lines = $\frac{2^{13}}{2^5} = 2^{13-5} = 2^8$\
No of Line number bits = $log_2\ 2^8 = 8\ bits$\
No. of P.A. bits = $log_2\ 2^{32} = 32\ bits$\
No of Tag bits = P.A. bits - (Line no. bits + offset) = $32 - (8 + 5) = 32 - 13 = 19\\ bits$\
Tag directory entriy $= 1 + 1 + 19 = 21\ bits$\
Tag directory size $= 21 \cdot 2^8 = 21 \cdot 256 = 5376\\ bits$
Total size of memory needed at the cache controller to store meta-data (tags) for the cache = 5376 bits

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

# Hardware Implementation
Lesson refers to last question in PYQs part 3.

P.A. bits: 6
Cache has $2^2$ lines
Line bits: 2 bits
Block ofset: 2 bits
Tag bits: 2 bits
P.A. bits are specific to each organization
![[DMM Hardware Implementation (HWI).png]]
Our goal is to compare the generated P.A's tag bits with the cache's tag bits to see if the data is in the cache or not.
In order to do so we need two types of combinational circuts:
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
![[DMM HWI - P.A. bits.png]]
![[DMM HWI - Disadvantage of DMM.png]]
