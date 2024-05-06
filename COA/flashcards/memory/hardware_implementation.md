---
id: hardware_implementation
aliases: []
tags:
  - flashcards/memory
---

#flashcards/memory/mapping/direct/hardware_implementation
Tag directory contains as many entries as the number of lines in the cache (true/false)::True
P.A. bits are the same for all organizations (true/false)::False
What is the most important part of the tag directory and why is it not the only important part?
?
- Tag bits.
    - Most, not only, because sometimes a few extra bits are added to the tag bits to store additional information.
        - Such as the pyq mentioning 1 valid bit and 1 modified bit.

#flashcards/memory/mapping/direct/hardware_implementation
What generates tag bits and how do they work?
?
1. With each cache line their are tag bits, specified by the processor, associated to it.
2. Generally the generated P.A. bits tag portion is match with the tag bits associate with the cache line in that particular instance.
3. If they're equal it a hit, if not it's a miss.


#flashcards/memory/mapping/direct/hardware_implementation
In the following P.A. split how many multiplexers and comparators are needed, and what type are they?
Tag bits = 2
Line bits = 2
Block/Line offset bits = 2
?
- 2 4x1 multiplexers
- 1 2-bit comparator

#flashcards/memory/mapping/direct/hardware_implementation
What type of component is the comparator?
?
- XOR Gate
    - If the generated tag bits and the cache's tag bits are equal, the output of the XOR gate will be 0 (cache miss).
    - If they're not equal, the output will be 1 (cache hit).


#flashcards/memory/mapping/direct/hardware_implementation
![[DMM HWI - Hit Latency Question.png]]::![[DMM HWI - Hit Latency Answer.png]]

#flashcards/memory/mapping/direct/hardware_implementation
What is the biggest disadvantage of direct memory mapping and why?
?
- Conflict miss.
    - Because the cache is divided into equally sized blocks, if two blocks are mapped to the same cache line, the second block will overwrite the first block.
    - This is a disadvantage because the first block may be needed again in the near future.
    - Worst case scenario is that the cache is full and the first block is overwritten, then the second block is needed again, and the first block is needed again, but the cache is full so the first block is overwritten again.
        - Shown in bottom example image:
        ![[DMM HWI - Disadvantage of DMM.png]]

#flashcards/memory/mapping/associative/fully/hardware_implementation
Conceptual Hardware Implementation
- Assuming there are 4 lines in the cache suppose the generated physical address is 8 bits, and the least significant 2 bits are the block offset.
- Therefore the remaining 6 bits are being used as the block number. Because in associative mapping the entire P.A. is used as the tag, the 6 bits are the tag bits.
?
All 4 lines will be connected to a 6 bit comparator each to which the tag bits of the P.A. bits will be fed parallely.
The outputs of the comparators will be given as input to a multi-input OR gate so it can indicate a cache hit if any of the lines have the required block.
Only one cache line will have the block if it is present.
Cache is very expensive and limited in size.
Having more than one copy of the same data is not a smart way to utilize the cache.
One may argue why use an or gate instead of an xor gate.
It would be more expensive to use a multi-input xor gate and we already spent too much on the comparators.
- Hit Latency = $T_{n-bit\ comparator} + T_{OR}$
