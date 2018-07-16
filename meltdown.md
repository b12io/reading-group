# Reading: Meltdown
* [Paper](https://meltdownattack.com/meltdown.pdf)
* [Adrian Colyer's helpful summary](https://blog.acolyer.org/2018/01/15/meltdown/)


# 3 Takeaways
* Through a side-channel attack, Meltdown takes advantage of a performance feature of modern CPUs called out-of-order execution to get access to memory reserved for the kernel, as well as memory used by other proesses. Memory used by the kernel and other process should not be accessible to the application.
* Because the exploit depends on a feature of modern CPUs that turns out to be a vulnerability due to side-channels, it affects all operating systems running on those CPUs. The paper shows that on an operating system like Linux or OS X, the entire physical memory can be read. This includes reading the memory of sandboxed processes that should be protected by things like containers/virtualization.
* Luckily, and unlike the related Spectre attack, Meltdown can largely be avoided through a countermeasure called KAISER that was developed a year earlier for the Linux kernel. At this point, the major operating systems all have similar patches available to protect against Meltdown, albeit by incurring a performance penalty.

# Questions I have going in
* What is the difference between out-of-order execution (apparently what Meltdown exploits) and speculative execution (apparently what Spectre exploits).

# Overall notes
![This picture explains a lot](https://adriancolyer.files.wordpress.com/2018/01/meltdown-listing-2.jpeg?w=200&zoom=2)

# Questions I have coming out


# Questions for B12 to ponder
* Are we patched? :)

# Other references
* [An article explaining the Linux kernel update that hides parts of kernel space from side-channel attacks](https://lwn.net/Articles/738975/)
* [This Stackoverflow response and the summary on page 3 of the paper](https://stackoverflow.com/questions/49601910/out-of-order-execution-vs-speculative-execution) explain the difference between out-of-order execution (e.g., I read some memory that I see you'll be accessing later so it takes less time to retrieve it) and speculative execution (e.g., I suspect this branch will evaluate, so I started running the code in the branch before knowing if I'm right).
