---
id: memory_hierarchy_and_interfacing
aliases: []
tags: []
---

# Memory Hierarchy

![[Memory Hierarchy.png]]

<dl>
    <dt>Memory Hierarchy:</dt>
    <dd>It is the way of organizing the memory units in a computer system.</dd>
    <dd>Deals with the way of connecting various levels of memory units to the processor and I/O peripherals.</dd>
</dl>
- The speed of the processor is counted using the unit MIPS
- $n

<dl>
    <dt>MIPS:</dt>
    <dd>Million Instructions Per Second</dd>
</dl>

$n^{th}$ Level $\subseteq$ $(n+1)^{th}$ Level
- CPU $\rightarrow\ n^{th}$ level $\rightarrow (n+1)^{th}$ level
    - if data is found in nth level, then it is called as Hit.
    - if data is not found in nth level, then it is called as Miss then move to $(n+1)^{th}$ level.

<dl>
    <dt>
        Simultaneos Memory Access:
    </dt>
    <dd>
        CPU is connected to all levels of memory simultaneously.
    </dd>
    <dd>
        When the CPU wants to access the data, it will check in all levels of memory.
    </dd>
</dl>
- This Arrangment is often found in systems with hierarchical memory architectures, such as multi-level cache systems.

If we have memory units:
M1, M2, M3

Access Time:
T1, T2, T3
- T1 < T2 < T3

Hit Ratio:
H1, H2, H3
- H1 > H2 > H3

Effective/Average Memory Access Time ($T_{avg}$):
- $H_1 T_1 + ((1-H_1)\cdot H_2) T_2 + ((1-H_1) \cdot (1-H_2))T_3$

- Because the memory units are connected to the CPU simultaneously, which is why these checks will run in parallel
    - So, the time taken to access the data will be the time taken to access the data from the memory unit which has the highest hit ratio.
- Total no. of Instructions = 100
- Example:
    - # of Instructions found in nth level = 80
    - MM's Hit Ratio = 80/100 = 0.8 = 80%

<dl>
    <dt>
        Hierarchical Memory Access:
    </dt>
    <dd>
        CPU is connected to only one level of memory at a time.
    </dd>
    <dd>
        When the CPU wants to access the data, it will check in the memory unit which is connected to the CPU.
    </dd>
</dl>
- Common in many computer architectures and is based on the principle of locality of reference.
- Effective Memory Access Time (T avg):
- $H_1T_1 + ((1-H_1) \cdot H_2) (H_1+T_2) + ((1-H_1) \cdot (1-H_2)) (H_1+T_2+T_3)$
