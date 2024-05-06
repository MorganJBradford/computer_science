---
id: intro
aliases: []
tags:
  - flashcards/memory
---

#flashcards/memory/intro
Memory::The faculty of the brain by which data or information is encoded, stored, and retrieved when needed -- Wikipedia

#flashcards/memory/intro
Primary Memory:
?
- It is the main memory of the computer.
- It is volatile memory.
- It is used to store data and instructions that are currently being executed by the CPU.
- It is also known as RAM (Random Access Memory) - Actually called DRAM (Dynamic RAM).
- It is faster than secondary memory.
- It is directly accessed by the CPU.

#flashcards/memory/intro
Secondary Memory:
?
- It is non-volatile memory (retains data even when the computer is turned off).
- It is slower than primary memory.
- Bigger in size.
- Cost-effective.
- Semi-Random Accessibility.
- It is used to store data and instructions that are not currently being executed by the CPU.
- It is not directly accessed by the CPU.
- It is also known as hard disk.
    - Slower because it is a mechanical device.
        - It has:
            - a spinning disk.
            - a read/write head.
        - The read/write head moves to the location of the data that needs to be read or written.
        - This movement takes time (seek time).

#flashcards/memory/intro
Cache Memory:
?
- It is a small block of memory that is used to store frequently accessed data.
- It is volatile memory.
- It is faster than primary memory.
- It is directly accessed by the CPU.
- It is also known as SRAM (Static RAM).

#flashcards/memory/intro
Memory Mapping Table:
?
| | | | Cache Memorry Mapping | | Virtual Memory Mapping | |
|-|-|-|-|-|-|-|
| Processor | $\leftrightarrow$ | Cache | $\leftarrow$Words (or blocks)$\rightarrow$ | Main Memory | $\leftarrow Pages \rightarrow$ | Secondary Memory |
| Processor | $\leftarrow$ | -------- | $\rightarrow$ | Main Memory | $\leftarrow Pages \rightarrow$ | Secondary Memory |
