---
id: cache_replacement_policies
aliases: []
tags: []
---

# Block Replacement:
- Which "Block" to replace?
    - Direct Mapping: No need to make the decision
        - Line number is specified by the Block number
    - Associative & Set Associative mapping:
        - MM block can be placed in any line of the cache/set
            - Availablitiy of choices
            - [x] Cache replacement policies
                - Reduce cache misses
                - Minimize "miss penalty" - Time required by the processor to get the data from the next level of the memory hierarchy during the cache miss
- Cache replacement policies are required for associative and set associative but not direct mapping

# Cache Replacement Policies

## RR, FIFO, LIFO, & Optimal:
a. Random Replacement
b. FIFA & LIFO
c. Optimal Replacement/Belady's Optimal Algorithm

### Random Replacement:
- Evint any block form cache at random
- Access information is not needed
- Not implemented. (used to be implemented in ARM architectures)

### FIFO:
- Events block from cache in their order of arrival
- Cache behave as a First-In-First-Out queue

Consider a fully associative cache memory with 4 lines that implements FIFO cache replacement policy. For the following block requests:
2, 3, 4, 7, 6, 3, 4, 7, 5, 4, 7, 8
Which are the Miss and Hit ratios, respectively?
?
| Cache Line | |
|-|-|
| 0 | $\cancel{2}$ 6 |
| 1 | $\cancel{3}$ 5 |
| 2 | $\cancel{4}$ 8 |
| 3 | 7 | |
Miss Ratio = $\frac{Number\ of\ Misses}{Total\ Number\ of\ Requests} \cdot 100 \mathbin{\%}$
= $\frac{7}{12} \cdot 100 \mathbin{\%} = 58.33 \mathbin{\%}$
Hit Ratio = $100 - 58.33 = 41.67 \mathbin{\%}$
\# of Misses: 7 = 4 Compulsory Misses + 3 Capacity Misses

### LIFO:
- Evicts the most recently added block i.e. Last-In-First-out
- Cache behaves as a stack

### Optimal Replacement/Belady's Optimal Algorithm:
- Evicts the block that will be used farthest in the future
- Prediction of Block requests is IMPOSSIBLE

Block Requests: 2, 3, 4, 7, 6, 3, 4, 7, 5, 4, 7, 8

| Cache Line |                |
|-|-|
| 0 | $\cancel{2}$ 6 |
| 1 | $\cancel{3}$ 5 |
| 2 | $\cancel{4}$ 8 |
| 3 | 7 |

- Widely used as an efficienc measuring tool for real replacement algorithms
- Proposed by L.A. Belady in 1966

## Recency Based Policies:

a. MRU - Most Recently Used
b. LRU - Least Recently Used
c. Pseudo-LRU - Pseudo-Least Recently Used

### MRU:
- Evicts most recently referred block
- Works well with cyclic patterns

Block Requests: 1, 2, 3, 4, 5, 1, 2, 3, 4, 1, 2

| Cache Line | |
|-|-|
| 0 | $b_1$ |
| 1 | $b_2$ |
| 2 | $\cancel{b_3}\ b_4$ |
| 3 | $\cancel{b_4}\ b_5$ |

## LRU:
- Exploits Temoral Locality
- Evicts least recently referred block
- Rigorous use of Age bits

### Explanation
Block Requests: 0, 1, 2, 3, 4, 2, 3, 1, 5, 6
Fully Associative Cache with 4 lines

| Cache Line | |
|-|-|
| 0 | $\cancel{b_0}\ \cancel{b_4}\ b_5$ |
| 1 | $b_1$ |
| 2 | $\cancel{b_2}\ b_6$ |
| 3 | $b_3$ |

### Implemntation
Block Requests: 0, 1, 2, 3, 4, 2, 3, 1, 5, 6

| Cache Line | MM Block in Line | Age bits (as decimal) |
|-|-|-|
| 0 | $\cancel{b_0}\ \cancel{b_4}\ b_5$ | $\cancel{0} \cancel{3} \cancel{2} \cancel{1} \cancel{0} \cancel{3} \cancel{2} \cancel{1} \cancel{0} \cancel{3} \cancel{2} 3$ |
| 1 | $b_1$ | $\cancel{1} \cancel{0} \cancel{3} \cancel{2} \cancel{1}\ 0\ \ 0\ \cancel{0} \cancel{3} \cancel{2} \cancel{1} 1$ |
| 2 | $\cancel{b_2}\ b_6$ | $\cancel{2} \cancel{1} \cancel{0} \cancel{3} \cancel{2} \cancel{1} \cancel{3} \cancel{2} \cancel{1} \cancel{0} \cancel{3} 2$ |
| 3 | $b_3$ | $\cancel{3} \cancel{2} \cancel{1} \cancel{0} \cancel{3} \cancel{2} \cancel{1} \cancel{3} \cancel{2} \cancel{1}\ 0\ 0$ |

Total no. of sequences = $4 \cdot 3 \cdot 2 \cdot 1 = 4! = 24$
In order to keep track of the age bits, we need to keep track of $\lceil{log_2(4!)}\rceil = 5$ bits
If we had 8 lines in our cache, we would need 8 different age bits for each line, or $\lceil{log_2(8!)}\rceil = 16$ bits
If we had 4-way or 8-way set associtive cache, we would need 4 or 8 age bits for each set
- HUGE OVERHEAD for caches with higher associativity
    - Impractical

## Pseudo-LRU:
- Generates Approximate measures for replacements

Block Requests: 0, 1, 2, 3, 4, 5, 6, 7, 2, 1, 9, 8
Fully associative cache with 8 lines

During replacement in the following image, in order to find the least recently used block we toggle each bit and then follow the associated direct.
Once we reach the line we replace it, and now it is automatically the most recently used block as the bits have been toggled.

![[PLRU example.png]]

## Frequency Based Policies:
- Least Frequently Used (LFU)
    - Evicts least frequencly referred block
    - Frequency is recorded for all blocks present in Cache

Block Requests: 0, 1, 2, 3, 4, 2, 3, 1, 5, 6
Tie breaker: FIFO

| Cache Line | MM Block in Line | Frequency |
|-|-|-|
| 0 | $\cancel{b_0}\ \cancel{b_4} \cancel{b_5} b_6$ | $\cancel{1} \cancel{1} \cancel{1} 1$ |
| 1 | $b_1\ b_1$ | $\cancel{1} 2$ |
| 2 | $b_2\ b_2$ | $1 \cancel{1} 2$ |
| 3 | $b_3\ b_3$ | $1\ \cancel{1} 2$ |

[Lesson](https://www.youtube.com/watch?v=_Hh-NcdbHCY&list=PLBlnK6fEyqRjdT1xkkBZSXKwFKqQoYhwy&index=24)
