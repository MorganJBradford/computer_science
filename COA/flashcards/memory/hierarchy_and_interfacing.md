---
id: hierarchy_and_interfacing
aliases: []
tags:
  - flashcards/memory
---

#flashcards/memory/hierarchy_and_interfacing
# Memory Interfacing:
?
- Part of Computer Organization.
  - Deals with the way of connecting various level of Memory units to Processor & I/O peripherals.
  - The speed of the processor is counted using the unit MIPS.

#flashcards/memory/hierarchy_and_interfacing
What does MIPS stand for?::Million Instructions Per Second

#flashcards/memory/hierarchy_and_interfacing
If our CPU is connected to multiple levels of memory simultaneously, how would we calculate the average memory access time for the following?
?
- If we have memory units: M1, M2, M3
- Acces Time:
    - T1, T2, T3
        - T1 < T2 < T3
- Hit Ratio:
    - H1, H2, H3
        - H1 > H2 > H3
        ?
$H_1 T_1 + ((1-H_1)\cdot H_2) T_2 + ((1-H_1) \cdot (1-H_2))T_3$\
        [^Because the memory units are connected to the CPU simultaneously, which is why these checks will run in parallel]
- So, the time taken to access the data will be the time taken to access the data from the memory unit which has the highest hit ratio.
     - Total no. of Instructions = 100
     - # of Instructions found in nth level = 80
     - MM's Hit Ratio = 80/100 = 0.8 = 80%


#flashcards/memory/hierarchy_and_interfacing
If our CPU is connected to only one level of memory at a time, how would we calculate the average memory access time for the following?
?
$H_1T_1 + ((1-H_1) \cdot H_2) (H_1+T_2) + ((1-H_1) \cdot (1-H_2)) (H_1+T_2+T_3)$

#flashcards/memory/hierarchy_and_interfacing
A cache memory needs an access time of 30 ns and main memore of 150 ns, what is the average access time of CPU (assume hit ration = 80%)?
- Parallel Organization
?
Assume both the cache and main memory are simultaneously connected to the proccesor.
| Access Time | Hit Ratio |
|-------------|-----------|
| $T_{cache} = 30 \ ns$ | $H_{cache}$ = 80% = 0.8 |
| $T_{MM} = 150 \ ns$ |
| $T_{avg} = H_{cache}T_{cache} + (1-H_{cache})T_{MM} \\ = 0.8 \cdot 30 + (1-0.8)\cdot150 \ ns \\ = 24 + 0.2 \cdot 150 = 54\ ns$ |

#flashcards/memory/hierarchy_and_interfacing
A cache memory needs an access time of 30 ns and main memore of 150 ns, what is the average access time of CPU (assume hit ration = 80%)?
- Level wise organization
?
Assume only one memory unit is connected to the CPU at a time.
- Level wise organization
| Access Time | Hit Ratio |
|-------------|-----------|
| $T_{cache} = 30 \ ns$ | $H_{cache}$ = 80% = 0.8 |
| $T_{MM} = 150 \ ns$ |
| $T_{avg} = H_{cache}T_{cache} + (1-H_{cache})(T_{cache}+T_{MM})$ |
| $= 0.8 \cdot 30 + (1-0.8)(30+150) \ ns$ |
| $= 24 + 0.2 \cdot 180 = 24 + 36 = 60\ ns$ |

#flashcards/memory/hierarchy_and_interfacing
Assume that for a certain processor, a read request takes 50 ns on a cache miss and 5 ns on a cache hit.
- Suppose while running a program, it was observed that 80% of the processor's read requests result in a cache hit.
- The average read access time in ns is:
?
| Access Time | Hit Ratio |
|-------------|-----------|
| $T_{cache}+T_{MM} = 50\ ns$ | $H_{cache}$ = 80% = 0.8 |
| $T_{cache} = 5\ ns$ |
| $T_{avg} = H_{cache}T_{cache} + (1-H_{cache})(T_{cache}+T_{MM})$ |
| $= 0.8 \cdot 5 + (1-0.8)\cdot 50\ ns$ |
| $= 4 + 0.2 \cdot 50 = 4 + 10 = 14\ ns$ |

#flashcards/memory/hierarchy_and_interfacing
Memory Hierarchy: Access Time | Size
?
1. Registers
2. S.R.A.M
3. Main Memory (D.R.A.M)
4. Secondary Memory

#flashcards/memory/hierarchy_and_interfacing
Memory Hierarchy: Cost | Usage Frequency
?
1. Secondary Memory
2. Main Memory D.R.A.M
3. S.R.A.M
4. Registers
