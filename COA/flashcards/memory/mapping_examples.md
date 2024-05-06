---
id: mapping_examples
aliases: []
tags:
  - flashcards/memory
---

#flashcards/memory/direct/examples
Given the following values, how many bits are needed to address each line?
- Cache Size: 16 words
- Block size: 4 words
- Line size: 4 words
- No. of Lines in Cache: 16/4 = 4
?
$log_2\ 4 = log_2\ 2^2 = 2\ bits$

#flashcards/memory/direct/examples
PA Bit Split (6 bit example)
?
4 bits for the block number, 2 bits for the block/line offset.
The block number can be further split into 2 bits for the tag bits and line number.

#flashcards/memory/direct/examples
Given the following values, how many bits are required to address each block?
- Main Memory Size: 64 words i.e. (0, 1, ..., 63)
- Block size: 4 words
- No. of Blocks in MM: 64/4 = 16
| | | | | |
|-|-|-|-|-|
| __1:__ | 0 | 1 | 2 | 3 |
| __2:__ | 4 | 5 | 6 | 7 |
| __3:__ | 8 | 9 | 10 | 11 |
| __...__ | ... | ... | ... | ... |
| __15:__ | 60 | 61 | 62 | 63 |
?
In this example we have 16 blocks, or $log_2\ 16 = log_2\ 2^4 = 4\ bits$ to address each block.

#flashcards/memory/direct/examples
If the processor generates the following address: 011111, which word of which block is being addressed?
- Main Memory Size: 64 words i.e. (0, 1, ..., 63)
- Block size: 4 words
- No. of Blocks in MM: 64/4 = 16
| | | | | |
|-|-|-|-|-|
| __1:__ | 0 | 1 | 2 | 3 |
| __2:__ | 4 | 5 | 6 | 7 |
| __3:__ | 8 | 9 | 10 | 11 |
| __...__ | ... | ... | ... | ... |
| __15:__ | 60 | 61 | 62 | 63 |
?
Block 7, Word 3

#flashcards/memory/direct/examples
If we consider all of the bit places' magnitudes and add up all of the values, we get the following:
- Main Memory Size: 64 words i.e. (0, 1, ..., 63)
- Block size: 4 words
- No. of Blocks in MM: 64/4 = 16
| | | | | |
|-|-|-|-|-|
| __1:__ | 0 | 1 | 2 | 3 |
| __2:__ | 4 | 5 | 6 | 7 |
| __3:__ | 8 | 9 | 10 | 11 |
| __...__ | ... | ... | ... | ... |
| __15:__ | 60 | 61 | 62 | 63 |
?
$2^5 + 2^4 + 2^3 + 2^2 + 2^1 + 2^0 = 0 + 16 + 8 + 4 + 2 + 1 = 31$

#flashcards/memory/direct/examples
Given the following values, what is the P.A. bits split?
MM Size: 4GB
Cache Size: 1MB
Block Size: 4 KB
?
MM Size = $4\ GB = 2^2 \cdot 2^{30}\ B = 2^{2+30} B = 2^{32}\ B$
- No. of P.A. bits = $log_2\ 2^{32} = 32\ bits$
- Block Size = $4\ KB = 2^2 \cdot 2^{10}\ B = 2^{2+10} B = 2^{12}\ B$
- Block Offset = $log_2\ 2^{12} = 12\ bits$
- No. of Blocks in MM = $\frac{2^{32}}{2^{12}} = 2^{32-12} = 2^{20}$
- Block number bits = $log_2\ 2^{20} = 20\ bits$
- Cache Size = $1\ MB = = 1 \cdot 2^{20}\ B = 2^{20}\ B$
- No. of Lines in Cache = $\frac{2^{20}}{2^{12}} = 2^{20-12} = 2^8$
- No. of Tag Bits: P.A. bits - (Line no. bits + offset) = $32 - (8 + 12) = 32 - 20 = 12\ bits$


#flashcards/memory/direct/examples
Given the following values, what is the tag directory size?
MM Size: 4GB
Cache Size: 1MB
Block Size: 4 KB
?
- Tag Directory Size = No. of entries $\cdot$ Tag bits = $2^8 \cdot 12 = 3072\ bits$

#flashcards/memory/direct/examples
Given the following values, what is the number of tag bits?
MM Size: 256 MB
Cache Size: 512 KB
Block Size: 256 B
Word Size: 1 Byte
?
- Tag bits: Identifies the MM block residing in the Cache Line.
- MM Size = $256\ MB = 2^8 \cdot 2^{20}\ B = 2^{8+20} B = 2^{28}\ B$
- Cache Size = $512\ KB = 2^9 \cdot 2^{10}\ B = 2^{9+10} B = 2^{19}\ B$
- No of Tag Bits: $log_2({2^{28}}\div{2^{19}}) = 9\ bits$

#flashcards/memory/direct/examples
Given the following values, what is the cache size?
Byte-Addressable MB Size: 16 GB
Block Size: 16 KB
No. of Tag bits: 10
?
MM Size = 16 GB = $2^4 \cdot 2^{30}\ B = 2^{4+30} B = 2^{34}\ B$
No. of P.A. bits = $log_2\ 2^{34} = 34\ bits$
Block Size = 16 KB = $2^4 \cdot 2^{10}\ B = 2^{4+10} B = 2^{14}\ B$
Block Offset = $log_2\ 2^{14} = 14\ bits$
No. of Line Number Bits: P.A. Bits - (tag bits + offset) = 34 - (10 + 14) = 34 - 24 = 10 bits
No. of Cache Lines = 2^10
Line Size = 2^14 B
Cache Size = 2^10 $\cdot$ 2^14 B = 2^24 B = 16 MB

#flashcards/memory/mapping/associative/fully/examples
MM Size: 4 GB
Cache Size: 1MB
Block Size: 4 KB
Word Size: 1 Byte
1. P.A. bits' split?
2. Tag directory size?
?
MM Size = $2^2\ bytes \cdot 2^{30}\ bytes = 2^{32}\ bytes$\
P.A. bits = $log_2(2^{32}) = 32\ bits$\
Block Size = $2^2\ bytes \cdot 2^{10}\ bytes = 2^{12}\ bytes$\
Block Offset = $log_2(2^{12}) = 12\ bits$\
No. of Block in MM = $2^{32}\ bytes \div 2^{12}\ bytes = 2^{20}\ bytes$\
Block N. bits/No. of Tag bits = $log_2(2^{20}) = 20\ bits$
- 20 Block No. bits/Tag Bits; 12 bits Block/Line offset\
Cache Size = $2^{20}\ bytes$\
1. No. of Line in Cache = $2^{20} \div 2^{12} = 2^8\ bytes$
2. Tag directory size = $2^8 \cdot 20\ bits$
    - 5120 bits

#flashcards/memory/mapping/associative/fully/examples
MM Size: 16 GB
Block Size: 16 KB
Word Size: 1 Byte
1. P.A. bits' split?
2. Tag Directory Size?
?
MM Size = $2^4 \cdot 2^{30}\ bytes = 2^{34}\ bytes$\
P.A. bits = $log_2(2^{34}) = 34\ bits$\
Block Size = $2^4 \cdot 2^{10}\ bytes = 2^{14}\ bytes$\
Block Offset = $log_2(2^{14}) = 14$\
No. of Blocks = $2^{34}\ bytes \div 2^{14}\ bytes = 2^{20}\ bytes$\
No. of Block bits = $log_2(2^{20}) = 20\ bits$
- Fully associative mapping; Tag bits and Block bits are equivalent
1. 20 Block/Tag bits; 14 block/line offset bits
2. Unable to determine:
    - Neither the Cache Size or the No. of Lines in Cache were provided
    - Tag directory size can't be calculated if we don't know:
        - How many lines are in the cache
        - How many bits are being used in order to store the tag information
