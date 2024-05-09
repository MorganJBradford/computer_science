---
id: mapping_examples
aliases: []
tags:
  - flashcards/memory
---

#flashcards/memory/mapping/direct/examples
Given the following values, how many bits are needed to address each line?
- Cache Size: 16 words
- Block size: 4 words
- Line size: 4 words
- # of Lines in Cache: 16/4 = 4
?
$log_2\ 4 = log_2\ 2^2 = 2\ bits$

#flashcards/memory/mapping/direct/examples
PA Bit Split (6 bit example)
?
4 bits for the block number, 2 bits for the block/line offset.
The block number can be further split into 2 bits for the tag bits and line number.

#flashcards/memory/mapping/direct/examples
Given the following values, how many bits are required to address each block?
- Main Memory Size: 64 words i.e. (0, 1, ..., 63)
- Block size: 4 words
- # of Blocks in MM: 64/4 = 16
| | | | | |
|-|-|-|-|-|
| __1:__ | 0 | 1 | 2 | 3 |
| __2:__ | 4 | 5 | 6 | 7 |
| __3:__ | 8 | 9 | 10 | 11 |
| __...__ | ... | ... | ... | ... |
| __15:__ | 60 | 61 | 62 | 63 |
?
In this example we have 16 blocks, or $log_2\ 16 = log_2\ 2^4 = 4\ bits$ to address each block.

#flashcards/memory/mapping/direct/examples
If the processor generates the following address: 011111, which word of which block is being addressed?
- Main Memory Size: 64 words i.e. (0, 1, ..., 63)
- Block size: 4 words
- # of Blocks in MM: 64/4 = 16
| | | | | |
|-|-|-|-|-|
| __1:__ | 0 | 1 | 2 | 3 |
| __2:__ | 4 | 5 | 6 | 7 |
| __3:__ | 8 | 9 | 10 | 11 |
| __...__ | ... | ... | ... | ... |
| __15:__ | 60 | 61 | 62 | 63 |
?
Block 7, Word 3

#flashcards/memory/mapping/direct/examples
If we consider all of the bit places' magnitudes and add up all of the values, we get the following:
- Main Memory Size: 64 words i.e. (0, 1, ..., 63)
- Block size: 4 words
- # of Blocks in MM: 64/4 = 16
| | | | | |
|-|-|-|-|-|
| __1:__ | 0 | 1 | 2 | 3 |
| __2:__ | 4 | 5 | 6 | 7 |
| __3:__ | 8 | 9 | 10 | 11 |
| __...__ | ... | ... | ... | ... |
| __15:__ | 60 | 61 | 62 | 63 |
?
$2^5 + 2^4 + 2^3 + 2^2 + 2^1 + 2^0 = 0 + 16 + 8 + 4 + 2 + 1 = 31$

#flashcards/memory/mapping/direct/examples
Given the following values, what is the P.A. bits split?
MM Size: 4GB
Cache Size: 1MB
Block Size: 4 KB
?
MM Size = $4\ GB = 2^2 \cdot 2^{30}\ B = 2^{2+30} B = 2^{32}\ B$
- # of P.A. bits = $log_2\ 2^{32} = 32\ bits$
- Block Size = $4\ KB = 2^2 \cdot 2^{10}\ B = 2^{2+10} B = 2^{12}\ B$
- Block Offset = $log_2\ 2^{12} = 12\ bits$
- # of Blocks in MM = $\frac{2^{32}}{2^{12}} = 2^{32-12} = 2^{20}$
- Block number bits = $log_2\ 2^{20} = 20\ bits$
- Cache Size = $1\ MB = = 1 \cdot 2^{20}\ B = 2^{20}\ B$
- # of Lines in Cache = $\frac{2^{20}}{2^{12}} = 2^{20-12} = 2^8$
- # of Tag Bits: P.A. bits - (Line no. bits + offset) = $32 - (8 + 12) = 32 - 20 = 12\ bits$


#flashcards/memory/mapping/direct/examples
Given the following values, what is the tag directory size?
MM Size: 4GB
Cache Size: 1MB
Block Size: 4 KB
?
- Tag Directory Size = # of entries $\cdot$ Tag bits = $2^8 \cdot 12 = 3072\ bits$

#flashcards/memory/mapping/direct/examples
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

#flashcards/memory/mapping/direct/examples
Given the following values, what is the cache size?
Byte-Addressable MB Size: 16 GB
Block Size: 16 KB
\# of Tag bits: 10
?
MM Size = 16 GB = $2^4 \cdot 2^{30}\ B = 2^{(4+30)} B = 2^{34}\ B$
\# of P.A. bits = $log_2\ 2^{34} = 34\ bits$
Block Size = 16 KB = $2^4 \cdot 2^{10}\ B = 2^{4+10} B = 2^{14}\ B$
Block Offset = $log_2\ 2^{14} = 14\ bits$
\# of Line Number Bits: P.A. Bits - (tag bits + offset) = 34 - (10 + 14) = 34 - 24 = 10 bits
\# of Cache Lines = 2^10
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
\# of Block in MM = $2^{32}\ bytes \div 2^{12}\ bytes = 2^{20}\ bytes$\
Block N. bits/# of Tag bits = $log_2(2^{20}) = 20\ bits$
- 20 Block # bits/Tag Bits; 12 bits Block/Line offset\
Cache Size = $2^{20}\ bytes$\
1. # of Line in Cache = $2^{20} \div 2^{12} = 2^8\ bytes$
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
\# of Blocks = $2^{34}\ bytes \div 2^{14}\ bytes = 2^{20}\ bytes$\
\# of Block bits = $log_2(2^{20}) = 20\ bits$
- Fully associative mapping; Tag bits and Block bits are equivalent
1. 20 Block/Tag bits; 14 block/line offset bits
2. Unable to determine:
    - Neither the Cache Size or the # of Lines in Cache were provided
    - Tag directory size can't be calculated if we don't know:
        - How many lines are in the cache
        - How many bits are being used in order to store the tag information

#flashcards/memory/mapping/associative/set/examples
Byte addressable MM Size: 256 MB
Cache Size: 1 MB
Block Size: 128 B
2-way Set Associative
1. P.A. split?
2. Tag directory size?
3. # of comparators needed & type of comparator?
?
P.A.S = $256\ MB = 2^{(8+20)} = 2^{28}\ bytes$
Block Size = $2^{7}\ bytes$
Offset = 7 bits
\# of Blocks in MM = $2^{(28 - 7)}\ = 2^{21}\ blocks$
Cache Size = $2^{20}\ bytes$
\# of lines = $2^{(20-7)} = 2^{13}$
No of sets = Number of lines $\div$ set size = $2^{(13-1)} = 2^{12}$
Tag bits = $28 - (12 + 7) = 9
1. 9 Tag bits; 12 Set # bits; 7 B/L offset bits
2. Tag directory size = $2^{13} \cdot 9 = 73728\ bits$
3. 2 (# of lines per set) 9-bit comparators (# of tag bits)

#flashcards/memory/mapping/associative/set/examples
Byte addressable MM Size: 4 MB
Block Size: 64 B
Tag bits: 10
4-way Set Associative
1. P.A. split?
2. Cache Size?
?
P.A.S = $4\ MB = 2^{(2+20)} = 2^{22}\ B$
P.A. bits = $log_2(2^{22}) = 22\ bits$
Block size = $64\ B = 2^6\ B$
B/L Offset = $log_2(2^6) = 6\ bits$
\# of MM Blocks = $2^{22} \div 2^6 = 2^{(22-6)} = 2^{16}$
Tag bits = 10
Set Size = 4 = $2^2$
Set # bits = $16 - 10 = 6$
1. 10 Tag bits; 6 Set # bits; 6 B/L Offset bits
\# of Sets = $2^6$
\# of Lines = # of Sets $\cdot$ set size = $2^6 \cdot 2^2 = 2^8$
2. Cache Size = $2^8 \cdot 2^6\ B = 2^{14}\ B = 2^4\ KB = 16\ KB$
    - Cache Size = (# of sets $\cdot$ Set Size) $\cdot$ Block Size

#flashcards/memory/mapping/associative/set/examples
Cache Size: 256 KB
Tag bits: 8
8-way Set Associative
- Byte addressable MM Size?
?
![[Cache Size Formula - Example.png]]

#flashcards/memory/mapping/associative/set/examples
MM Size: 128 KB
Cache Size: 16KB
Block Size: 256 B
Byte addressable memory
- P.A. split?
    1. 2-way Set Associative
    2. 4-way Set Associative
    3. 8-way Set Associative
?
MM Size = $128\ KB = 2^7 \cdot 2^{10} = 2^{17}\ B$
P.A. bits = $log_2(2^{17}) = 17\ bits$
Block Size = $256\ B = 2^8\ B$
B/L Offset = $log_2(2^8) = 8\ bits$
\# of MM Blocks = $2^{(17-8)} = 2^9$
Cache Size = $16\ KB = 2^{14}$
\# of Cache Line = $2^{(14-8)} = 2^6$
1. 2-way
    - # of sets = $2^{(6-1)} = 2^5$
    - Tag bits = $9 - 5 = 4$
        - 4 Tag bits; 4 Set bits; 8 B/L bits.
2. 4-way
    - # of sets = $2^{(6-2)} = 2^4$
    - Tag bits = $9 - 4 = 5$
        - 5 Tag bits; 4 Set bits; 8 B/L bits.
3. 8-way
    - # of sets = $2^{(6-3)} = 2^3$
    - Tag bits = $9-3 = 6$
        - 6 Tag bits; 3 Set bits; 8 B/L bits.
- Note that as the "way" increases the Set bits are reduced and the Tag bits increase.

#flashcards/memory/mapping/associative/set/examples
If the associativity of a processor cache is doubled while keeping the capacity and block size unchannged, which of of the following is guaranteed to be NOT affected?
A) Width of tag comparator
B) Width of set index decoder
C) Width of way selection multiplexer
D) Width of processor to main memory data bus
?
![[Gate CS 2014.png]]
Answer is D. We have not studied data buses at this time; however, utilizing the previous example we could find the answer through eliminating the other options.
Explanation: [timestamped link](https://youtu.be/-oaiLatXdXw?si=ArlbNN8BF7yca5-T&t=300)
