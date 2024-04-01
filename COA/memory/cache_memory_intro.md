---
id: cache_memory_intro
aliases: []
tags:
  - flashcards/memory/cache
---

# Cache Memory
- Generally comprised of 3 levels:
  - L1 Cache
  - L2 Cache
  - L3 Cache


  - Dual core, quad core, and octa core processors belong to MIMD (Multiple Instruction Multiple Data) architecture in Flynn's taxonomy.
    - Each core has its own L1 cache. All cores share the L2 cache. The L3 cache is shared by all cores.

## L1 Cache
- Embedded in the processor chip.
- Fastest cache memory.
- Smallest in size.

## L2 Cache
- Initially incorporated in the motherboard.
- Now embedded in the processor chip.
- Different processor cores have their own L2 caches.
- Used to store data that is frequently accessed which are second in priority and which cannot be incorporated in L1 due to space limitation.

## L3 Cache (Shared Cache)
- Embedded in the processor.
- Shared by all cores.
- Largest in size.
- Used to store data that is least frequently accessed.

### Cache related terms:
  Cache Hit::When the data is found in the cache memory.
  Hit Latency::Time taken to access the data from the cache memory.
  Tag Directory (Data Structure)::Processor finds out whether the data is present in the cache memory or not.
  Cache Miss::When the data is not found in the cache memory.
  Miss Latency::Time taken to access the data from the main memory.

### Other terms:
  Page fault::When the data is not found in the main memory.
  Page fault service time::Time taken to access the data from the secondary memory.
  Page hit::When the data is found in the main memory.


#### Locality of Reference
Locality Reference::The data that is accessed once is likely to be accessed again in the near future.
Pinciple of Locality::States that the data that is accessed once is likely to be accessed again in the near future.
Spacial Locality::States that the data that is accessed once is likely to be accessed again in the near future.
Temporal Locality::States that the data that is accessed once is likely to be accessed again in the near future.
