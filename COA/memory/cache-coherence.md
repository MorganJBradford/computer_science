---
id: cache-coherence
aliases: []
tags: []
---

# Cache Coherence
<dl>
    <dt>Cache Coherence</dt>
    <dd>It is the uniformity of shared resource data that ends up stored in multiple local caches.</dd>
    <dd>When one cache modifies the data, the other caches must be updated to reflect that change.</dd>
    <dt>Cache Coherence Problem</dt>
    <dd>It is the challenge of keeping multiple local caches synchronized when one of the processors</dd>
    <dd> updates its local copy of data which is shared among multiple caches.</dd>
    <dt>Cache Coherence Protocols</dt>
    <dd>These are the set of rules that ensure that the data in the caches is kept coherent.</dd>
</dl>

## Cache States
- **Modified**: The cache block has been modified and is not consistent with the main memory.
- **Shared**: The cache block is shared among multiple caches and is consistent with the main memory.
- **Invalid**: The cache block is invalid and cannot be used.
- **Exclusive**: The cache block is not modified, is only present in the current cache, and is consistent with the main memory.
    - May be changed to shared at any moment in response to a read request of another processor.
- **Owned**: The cache block is owned by the cache and is consistent with the main memory.
    - Responsible for handling read requests from other processors.
- **Forward**: The cache block is forwarded to another cache.
    - Special form of the shared state.
    - Cache with the forward state is responsible for forwarding the updations to the other caches.

## Cache Coherence Protocols (Hardware-Based. Called schemes for software based)
- [Snooping-Based Cache Coherency Protocol (Bus-Based)](https://www.youtube.com/watch?v=YNpaELJZm2c&list=PLBlnK6fEyqRjdT1xkkBZSXKwFKqQoYhwy&index=27)
    - **Write Update - Write Through**:
    - **Write Update - Write back**:
    - **Write Invalidate - Write through**:
    - **Write Invalidate - Write back**:
- [Directory-Based Cache Coherency Protocol](https://www.youtube.com/watch?v=KEc4NQZjkMI&list=PLBlnK6fEyqRjdT1xkkBZSXKwFKqQoYhwy&index=28)
    - Meant for distributed memory systems.
