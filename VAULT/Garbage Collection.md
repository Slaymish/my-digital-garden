# Garbage Collection

Related: #programming #java
Hamish Burke || 01-02-2023
***


Without garbage collection:
- ask and release memory yourself.
- like c++ etc
- [[Memory Leaks]]


older 'reference counters'
- Semi automatic mem management
- counts amount of memory using/not using
- when count goes back to zero, it automatically frees that memory
- can be prone to [[Memory Leaks]]
- slow

***

## Garbage Collection

- Automatic memory management
- More accurately able to know when you've finished using the memory

<h2 align="center">

Algorithm to manage memory

</h2>

<p align="center">
	Is it reachable?
</p>


- work out whats live memory (mark it)
- sweep and free all unmarked memory

Proble






