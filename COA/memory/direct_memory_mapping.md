---
id: direct_memory_mapping
aliases: []
tags:
  - flashcards/memory/direct_memory_mapping
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

Word::Smallest Addressable Unit of Memory

Byte-Addressable Memory::1 word = 1 Byte

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

Natural Log equivalent to Log base 2::$ln(n)\div ln(2) = log_2\ n$\
Natural Log 64 word Calculation::$ln(64)\div ln(2) = 6$\
Log2 64 word Calculation::$log_2\ 64\ = log_2\ 2^6 = 6$

P.A. bits
?
Physical Address bits
Main Memory is sometimes referred to as physical address space

In this example we have 16 blocks, or $log_2\ 16 = log_2\ 2^4 = 4$ bits to address each block.


If the processor generates the following address: 011111, which word of which block is being addressed?::Block 7, Word 3

If we consider all of the bit places' magnitudes and add up all of the values, we get the following:
?
$2^5 + 2^4 + 2^3 + 2^2 + 2^1 + 2^0 = 0 + 16 + 8 + 4 + 2 + 1 = 31$

### Cache Memory

- Cache Size: 16 words
- Block size: 4 words
- Line size: 4 words
- No. of Lines in Cache: 16/4 = 4

How many bits are needed to address each line?::$log_2\ 4 = log_2\ 2^2 = 2$ bits

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
?
4 bits for the block number, 2 bits for the block/line offset.
The block number can be further split into 2 bits for the tag bits and line number.

Tag Bits::The bits that are used to identify the block in the cache memory.
Line Number::The bits that are used to identify the line in the cache memory.
Block/Line Offset::The bits that are used to identify the word in the block.

# Questions

When Word Size is equal to 1 Byte, this is referred to as::Byte-Addressable Memory

Byte Chart
?
|        |              |        |
|--------|--------------|--------|
| 1 Byte | 8 bits       |        |
| 1 KB   | 1024 B(ytes) | 2^10 B |
| 1 MB   | 1024 KB      | 2^20 B |
| 1 GB   | 1024 MB      | 2^30 B |


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

What is a Tag Directory?
?
- A data structure that helps the processor find out whether the data is present in the cache memory or not.
- Primarily keeps the record of the Tag bits, cache line-wise.
- No. of entries = No. of Cache lines.

Given the following values, what is the tag directory size?
MM Size: 4GB
Cache Size: 1MB
Block Size: 4 KB
?
- Tag Directory Size = No. of entries $\cdot$ Tag bits = $2^8 \cdot 12 = 3072$ bits

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



Word??Smallest Addressable Unit of Memory
Byte-Addressable Memory::1 word = 1 Byte
Natural Log equivalent to Log base 2::$ln(n)\div ln(2) = log_2\ n$\
Natural Log 64 word Calculation::$ln(64)\div ln(2) = 6$\
Log2 64 word Calculation::$log_2\ 64\ = log_2\ 2^6 = 6$
If the processor generates the following address: 011111, which word of which block is being addressed?::Block 7, Word 3
How many bits are needed to address each line?::$log_2\ 4 = log_2\ 2^2 = 2$ bits
Tag Bits::The bits that are used to identify the block in the cache memory.
Line Number::The bits that are used to identify the line in the cache memory.
Block/Line Offset::The bits that are used to identify the word in the block.
When Word Size is equal to 1 Byte, this is referred to as::Byte-Addressable Memory
When Word Size is equal to 1 Byte, this is referred to as::Byte-Addressable Memory
