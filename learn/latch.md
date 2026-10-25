# Field notes: Latch

**Static analysis, bit operations and reversible transforms**

## Read the transformation in both directions

A stripped executable preserves machine instructions while discarding much source-level metadata. Start with strings, imports, function boundaries, and the input loop. A small validation routine often combines a fixed-length check with a per-byte transform. Translate each instruction into a simple equation before guessing values.

A rotate is reversible: rotating left by *k* bits is undone by rotating right by the same amount. XOR is its own inverse. If the code computes `rotate_left(input XOR mask)`, reverse the rotation first, then XOR the same mask. Repeat the equation for each byte and inspect how its mask depends on the position.

The binary also transforms the output after a successful check. Recovering the accepted input is therefore only half the analysis. Trace the output loop and undo its position-dependent operation. Static analysis can recover both transformations without running unknown programs; this training binary is harmless and contains no network or persistence code.

Learning reference: [Ghidra official project](https://github.com/NationalSecurityAgency/ghidra).

---
*AIRANGE Learning Lab · Medium · Use authorized challenge files only.*
