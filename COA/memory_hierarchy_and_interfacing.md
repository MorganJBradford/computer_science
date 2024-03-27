---
id: memory_hierarchy_and_interfacing
aliases: []
tags: []
---

# Memory Hierarchy

## Access Time | Size
   >>>> Registers
   >>> S.R.A.M
   >> Main Memory
   >> D.R.A.M
   > Secondary Memory

## Cost | Usage Frequency
   >>>> Secondary Memory
   >>> Main Memory
   >>> D.R.A.M
   >> S.R.A.M
   > Registers

# Memory Interfacing:
  - Part of Computer Organization.
  - Deals with the way of connecting various level of Memory units to Processor & I/O peripherals.
  - The speed of the processor is counted using the unit MIPS.

  $ MIPS: Million Instructions Per Second

  nth Level ⊆ (n+1)th Level

  CPU |----> nth level |----> (n+1)th level
  - if data is found in nth level, then it is called as Hit.
  - if data is not found in nth level, then it is called as Miss then move to (n+1)th level.

  Method 1 of interfacing:
## CPU is connected to all levels of memory simultaneously.
## When the CPU wants to access the data, it will check in all levels of memory.

### If we have memory units:
#### M1, M2, M3
### Acces Time:
#### T1, T2, T3
##### T1 < T2 < T3
### Hit Ratio:
#### H1, H2, H3
##### H1 > H2 > H3

### This is known as Effective/Average Memory Acces Time (T avg):
#### H<sub>1</sub> T<sub>1</sub> + ((1-H<sub>1</sub>)*H<sub>2</sub>) T<sub>2</sub> + ((1-H<sub>1</sub>) * (1-H<sub>2</sub>))T<sub>3</sub>

     ^ Because the memory units are connected to the CPU simultaneously, which is why these checks will run in parallel.
     - So, the time taken to access the data will be the time taken to access the data from the memory unit which has the highest hit ratio.

     > Total no. of Instructions = 100
     > No. of Instructions found in nth level = 80
     > MM's Hit Ratio = 80/100 = 0.8 = 80%


     Method 2 of interfacing:
## CPU is connected to only one level of memory at a time.
## When the CPU wants to access the data, it will check in the memory unit which is connected to the CPU.
### Effective Memory Access Time (T avg):
#### H<sub>1</sub>H<sub>1</sub> + ((1-H<sub>1</sub>) * H<sub>2</sub>) (H<sub>1</sub>+T<sub>2</sub>) + ((1-H<sub>1</sub>) * (1-H<sub>2</sub>)) (H<sub>1</sub>+T<sub>2</sub>+T<sub>3</sub>)
