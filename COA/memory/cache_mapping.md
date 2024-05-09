---
id: cache_mapping
aliases: []
tags: []
---

- [ ] ---
id: cache_mapping
aliases: []
tags: []
---

# Cache Memory Mapping - A Comparative Study

![[Cache Memory Mapping - Comparative Study Intro.png]]

The following is a comparative study of the three most common cache memory mapping techniques: Direct Mapping, Associative Mapping, and Set Associative Mapping (4-way for this example):

![[Cache Memory Mapping - Comparative Study.png]]

The parameters are shown in the columns, and the mapping techniques are shown in the rows.

## Tag bits
Tag bits are used for the identification of the MM blocks inside the cache lines.

Direct mapping we are using 11 tag bits.
Associative mapping 20 tag bits.
4-way set associative 13 tag bits.

## Cache Lines
# of cache lines is a sole property of the cache that depends on the size of the line or the block. It has nothing to do with the mapping technique.
Therefore, the number of cache lines will remain the same for all of the different cache mapping techniques:
$2^{11}$

## Tag Directory Size
We know the number of tag directory entries will be the same as the number of cache lines; however, the tag directory size will vary because of the different number of tag bits in the different mapping techniques.

Direct mapping: $2^{11} \cdot 11\ tag\ bits$
Associative mapping: $2^{11} \cdot 22\ tag\ bits$
4-way Set Associative Mapping: $2^{11} \cdot 13\ tag\ bits$

The number of tag directory entries in every case will be the same, but the size of the tag directory will differ because of the different number of tag bits.

## Comparators

Direct mapping is a very strict mapping policy, and for block identification we are going to only compare a single cache line at a time, so we only need 1 comparator.

Associatie mapping is flexible, meaning we don't have any restrictions on placing any of the MM blocks into any of the cache lines. Therefore, we will need $2^{11}$ comparators because we need the comparators to be associated with all of the cache lines.

4-way set associative mapping we know that due to the 4-way, every set inside the cache is going to have 4 lines in them. This means we will be comparing only 4 lines belonging to the same set during block identification. Therefore, the number of comparators we will need is 4.

Summary:
- Direct Mapping: always 1 comparator
- Associative Mapping: same as number of cache lines
- k-way Set Associative Mapping: depends on the value of k

Type of comparators depends on the tag size because comparing the tags associated to the cache lines with the tag field of the P.A. we can actually specify either the blocks presence or absence inside the cache. In this specific scenario:
- Direct Mapping: we calculated the tag bits to be 11 bits; therefore, we need one 11 bit comparator.
- Associative Mapping: since the tag bits are of 22 bits, we will need $2^{11}$ 22 bit comparators.
- 4-way Set Associative Mapping: we calculated the tag bits to be 13 bits; therefore, we need four 13 bit comparators.

Remeber the number of lines inside the cache depends soley upon the cache's overall size and the block or the line size and has nothing to do with the mapping technique.

## Special Note
"k-way" Set Associative Mapping
    1. if k = 1, then 1 set = 1 line
        - same as Direct Mapping
    2. if k = N (lines inside the cache), then 1 set = All lines i.e. Entire Cache
        - same as Fully-Associative Mapping

