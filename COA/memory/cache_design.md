---
id: cache_design
aliases: []
tags: []
---

# Cache Design

1. Block Placement:
    - Where to place the Main Memory Block in the Cache?
2. Block Indetification:
    - How to find the Main Memory Block in the Cache?
3. Block Replacement:
    - During a Cache Miss, how to choose which entry to replace from the Cache?
4. Write Strategy:
    - How are the updations propagated?

## Block Placement

- Direct Mapping:
    - $Block \# \mathbin{\%} \# lines$
- Set Associative Mapping:
    - $Block \# \mathbin{\%} \# sets$
- Fully Associative Mapping:
    - Anywhere!!

## Block Identification

- Direct Mapping:
    1. Find the potential match using Line # & Offset bits.
    2. Compare the Tag bits.
    - P.A. bits:
        - Tag
        - Line #
        - B/L offset
- Set Associative Mapping:
    1. Find the set using Set Index.
    2. Compare the Tag parallely.
    - P.A. bits:
        - Tag
        - Set #
        - B/L offset
- Fully Associative Mapping:
    1. Find the potential match comparing all the Tag bits to every line, simultaneously.
    - P.A. bits:
        - Tag
        - B/L offset

## Block Replacement

- Cache is Limited in Size.
- What should be done,
    a. When the cache is fullL a.k.a Capacity Miss - Can do Block Replacement.
    b. When the potential match can't be found?
        i. Compulsory Miss - The MM Block we are looking for in the cache has not been accessed yet.
        ii. Conflict Miss - The MM Block we are looking for in the cache has been replaced by another MM Block - Can do Block Replacement.
- Replace a "Block" residing in cache with the new block request & move the replaced "Block" into the next level of Memory Hierarchy.

Processor - $n^{th}$ level - $(n+1)^{th}$ level -
Processor (New Block!!) - Cache (Cache Miss) - Main Memory
When the cache block is selected and moved to MM to make space, which then will be brought from the next level of the MM to the cache.

- Which "Block" to replace?
- Cache Replacement Policies:
    a. Random Replacement
    b. FIFO & LIFO
    c. Recency Based Policies
    d. Frequency Based Policies
    e. Optimal Replacment Policy/Belady's Optimal Algorithm

## Write Strategy

- When?
    - Processor needs to modify data word.
- Situations:
    1. Write Hit: The data is present in the cache.
        1.1. Write Through:
            - Cache & MM are updated simultaneously.
            - Used during lesser write operations.
        - Reliable & helps in Data Recovery.
        - Delayed Data writes.
        1.2. Write Back/Write Deferred:
            - Cache is updated in real time & uses "Dirty-bit".
                - Dirty-bit is stored in the Tag Directory for each Tag Direcory entry along with its Tag information.
            - MM is updated when replacement takes place.
        - Faster.
        - Data recovery is impossible
    2. Write Miss: The data is absent from the cache.
        2.1. Write Allocate:
            - Data is brought into the cache first.
            - Can work equally with Write-through & Write-back.
        2.2. No-Write Allocate:
            - Data is updated directly in the Main Memory.

[Lesson](https://www.youtube.com/watch?v=1tvW8kzOpSA&list=PLBlnK6fEyqRjdT1xkkBZSXKwFKqQoYhwy&index=22)
