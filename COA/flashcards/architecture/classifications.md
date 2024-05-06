---
id: classifications
aliases: []
tags:
  - flashcards/architecture
---

#flashcards/architecture/classifications
What components comprise Von-Neumann Architecture (Princeton Architecture)?
?
-   CPU
-   Memory
-   I/O

#flashcards/architecture/classifications
What are the types of Non-Von-Neumann Architecture?
?
- Harvard Architecture:
    - Used separate memory units for data and instructions
    - Pioneered Parallel Processing
- Modified Harvard Architecture:
    - Cannot be classified as Von-Neumann or Harvard as it has features of both

#flashcards/architecture/classifications
How is the Harvard Architecture organized?
?
- Separate memory units
    - One for data
    - One for instructions
- Faster than Von-Neumann
- Used in DSPs, Microcontrollers, etc.

#flashcards/architecture/classifications
Modified Harvard Architecture facts
?
- Cache memory is used to store both data and instructions
- Used in modern computers

#flashcards/architecture/classifications
SISD (Single Instruction [stream], Single Data [stream]) facts
?
- Von-Neumann Architecture belongs to this category
- Has one CPU which executes one instruction at a time

#flashcards/architecture/classifications
SIMD (Single Instruction [stream], Multiple Data [streams]) facts
?
- Processor array belongs to this category
- Multiple CPUs execute the same instruction on different data
- More than one ALU (Arithmetic Logic Unit)

#flashcards/architecture/classifications
MISD (Multiple Instruction [streams], Single Data [stream]) facts
?
- Not used in practice
- Multiple CPUs execute different instructions on the same data

#flashcards/architecture/classifications
MIMD (Multiple Instruction [streams], Multiple Data [streams]) facts
?
- Multiprocessor systems belong to this category
- Multiple CPUs execute different instructions on different data

#flashcards/architecture/classifications
Which category does the Von-Neumann Architecture belong to?::SISD
Which category does the Processor Array belong to?::SIMD
Which category does the Multiprocessor system belong to?::MIMD
Which category is used in modern computers?::Modified Harvard Architecture
Which category is not used in practice?::MISD

#flashcards/architecture/classifications
MIMD can be classified as
?
- SMP (Symmetric Multiprocessing)
- NUMA (Non-Uniform Memory Access)
- Clusters
- Grids
- Cloud Computing
- facts:
    - Proposed by Flynn in 1966
        - Also known as Flynn's Taxonomy
