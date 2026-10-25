# Field notes: Stamp

**GCC compiler hardening documentation**

## Where the overwrite lands

A memory overwrite is a boundary mistake with visible consequences. A C structure lays its members out in address order, with possible alignment padding. If a program reads into a character array while using the size of its enclosing structure, later members can be changed even when the overall read remains inside allocated memory. That distinction separates a real field overflow from a crash caused by writing past the whole object.

First inspect the source and record the offsets of every field. Then compare the maximum accepted input length with the name-array length. In a debugger, send progressively longer patterns and observe the rejected-ticket diagnostic. The two values together explain the overwrite. Endianness matters when bytes represent a multi-byte integer: on x86-64 the least significant byte is stored first.

For safe practice, use only this local or event instance. Modern compilers add stack canaries and other checks, but a neighboring field can still be corrupted without overwriting a return address. The useful lesson is to bound each read by the destination member’s capacity and validate all authorization fields after parsing.

Learning reference: [GCC instrumentation options](https://gcc.gnu.org/onlinedocs/gcc/Instrumentation-Options.html).

---
*AIRANGE Learning Lab · Medium · Use authorized challenge files only.*
