---
id: cache
aliases: []
tags:
  - flashcards/memory
---

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
