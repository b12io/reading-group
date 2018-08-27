# Reading: Spectre
* [Paper](https://spectreattack.com/spectre.pdf)

# Questions I have going in
* How was spectre different from meltdown?
* What about the attack makes it impossible to create a patch for?

# Notes
* Demonstrated attack using native code, JavaScript in a browser, and eBPF
* At a high level, attacker locates a sequence of instructions within the victim process's address space which, when executed, acts as covert channel transmitter that leaks the victim's memory or register contents. The attacker than tricks the CPU into speculatively and erroneously executing this instruction sequence. Finally, the attacker retrieves the leaked information over the covert channel.
* Variant 1: exploiting conditional branches
  * Attacker mistrains branch predictor to mispredict direction of a branch, allowing an attacker to read secret info stored in the program's address space
  * Ex. `if ( x < arraysize)`. Mistrains this branch by inputiing several valid values, then inputs one that is out of bounds
* Variant 2: exploiting indirect branches
  * Attacker chooses a *gadget* from the victim's address space and mistrains the branch predictor to go there. The attacker mistrains by performing indirect branches to this address space in it's own address space. Doesn't matter what resides there.
* Other variants: further attacks can be designed by varying the method of achieving speculative execution and the method used to leak the information.
* Imperically verified on several Intel processors
* Comparison with Meltdown
  * Meltdown doesn't use branch prediction
  * Exploits out of order instruction execution after accessing kernel memory from user space triggers an exception to leak contents of accessed memory through a cache covert channel
  * The Spectre attack reads memory from victim memory, not from kernel memory. So it can't be fixed by just adding a kernel space bit check, or the KAISER mechanism
* *Speculative execution*: out of order execution reaches a conditional branch. Makes a prediction for which path to follow and speculatively executes instructions along that path. On one processor, reorder buffer has space for 192 micro ops
* *Direct and indirect branches*: Indirect branch instructions can jump to arbitrary target addresses computed at runtime
* *Branch target buffer*: map of address if branch instruction to destination address 
* Branch prediction logic is typically not shared across physical cores
