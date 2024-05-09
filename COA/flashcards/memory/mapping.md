---
id: mapping
aliases: []
tags:
  - flashcards/memory
---

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

#flashcards/memory/mapping #flashcards/memory/mapping/direct
The bits that are used to identify the block in the cache memory.::Tag Bits
The bits that are used to identify the line in the cache memory.::Line Number
The bits that are used to identify the word in the block.::Block/Line Offset

#flashcards/memory/mapping/direct
What is a Tag Directory?
?
- A data structure that helps the processor find out whether the data is present in the cache memory or not.
- Primarily keeps the record of the Tag bits, cache line-wise.
- # of entries = # of Cache lines.

#flashcards/memory/mapping/direct
Given the following values please provide the calculation for determining the number of bits required to address each block.
- Main Memory Size: 64 words i.e. (0, 1, ..., 63)
- Block size: 4 words
- # of Blocks in MM: 64/4 = 16
| | | | | |
|-|-|-|-|-|
| __1:__ | 0 | 1 | 2 | 3 |
| __2:__ | 4 | 5 | 6 | 7 |
| __3:__ | 8 | 9 | 10 | 11 |
| __...__ | ... | ... | ... | ... |
| __15:__ | 60 | 61 | 62 | 63 |
?
In this example we have 64 words, or $log_2\ 64 = log_2\ 2^6 = 6\ bits$ to address each block.

#flashcards/memory/mapping/associative
MM Size = 2 GB
Block Size = 4 KB
Comparator Delay = 15n nanoseconds
Delay of Multi-input OR gate = 7 nanoseconds (Fully associative mapping)
What is the hit latency?
?
- MM Size = $2^1 \cdot 2^{30} = 2^{31} B$
- P.A. bits = $log_2(2^{31}) = 31\ bits$
- Block Size = $2^{11} B$
- Block Offset = $log_2(2^{11}) = 11\ bits$
- # of Tag bits = (31 - 11) = 20 bits
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
