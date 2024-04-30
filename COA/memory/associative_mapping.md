---
id: associative_mapping
aliases: []
tags: []
---

# Associate Memory Mapping
## Strengths

Direct Memory Mapping has a distict weakness: Cache Misses

There are many types of cache misses (First 3 are known as the 3 Cs):
Type of Cache Misses (First 3 are known as the 3 Cs):
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

## Types of Associative Memory Mapping

The solution to direct memory mapping's issue with conflict misses is to use associative memory mapping.

In assocative mapping there are no restrictions regarding the mapping technique. Any block can be assigned to any of the cache lines.

### Fully Associative Mapping
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

#### Conceptual Hardware Implementation
Assuming there are 4 lines in the cache suppose the generated physical address is 8 bits, and the least significant 2 bits are the block offset.
Therefore the remaining 6 bits are being used as the block number. Because in associative mapping the entire P.A. is used as the tag, the 6 bits are the tag bits.

All 4 lines will be connected to a 6 bit comparator each to which the tag bits of the P.A. bits will be fed parallely.
The outputs of the comparators will be given as input to a multi-input OR gate so it can indicate a cache hit if any of the lines have the required block.
Only one cache line will have the block if it is present.
Cache is very expensive and limited in size.
Having more than one copy of the same data is not a smart way to utilize the cache.
One may argue why use an or gate instead of an xor gate.
It would be more expensive to use a multi-input xor gate and we already spent too much on the comparators.

Hit Latency = $T_{n-bit\ comparator} + T_{OR}$

Example:
MM Size = 2 GB
Block Size = 2 KB
Comparator Delay = 15n nanoseconds
Delay of Multi-input OR gate = 7 nanoseconds
What is the hit latency?









### Set Associative Mapping
    - A compromise between direct and fully associative mapping
    - Cache is divided into a number of sets
    - Each set contains a number of lines
    - A block can be placed in any line of a specific set
    - P.A. bits are split into tag bits, set bits, and block offset bits
        - The tag bits are used to identify the block in the cache
        - The set bits are used to identify the set in the cache
        - The block offset bits are used to identify the word in the block

