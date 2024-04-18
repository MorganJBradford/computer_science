---
id: architecture
aliases: []
tags:
  - flashcards/architecture
---


#flashcards/architecture/basics
Computer Archicecture::It is the design of computers, including their instruction sets, hardware components and system organization.

#flashcards/architecture/basics
There are two main components of computer architecture:
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
MOV r2, 03H
ADD R1, R2
STORE X, R1

#flashcards/architecture/basics
Hardware System Architecture example::ADDER

#flashcards/architecture/basics
_History_
?
> Analytical Engine (1837) - Charles Babbage:
>> First general-purpose computer
>> Assisted by Ada Lovelace
>>> First one to propose programming languages
>>> Was tutored by Augustus De Morgan
>>>> De Morgan's Laws revulutionized Boolean Algebra (George Boole)
> Alan Turing (1936) - Computability and Non-Computability
> Johann Von Neumann (1945) - Stored Program Concept
>> Child prodigy
>> Was able to divide 8 digit numbers by 8 digit numbers at the age of 6
>> Worked full time at Princeton by the age of 30
>> Proposed the Von Neumann Architecture
>>> Offered Turing a research assistant position under his supervision in quantum mechanics at the intitute of advanced studies

#flashcards/architecture/classifications
# Von-Neumann Architecture (Princeton Architecture)
?
## CPU
## Memory
## I/O

#flashcards/architecture/classifications
# Non-Von-Neumann Architecture
?
## Harvard Architecture:
### Used separate memory units for data and instructions
### Pioneered Parallel Processing
## Modified Harvard Architecture:
### Cannot be classified as Von-Neumann or Harvard as it has features of both

#flashcards/architecture/classifications
# Hardvard Architecture:
?
## Separate memory units
## One for data
## One for instructions
## Faster than Von-Neumann
## Used in DSPs, Microcontrollers, etc.

#flashcards/architecture/classifications
# Modified Harvard Architecture:
?
## Cache memory is used to store both data and instructions
## Used in modern computers

#flashcards/architecture/classifications
# SISD (Single Instruction [stream], Single Data [stream]):
?
## Von-Neumann Architecture belongs to this category
## Has one CPU which executes one instruction at a time

#flashcards/architecture/classifications
# SIMD (Single Instruction [stream], Multiple Data [streams]):
?
## Processor array belongs to this category
## Multiple CPUs execute the same instruction on different data
## More than one ALU (Arithmetic Logic Unit)

#flashcards/architecture/classifications
# MISD (Multiple Instruction [streams], Single Data [stream]):
?
## Not used in practice
## Multiple CPUs execute different instructions on the same data

#flashcards/architecture/classifications
# MIMD (Multiple Instruction [streams], Multiple Data [streams]):
?
## Multiprocessor systems belong to this category
## Multiple CPUs execute different instructions on different data

#flashcards/architecture/classifications
## MIMD can be classified as
?
### SMP (Symmetric Multiprocessing)
### NUMA (Non-Uniform Memory Access)
### Clusters
### Grids
### Cloud Computing
## Proposed by Flynn in 1966
### Also known as Flynn's Taxonomy
