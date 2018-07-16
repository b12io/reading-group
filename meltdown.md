# Reading: Meltdown
* [Paper](https://meltdownattack.com/meltdown.pdf)
* [Adrian Colyer's helpful summary](https://blog.acolyer.org/2018/01/15/meltdown/)


# 3 Takeaways
* Through a side-channel attack, Meltdown takes advantage of a performance feature of modern CPUs called out-of-order execution to get access to memory reserved for the kernel, as well as memory used by other proesses. Memory used by the kernel and other process should not be accessible to the application.
* Because the exploit depends on a feature of modern CPUs that turns out to be a vulnerability due to side-channels, it affects all operating systems running on those CPUs. The paper shows that on an operating system like Linux or OS X, the entire physical memory can be read. This includes reading the memory of sandboxed processes that should be protected by things like containers/virtualization.
* Luckily, and unlike the related Spectre attack, Meltdown can largely be avoided through a countermeasure called KAISER that was developed a year earlier for the Linux kernel. At this point, the major operating systems all have similar patches available to protect against Meltdown, albeit by incurring a performance penalty.

# Questions I have going in
* What is the difference between out-of-order execution (apparently what Meltdown exploits) and speculative execution (apparently what Spectre exploits)?

# Overall notes
* Section 2 is a great recap (or introduction) to computer architecture/organization classes. Each program has access to virtual memory addresses, which are mapped to physical memory by way of translation tables that are swapped out at each context (program) switch. The kernel's memory (kernel space) is also accessible in each virtual address space to make process <-> kernel communication more efficient. In practice on Linux and OS X, the entire physical memory is accessible in the kernel's memory, though through something called KASLR it's randomized on each reboot. Programs normally can't access kernel space without permission, but through some cache/side-channel tricks, they will be able to surmise what's in kernel space, and by extension what's in the rest of physical memory.
* The way the process is able to determine the contents of a page it can't access is via a [flush+reload](https://eprint.iacr.org/2013/448.pdf) attack, which is written about in a different paper. A screenshot from the paper helps explain how it works. Basically, if your program says "get rid of this memory location" and then tries to access the location again after some time, if it takes a short amount of time to pull the data up again, then it's likely been read (into a shared cache) by some other program:
![flush+reload](https://marcua.keybase.pub/meltdown-screenshots/flush-reload.png)
* To show how a read based on some data you're not allowed to access is possible with flush+reload, the authors provide a toy example, which I've annotated. Assuming `data` is a byte (256 possible values), and given that memory pages are 4 KB, I can create an array of size 1MB (256\*4096). After reading array element `data * 4096`, I can flush+reload pages to determine which page was read, corresponding to the value of `data:
![flush+reload](https://marcua.keybase.pub/meltdown-screenshots/toy-example.png)
* But how can you hit an exception and not crash your program? The authors offer three approaches:
  1) fork your program and let your child run the exceptional code (crashing) as well as the out-of-order read. Then run flush+reload to see what your child read.
  2) create a signal-based exception handler that tells the program to ignore the crash/segmentation fault.
  3) suppress the exception through transactional memory, or some tricks that the Spectre attack utilizes that I didn't understand.
* Section 5 explains the 5-line assembly inner loop. I've annoted the assembly to understand it better. Essentially, outside of this assembly, you're looping over every byte of the kernel. For each byte, you run the code in the annotated screenshot below, trying to access a mapped part of your probe array. After each byte, you run flush+reload to determine what the value at that kernel memory byte was. Sounds tiring, except it's done by a computer :):
![annotated assembly](https://marcua.keybase.pub/meltdown-screenshots/annotated-assembly.png)

# Questions I have coming out
* Does 503 KB/second mean the exploit is too slow in practice? At 503 KB/second, it would take (1024\*1024\*1024\/(503\*1024))\/3600 \=\~ 0.58 hours to read 1 GB of memory. That means it would take several days to copy memory from a modern server, which doesn't seem unreasonable. You'd probably hit some unencrypted passwords before then :).

# Questions for B12 to ponder
* Are we patched :)? I'm pretty sure we are by virtue of AWS upgrading all of the host kernels on our virtualized instances.

# Other references
* [An article explaining the Linux kernel update that hides parts of kernel space from side-channel attacks](https://lwn.net/Articles/738975/)
* [This Stackoverflow response and the summary on page 3 of the paper](https://stackoverflow.com/questions/49601910/out-of-order-execution-vs-speculative-execution) explain the difference between out-of-order execution (e.g., I read some memory that I see you'll be accessing later so it takes less time to retrieve it) and speculative execution (e.g., I suspect this branch will evaluate, so I started running the code in the branch before knowing if I'm right).
