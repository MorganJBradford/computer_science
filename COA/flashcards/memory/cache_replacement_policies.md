---
id: cache_replacement_policies
aliases: []
tags:
  - flashcards/memory/cache_replacement_policies
---

#flashcards/memory/cache_replacement_policies/pyqs
Consider a fully associative cache with 8 cache blocks (numbered 0-7) and the following sequence of memory block requests:
4, 3, 25, 8, 19, 6, 25, 8, 16, 35, 45, 22, 8, 3, 16, 25, 7
If the LRU replacement policy is used, which cache block will have memory block 7?
A) 4
B) 5
C) 6
D) 7
?
Answer: B

#flashcards/memory/cache_replacement_policies/pyqs
Consider a 2-way set associative cache memory with 4 sets and a total of 7 cache blocks (0-7) and a main memory with 128 blocks (0-127).
What memory blocks will be present in the cache after the following sequence of memory block references if the LRU policy is used for cache block replacement.
Assuming that initially the cache did not have any memory blocks from its current job?
0 5 3 9 7 0 16 55
A) 0 3 5 7 16 55
B) 0 3 5 7 9 16 55
C) 0 5 7 9 16 55
D) 3 5 7 9 16 55
?
![[LRU Cache Replacement 2 way pyq answer.png]]
Answer: C
