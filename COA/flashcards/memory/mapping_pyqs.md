---
id: mapping_pyqs
aliases: []
tags: []
---

- [ ] ---
id: mapping_pyqs
aliases: []
tags:
  - flalshcards/memory
---

#flashcards/memory/mapping/direct/pyqs
A direct mapped cache memory of 1 MB has a block size of 256 bytes.
The cache has an access time of 3 ns and a hit rate of 94%. During a cache miss, it takes 20 ns to bring the first word of a block from the main memory, while each subsequent word takes 5 ns.
The word size is 64 bits. The average memory access time in ns (round of to 1 decimal place) is:
?
Block Size = 256 B
Word Size = 64 bits = $8 \cdot 8 bits = 8 B$\
No of words per Block = $256\ B \div 8\ B = 2^8 \div 2^3 = 2^{8-3} = 2^5$
<br/>
$H_{cache} = 94\% = 0.94$\
$T_{cache} = 3\ ns$\
$T_{MM} = 20 ns for the 1st word, 5\ ns for the rest (for every block)$\
$T_{avg} = H_{cache}T_{cache} + (1-H_{cache})(T_{cache} + T_{MM})$\
$= 0.94 \cdot 3 + (1 - 0.94)(3+((20 \cdot 1) + ((2^5 - 1) \cdot 5)))\ ns$\
$= 2.82 + 0.06(3 + 20 + 155)\ ns = 2.82 + 0.06(178)\ ns$\
$= 2.82 + 10.68 = 13.5\ ns$\
<br/>
Answer: 13.5 ns

#flashcards/memory/mapping/direct/pyqs
Consider a machine with byte addressable main memory of $2^{20}\ bytes$, lock size of 16 bytes and a direct mapped cache having $2^{12}$ cache lines.
Let the addresses of two consecutive bytes in main memory be $(E201F)_{16}$ and $(E2020)_{16}$.
The cache index for the memory address $(E201F)_{16}$.
What are the tag and cache line address (in hex) for main memory address $(E201F)_{16}$?
?
Main Memory Size = $2^{20}\ bytes$\
\# of P.A. bits = $log_2\ 2^{20} = 20\ bits$\
<br/>
Block Size = 16 bytes\
Block Offset = $log_2\ 16 = 4\ bits$\
<br/>
\# of Cache Lines = $2^{12}$\
No of Line number bits= $log_2\ 2^{12} = 12\ bits$\
<br/>
No of Tag bits = P.A. bits - (Line # bits + offset) = $20 - (12 + 4) = 20 - 16 = 4\ bits$
<br/>
$E201F_{16} = 1110\ 0010\ 0000\ 0001\ 1111_2$\
<br/>
Tag in Hex = $1110 = E$\
Cache line address in hex = $0010\ 0000\ 0001 = 201$\

#flashcards/memory/mapping/direct/pyqs
Consider a machine with byte addressable memory of $2^{32}\ bytes$ divided into blocks of size 32 bytes. Assume a direct mapped cache having 512 cache lines is used with this machine. The size of tag field bits is:
?
Main Memory Size = $2^{32}\ bytes$\
\# of P.A. bits = $log_2\ 2^{32} = 32\ bits$\
<br/>
Block Size = 32 B = $2^5\ bytes$\
<br/>
\# of cache lines = 512 = $2^9$\
No of Line number bits = $log_2\ 2^9 = 9\ bits$
<br/>
No of Tag bits = P.A. bits - (Line # bits + offset) = $32 - (9 + 5) = 32 - 14 = 18\ bits$

#flashcards/memory/mapping/direct/pyqs
An 8 KB direct-mapped write-back cache is organized as multiple blocks, each of size 32 bytes.
The processor generates 32 bit addresses.
The cache controller maintains the tag information for each cache block comprising of the following.
1 Valid bit, 1 Modified bit.
As many bits as the minimum needed to identify the memory block mapped in the cache.
What is the total size of memory needed at the cache controller to store meta-data (tags) for the cache?
?
Cache size = 8 KB = $2^3 \cdot 2^{10} = 2^{3+10} = 2^{13}\ bytes$\
<br/>
Block size = 32 bytes = $2^5\ bytes$\
Block offset = $log_2\ 32 = 5\ bits$\
<br/>
\# of cache lines = $\frac{2^{13}}{2^5} = 2^{13-5} = 2^8$\
No of Line number bits = $log_2\ 2^8 = 8\ bits$\
<br/>
\# of P.A. bits = $log_2\ 2^{32} = 32\ bits$\
No of Tag bits = P.A. bits - (Line # bits + offset) = $32 - (8 + 5) = 32 - 13 = 19\\ bits$\
<br/>
Tag directory entriy $= 1 + 1 + 19 = 21\ bits$\
Tag directory size $= 21 \cdot 2^8 = 21 \cdot 256 = 5376\\ bits$
<br/>
Total size of memory needed at the cache controller to store meta-data (tags) for the cache = 5376 bits

#flashcards/memory/mapping/direct/pyqs
Consider a machine with a byte adressable main memory of $2^{16}$ bytes. Assume that a direct mapped data cache consisting of 32 lines of 64 bytes each is used in the system.
A 50 x 50 two-dimensional array is stored in the main memory starting from memory location 1100H.
Assume that the data cache is initially empty. The complete array is accessed twice.
Assume that the contents of the data cache do not change in between the two accesses.
<br/>
- How many cache misses will occur in total?
a) 40
5) 50
c) 56
d) 59
<br/>
- Which of the following line of the data cache wil be replaced by new blocks in accessing the array for the second time?
a) line 4 to 11
b) line 4 to line 7
c) line 0 to line 7
d) line 0 to line 8
?
Main Memory Size = $2^{16}\ bytes$\
\# of P.A. bits = $log_2\ 2^{16} = 16\ bits$\
<br/>
Block Size = 64 B = $2^6\ bytes$\
Block offset = $log_2\ 64 = 6\ bits$\
<br/>
\# of cache lines = 32\
No of Line number bits = $log_2\ 32 = 5\ bits$\
<br/>
No of Tag bits = P.A. bits - (Line # bits + offset) = $16 - (5 + 6) = 16 - 11 = 5\ bits$\
<br/>
Total number. of elements in the array = $50 \cdot 50 = 2500$\
Element size = 1 byte
Array size = 2500 bytes
\# of blocks to store in the array = $\frac{2500}{64} = 39.0625$\
Blocks are divided equally and we can't use 39.0625 blocks, so we use 40 blocks
\# of blocks = 40
<br/>
P.A. Split
| | $\leftarrow 16\ bits \rightarrow$ | |
|-|-|-|
| 5 bits | 5 bits | 6 bits |
| Tag | Line | Offset |
<br/>
<br/>
Array is stored in the main memory starting from 1100H (H denotes a hexidecimal number) which is 0001 0001 0000 0000 in binary
<br/>
Tag bits = 0001 0
Line bits = 00100
Offset bits = 000000
Line number is 4
<br/>
From this we know that the array is stored starting at line 4 onward.
40 blocks are required to store the entire array.
Let's call them $b_0, b_1, b_2, ..., b_{39}$
The following table represents the cache memory after the first access of the array.
<br/>
| Block | First Access | |
|-|-|-|
| 0 | $b_{28}$ | |
| 1 | $b_{29}$ | |
| 2 | $b_{30}$ | |
| 3 | $b_{31}$ | |
| 4 | ~~$b_0$~~ $b_{32}$ | |
| 5 | ~~$b_1$~~ $b_{33}$ | |
| 6 | ~~$b_2$~~ $b_{34}$ | |
| 7 | ~~$b_3$~~ $b_{35}$ | |
| 8 | ~~$b_4$~~ $b_{36}$ | |
| 9 | ~~$b_5$~~ $b_{37}$ | |
| 10 | ~~$b_6$~~ $b_{38}$ | |
| 11 | ~~$b_7$~~ $b_{39}$ | |
| 12 | $b_8$ | |
| ... | ... | ... |
| 30 | $b_{26}$ | |
| 31 | $b_{27}$ | |
- First iteration cache misses is 40 because the cache is empty.
<br/>
| Block | First Access | Second Access |
|-|-|-|
| 0 | $b_{28}$ | |
| 1 | $b_{29}$ | |
| 2 | $b_{30}$ | |
| 3 | $b_{31}$ | |
| 4 | ~~$b_0$~~ ~~$b_{32}$~~ | ~~$b_0$~~ $b_{32}$ |
| 5 | ~~$b_1$~~ ~~$b_{33}$~~ | ~~$b_1$~~ $b_{33}$ |
| 6 | ~~$b_2$~~ ~~$b_{34}$~~ | ~~$b_{2}$~~ $b_{34}$ |
| 7 | ~~$b_3$~~ ~~$b_{35}$~~ | ~~$b_{3}$~~ $b_{35}$ |
| 8 | ~~$b_4$~~ ~~$b_{36}$~~ | ~~$b_{4}$~~ $b_{36}$ |
| 9 | ~~$b_5$~~ ~~$b_{37}$~~ | ~~$b_{5}$~~ $b_{37}$ |
| 10 | ~~$b_6$~~ ~~$b_{38}$~~ | ~~$b_{6}$~~ $b_{38}$ |
| 11 | ~~$b_7$~~ ~~$b_{39}$~~ | ~~$b_{7}$~~ $b_{39}$ |
| 12 | $b_8$ | |
| ... | ... | ... |
| 30 | $b_{26}$ | |
| 31 | $b_{27}$ | |
- Second iteration cache misses is 16 because the cache is full.
<br/>
- \# of cache misses = 40 + 16 = 56
- line 4 to line 11

#flashcards/memory/mapping/associative/fully/pyqs
A certain processor uses a fully associative cache of size 16 KB, the cache block size is 16 bytes.
Assume that the main memory is byte addressable and uses a 32-bit address.
How many bits are required for the Tag and the Index fields respectively in the addresses generated by the processor?
A) 24 bits and 0 bits
B) 28 bits and 4 bits
C) 24 bits and 4 bits
D) 28 bits and 0 bits
?
Cache Size = $2^4 \cdot 2^{10} = 2^{14}$ bytes
Block Size = $16\ B = 2^4\ B$
Block Offset = 4
Line #/Index bits = $log_2(2^{14-4}) = 10$
P.A. bits = 32
Tag bits = $32 - 4 = 28$
- D: 28 bits and 0 bits

#flashcards/memory/mapping/associative/set/pyqs
A block-set associative cache memory consists of 128 blocks divided into four block sets.
The main memory consists of 16,384 blocks and each block contains 256 eight bit words.
1. How many bits are required for addressing the main memory?
2. How many bits are needed to represent the TAG, SET and WORD fields?
?
\# of Cache Lines = 128 = $2^7$
\# of MM Blocks = 12384 = $2^{14}$
\# of Words per Block = 256
Block Size = $256 \cdot 1\ B = 256\ B = 2^8\ B$
MM Size = $2^8\ words \cdot 2^{14}\ blocks = 2^{22}\ bytes$
1. P.A. bits = 22
WORD = 8 bits
4-way Set Associative
No of Sets = $2^{(7-2)} = 2^5$
2. 9 tag bits; 5 Set bits; 8 WORD bits.

#flashcards/memory/mapping/associative/set/pyqs
A computer has a 256 KB, 4-way set associative, write back data cache with block size of 32 B.
The processor sends 32 bit addresses to the cache controller.
Each cache tag directory entry contains, in addition to address tag, 2 valid bits, 1 modified bit and 1 replacement bit.
1. The number of bits in the tag field of an address is
    a) 11
    b) 14
    c) 16
    d) 27
2. The size of the cache tag directory is
    a) 160 Kbits
    b) 136 bits
    c) 40 Kbits
    d) 32 bits
?
P.A bits = 32
Block Size = $32\ B = 2^5\ B$
B/L Offset = 5
Cache Size = 256 KB = $2^8 \cdot 2^{10} = 2^{18}\ bytes$
\# of Lines = $2^{(18-5)} = 2^{13}$
\# of Sets = $2^{(13-2)} = 2^{11}$
Tag bits = 16 bits
1. 16 bits
Tag directory entry = $16 + 2 + 1 + 1 = 20\ bits$
Tag directory size = $2^{13} \cdot 20\ bits = 2^{13} \cdot 2^1 \cdot 10\ bits = 2^{14} \cdot 10\ bits = 2^4 \cdot 10 \cdot 2^{10}\ bits = 160\ Kbits$
2. 160 Kbits

#flashcards/memory/mapping/associative/set/pyqs
4-way Set Associative Cache
\# of Lines: 128
Line Size: 64 words
P.A. bits: 20
- P.A. split?
?
\# of Lines = 128 = $2^7$
Line Size = 64 words = $2^6\ words$
P.A. bits = 20 bits
Block Offset = 6
\# of Sets = $2^{(7-2)} = 2^5$
Tag bits = P.A. bits - (Set # bits + B/L Offset bits) = $20 - (5 + 6) = 20 - 11 = 9\ bits$
- P.A. split: 9 Tag bits; Set # bits 5; B/L Offset bits 6.

#flashcards/memory/mapping/associative/set/pyqs
In a k-way set associative cache, the cache is divided into v sets, each of which consist of k lines.
The lines of a set are placed in sequence one after another.
The lines in set s are sequenced before the lines in set (s+1). The main memory blocks are numbered 0 onwards.
The main memory block numbered j must be mapped to any one of the cache lines from:
a) $(j \mathbin{\%} v) \cdot k\ to\ (j \mathbin{\%} v) \cdot k + (k - 1)$
b) $(j \mathbin{\%} v)\ to\ (j \mathbin{\%} v) + (k - 1)$
c) $(j \mathbin{\%} k)\ to\ (j \mathbin{\%} k) + (v - 1)$
d) $(j \mathbin{\%} k) \cdot v\ to\ (j \mathbin{\%} k) \cdot v + (v - 1)$
?
- $(j \mathbin{\%} v) \cdot k\ to\ (j \mathbin{\%} v) \cdot k + (k - 1)$
Refactor question using [this](https://www.youtube.com/watch?v=AByFL521DRg&list=PLBlnK6fEyqRjdT1xkkBZSXKwFKqQoYhwy&index=18) explanation.

#flashcards/memory/mapping/all/pyqs
Consider two cache organizations: The first one is 32 KB 2-way set associative with 32-byte block size.
The second one is of the same size but direct mapped. The size of an address is 32 bits in both cases.
A 2-to-1 multiplexer has a latency of 0.6 ns while a kbit comparator has a latency of k/10 ns.
The hit latency of the set associative organization is h1 while that of the direct mapped one is h2.
1. The value of h1 is:
    a) 2.4 ns
    b) 2.3 ns
    c) 1.8 ns
    d) 1.7 ns
2. The value of h2 is:
    a) 2.4 ns
    b) 2.3 ns
    c) 1.8 ns
    d) 1.7 ns
?
Cache size = $32\ KB = 2^{15}\ B$
Block Size = $32\ B = 2^5\ B$
Block offset = 5 bits
Set Size = 2 lines
\# of lines = $2^{(15-5)} = 2^{10}$
\# of sets = $2^{(10-1)} = 2^9$
- 18 tag bits; 9 set bits; 5 B/L bits.
    - $2^9 \cdot 1$ MUX
    - How many?
        - 2 lines per set. 18 bits for the tags. Both lines inside each set will have 18 tag bits associated to each of them. With each input line of the MUX in can only read a single bit. For 18 bits, we will need 18 $2^9 \cdot 1$ MUX.
        - Moreover, it's a 2-way set associative, meaning we need to refer to all of the tags of all of the lines belonging to the same set.
            - $18 \cdot 2 = 36$ MUX
                - We need 36 $2^9 \cdot 1\ MUX$
Since we are using 18 bits for tags and it's 2-way set associative cache organization, we will need 2 18-bit comparators. The output of these two will be fed into an or gate.
2 input OR Gate
| A | B | O/P |
|-|-|-|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |
$$
\overline{A}B + A\overline{B} + AB
= \overline{A}B + A\ (\overline{B}+B)
= \overline{A}(B) + A(1)
$$
Multiplexers are functionally complete, so we can implement any of the above boolean functions.
In this scenario, if we consider B to be $I_0$ and 1 to be $I_1$ and keeping A for the select line, in that case when A will be low B or $I_0$ will be selected, and when A is high, 1 will be selected.
Thus, using this 2-to-1 multiplexer this function can be implemented. This is why the question has the 2-to-1 MUX which will replace the OR gate in the circuitry.
k = 18.
Comparator latency = 18/10 ns = 1.8 ns
1. 2.4 ns
    - 1.8 + 2-to-1 hit latency
        -   $1.8 + 0.6 = 2.4\ ns$
P.A. bits = 32
- P.A. split
    - 17 tag bits; 10 Line # bits; 5 B/L offset bits.
Line bits will be used as select lines for the MUX.
    - $2^{10} \cdot 1$ MUX
    - 17 needed
    - single 17-bit comparator needed
        - Latency = 17/10 ns
            - 1.7 ns
2. 1.7 ns
[^ Super confused about the boolean algebra section. Need to review before adding this card. Card unfinished due to skill issue.]
Refactor with [this](https://www.youtube.com/watch?v=F_gOWc50MtI&list=PLBlnK6fEyqRjdT1xkkBZSXKwFKqQoYhwy&index=20)

#flashcards/memory/mapping/associative/set/pyqs
A 4-way set-associative cache memory unit with a capacity of 16 KB is built using a block size of 8 words.
The word length is 32 bits. The size of the physical address space is 4GB.
The number of bits for the TAg field is:
a) 5
b) 15
c) 20
d) 25
?
P.A.S = $4^{(2+30)} = 2^{32}$
Word Size = 32 bits = $4 \cdot 8\ bits = 4\ B$
Block Size = 8 words = $2^3 \cdot 4\ B = 2^{(3+2)} = 5\ B$
B/L Offset = $log_2^{(2^5)} = 5$
Cache Size = $2^{(4+10)} = 2^{14}$
\# of Lines = $2^{(15-5)} = 2^9$
\# of Sets = $2^{(9-2)} = 2^7$
- 20 tag bits; 7 Set # bits; 5 B/L Offset bits
This is a trick question though. "The word length is 32 bits" so it is not byte addressable (8 bit words, or one byte).
We need to instead convert every unit to word.
Word Size = 32 bits = $4 \cdot 8\ bits = 4\ B$
P.A.S = $4\ GB = 4\ GB \div 4\ B = 1\ GW = 2^{30}\ W$
Block Size = 8 words = $2^3\ W$
Cache Size = 16 KB = $16\ KB \div 4\ B = 4\ KW = 2^{12}\ W$
\# of Lines = $2^{(12-3)} = 2^9\ W$
\# of Sets = $2^{(9-2)} = 2^7$
- Tag bits 20; 7 Set # bits; 3 B/L Offset bits
Though this specific question results in the same number of tag bits, note the different P.A. split.
Answer: C - 20 bits

#flashcards/memory/mapping/associative/set/pyqs
The size of the physical address space of a processor is $2^P\ bytes$. The word length is $2^W\ bytes$.
The capacity of cache memory is $2^N\ bytes$. The size of each cache block is $2^M\ words$.
For a k-way set-associative cache memory, the length (in number of bits) of the tag field is:
a) $P - N - log_2K$
b) $P - N + log_2K$
c) $P - N - M - W - log_2K$
d) $P - n - M - W + log_2K$
?
P.A.S = $2^P\ B = 2^P \div 2^W = 2^{P-W}$
Word Size = $2^W\ B$
Cache Size = $2^N \div 2^W = 2^{N-W}\ words$
Block Size = $2^M\ words$
B/L Offset = M
\# of Lines = $2^{(N-W)} \div 2^M = 2^{(N-W-M)}$
$K = 2^X$
\# of Sets = $2^{(N-W-M)} \div 2^X = 2^{(N-W-M) - X}$
\# of Set bits = $N-W-M-X$
Because X is our own variable and not given, let's replace it with items given in the example.
$X = log_2K$
\# of Sets = $2^{(N-W-M)} \div 2^X = 2^{(N-W-M) - log_2K}$
\# of Set bits = $N-W-M-log_2K$
\# of Tag bits = $(P-W) - ((N-W-M-log_2K) + M) = P-W - N+W+M+log_2K-M$
- $P-N+log_2K$
