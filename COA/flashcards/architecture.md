---
id: architecture
aliases: []
tags:
  - flashcards/architecture
---


#flashcards/architecture/basics
Computer Archicecture::It is the design of computers, including their instruction sets, hardware components and system organization.

#flashcards/architecture/basics
What are the two main components of computer architecture:
?
1. Instruction Set Architecture (ISA)
2. Hardware System Architecture (HSA)

#flashcards/architecture/basics
Instruction Set Architecture (ISA)
?
- The interface between the hardware and the software. It is the set of instructions that a computer can execute. It is the most important abstraction in computer architecture.
- It is the boundary between the hardware and the software. It is the contract between the hardware and the software

#flashcards/architecture/basics
Hardware System Architecture (HSA)::It is the actual hardware implementation of the computer. It includes the components like CPU, memory, I/O devices, etc.

#flashcards/architecture/basics
Instruction Set Architecture example:
?
MOV R1, O2H
MOV R2, 03H
ADD R1, R2
STORE X, R1

#flashcards/architecture/basics
Hardware System Architecture example::ADDER

#flashcards/architecture/history
Who created the Anaylitial Engine and when?::Charles Babbage in 1837
What is Charles Babbage known for?::He is known for creating the first general-purpose computer, the Analytical Engine.
Who assisted Charles Babbage in creating the Analytical Engine?::Ada Lovelace
What is Ada Lovelace known for?::She was the first one to propose programming languages.
Who tutored Ada Lovelace?::Augustus De Morgan
What is Augustus De Morgan known for?::De Morgan's Laws revolutionized Boolean Algebra.
Who proposed the idea of computability and non-computability?::Alan Turing
Who proposed the idea of the stored program concept?::Johann Von Neumann

#flashcards/architecture/history
What is Alan Turing known for?
?
He is known for creating the Turing Machine, which is the theoretical model of a computer.
He is also known for breaking the Enigma code during World War II.
He is considered the father of computer science.

#flashcards/architecture/history
Johann Von Neumann facts
?
He was a child prodigy who was able to divide 8 digit numbers by 8 digit numbers at the age of 6.
He worked full time at Princeton by the age of 30.
He proposed the Von Neumann Architecture.
He offered Turing a research assistant position under his supervision in quantum mechanics at the Institute of Advanced Studies.

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
