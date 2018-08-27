# Reading: Spectre
* [Paper](https://spectreattack.com/spectre.pdf)

# Takeaways
* The Spectre attack:
  * Locates a sequence of instructions within the victim process's address space which, when executed, acts as covert channel transmitter that leaks the victim's memory or register contents
  * Tricks the CPU into speculatively and erroneously executing this instruction sequence.
  * Retrieves the leaked information over the covert channel.
* The paper empirically tested the attack with two variants: exploiting conditional branches and exploiting indirect branches.
* The two variants were tested on a variety of hardware, from Intel processors to AMD and ARM-based Samsung and Qualcomm processors found on mobile phones.
* Some mitigation techniques for attacking using JavaScript in a browser seem relatively easy to implement and are already used by Google Chrome and WebKit (limiting access to secret data, limiting extraction from covert channels by degrading timer resolution). Mitigation techniques for native code seem heavy-weight (preventing spectulative execution for unsafe branches) or are not feasible with current processors (preventing data from entering covert channels).

# Questions I have going in
* How was spectre different from meltdown?
* What about the attack makes it impossible to create a patch for?

# Notes
* Demonstrated attack using native code, JavaScript in a browser, and eBPF
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
