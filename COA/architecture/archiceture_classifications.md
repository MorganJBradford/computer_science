---
id: archiceture_classifications
aliases: []
tags: []
---

# Von-Neumann Architecture (Princeton Architecture)
?
## CPU
## Memory
## I/O

# Non-Von-Neumann Architecture
?
## Harvard Architecture:
### Used separate memory units for data and instructions
### Pioneered Parallel Processing
## Modified Harvard Architecture:
### Cannot be classified as Von-Neumann or Harvard as it has features of both

# Hardvard Architecture:
?
## Separate memory units
## One for data
## One for instructions
## Faster than Von-Neumann
## Used in DSPs, Microcontrollers, etc.

# Modified Harvard Architecture:
?
## Cache memory is used to store both data and instructions
## Used in modern computers

# SISD (Single Instruction [stream], Single Data [stream]):
?
## Von-Neumann Architecture belongs to this category
## Has one CPU which executes one instruction at a time

# SIMD (Single Instruction [stream], Multiple Data [streams]):
?
## Processor array belongs to this category
## Multiple CPUs execute the same instruction on different data
## More than one ALU (Arithmetic Logic Unit)

# MISD (Multiple Instruction [streams], Single Data [stream]):
?
## Not used in practice
## Multiple CPUs execute different instructions on the same data

# MIMD (Multiple Instruction [streams], Multiple Data [streams]):
?
## Multiprocessor systems belong to this category
## Multiple CPUs execute different instructions on different data

## MIMD can be classified as
?
### SMP (Symmetric Multiprocessing)
### NUMA (Non-Uniform Memory Access)
### Clusters
### Grids
### Cloud Computing

## Proposed by Flynn in 1966
### Also known as Flynn's Taxonomy
