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
- Every process is subdiveded into equal size pages.
## Main Memory
- Subdivided into equally sized frames.

The process of subdividing processes into pages and then bringith them into the main memory is done by the operating system.

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

||||||
|-|-|-|-|-|
__1:__ | 0 | 1 | 2 | 3 |
__2:__ | 4 | 5 | 6 | 7 |
__3:__ | 8 | 9 | 10 | 11 |
__...__ | ... | ... | ... | ... |
__15:__ | 60 | 61 | 62 | 63 |

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
