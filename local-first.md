# Reading
*Local-First Software: You Own Your Data, in spite of the Cloud*

Martin Kleppmann, Adam Wiggins, Peter van Hardenberg, Mark McGranaghan

[Paper](https://martin.kleppmann.com/papers/local-first.pdf)

# Questions I had before reading the paper
- Why do we need to make software local-first? In which case is it necessary? In which case is it not?
- Why is it hard? How close are we in making this a reality?

# Takeaways
- The way most softwares these days (e.g., Google Doc, Trello) support collaboration take away some advantages of old-world softwares away. For example, they are not as responsiveness because data have to travel to and from the server. User doesn't have control of their data and mostly have to depend to the platform.
- CRDTs (Conflict-free Replicated Data Types), a git-like model for any type of files, shows promises in implementing the local-first ideals.

# Notes
- 7 ideals of local-first software
  1. Fast
  2. Multi-device
  3. Offline
  4. Collaboration
  5. Longevity
  6. Privacy
  7. User control
- Instead of using the server as the source of truth, they propose a more peer-to-peer like system where any running app could be the source of truth.
- Am I the only one who has the word BlockChain pop up in my mind while reading this?
- I am surprised that conflicts is not a big issue.
- Challenges to HCI researchers. How might we design a system that help people resolve conflicts? How might we show the changes being made so that people can avoid conflicts"

# Questions coming out?
- Is this actually the best way
- How to deal with large history issues? What kind of assumptions should you make when design a local-first system?
- Not a question but there are a bunch of things to check out after this. :)
- How might this type of protocal becomes a mainstream? The current server-centric model seems to be doing a good job in locking users in their system.


# Questions / Applications for B12
- Related examples at B12, when we have multiple users editing the website at once, people rewrite each other's work. How might we make use of something like automerge to resolve this issues? Should we show who is working on what? Maybe, we can try lock some parts of the experience for some users?
- Can we apply the tool like automerge to speed up the loading time?
- How might we integrate the design of conflicts to the users?
