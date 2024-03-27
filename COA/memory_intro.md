---
id: memory_intro
aliases: []
tags: []
---

Memory
: The faculty of the brain by which data or information is encoded, stared, and rtieved when needed -- Wikipedia

# Image, audio, text, instructions for a key press or a mouse click are all stored as bits in memory. Each memory cell can have either 0 or 1.
## All of these are comprised of millions of bits and processed by the CPU.

# Should we have one giant block of memory or should we have multiple blocks of memory?
## As the size of memory increases, the time taken to access the memory also increases. So, we have multiple blocks of memory.

   > Frequency: 2 GHz
   >> Time: $\frac 1{Frequency} = 0.5\ ns \\$
   >> $= 1/2x10^9 = 0.5x10^-9 = 0.5 ns\ $
   >>> How did we get the exponent?


| Prefix | Units | Add Expressions  | Final Expressions         |
|--------|-------|------------------|----------------------------|
| 1 Kilo Unit    | 1000 Unit        | $10^3 <Unit>$ | $10^3 <Unit>$  |
| 1 Mega <Unit>  | 1000 Kilo <Unit> | $10^3 \cdot 10^3$ | $10^6 <Unit>$  |
| 1 Giga <Unit>  | 1000 Mega <Unit> | $10^6 \cdot 10^3$ | $10^9 <Unit>$  |
| 1 Tera <Unit>  | 1000 Giga <Unit> | $10^9 \cdot 10^3$ | $10^{12} <Unit>$ |


# Primary Memory:
## It is the main memory of the computer.
## It is volatile memory.
## It is used to store data and instructions that are currently being executed by the CPU.
## It is also known as RAM (Random Access Memory) - Actually called DRAM (Dynamic RAM).
## It is faster than secondary memory.
## It is directly accessed by the CPU.
# Secondary Memory:
## It is non-volatile memory | It retains data even when the computer is turned off.
## It is slower than primary memory.
## Bigger in size.
## Cost-effective.
## Semi-Random Accessibility.
## It is used to store data and instructions that are not currently being executed by the CPU.
## It is not directly accessed by the CPU.
## It is also known as hard disk.
### Slower because it is a mechanical device.
#### It has:
##### a spinning disk.
##### a read/write head.
#### The read/write head moves to the location of the data that needs to be read or written.
#### This movement takes time (seek time).
# Cache Memory:
## It is a small block of memory that is used to store frequently accessed data.
## It is volatile memory.
## It is faster than primary memory.
## It is directly accessed by the CPU.
## It is also known as SRAM (Static RAM).

```
   |----------------------------------------------------------------------------------------------------|
   |--------------------------|  Cache Memory Mapping   |---------- Virtual Memory Mapping  ------------|
   | Processor | <--> | Cache | <--Words (or blocks)--> | Main Memory | <-- Pages --> | Secondary Memory |
   | Processor | <------------------------------------> | Main Memory | <-- Pages --> | Secondary Memory |
   |----------------------------------------------------------------------------------------------------|
```
