---
id: cache_memory_intro
aliases: []
tags: []
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
<dl>
    <dt>Cache Hit:</dt>
    <dd>When the data is found in the cache memory.</dd>
    <dt>Hit Latency:</dt>
    <dd>Time taken to access the data from the cache memory.</dd>
    <dt>Tag Directory (Data Structure):</dt>
    <dd>Processor finds out whether the data is present in the cache memory or not.</dd>
    <dt>Cache Miss:</dt>
    <dd>When the data is not found in the cache memory.</dd>
    <dt>Miss Latency:</dt>
    <dd>Time taken to access the data from the main memory.</dd>
</dl>

### Other terms:
<dl>
    <dt>Page Fault:</dt>
    <dd>When the data is not found in the main memory.</dd>
    <dt>Page Fault Service Time:</dt>
    <dd>Time taken to access the data from the secondary memory.</dd>
    <dt>Page Hit:</dt>
    <dd>When the data is found in the main memory.</dd>
</dl>

#### Locality of Reference
<dl>
    <dt>Principle of Locality:</dt>
    <dd>States that the data that is accessed once is likely to be accessed again in the near future.</dd>
    <dt>Spacial Locality:</dt>
    <dd>States that the data that is accessed once is likely to be accessed again in the near future.</dd>
    <dt>Temporal Locality:</dt>
    <dd>States that the data that is accessed once is likely to be accessed again in the near future.</dd>
</dl>
