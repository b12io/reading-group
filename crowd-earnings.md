# A Data-Driven Analysis of Workers’ Earnings on Amazon Mechanical Turk
[Paper link](https://www.cs.cmu.edu/~jbigham/pubs/pdfs/2018/crowd-earnings.pdf)

# Main Takeaways
* The authors looked at traces from 2676 workers across 3.8M HITs (tasks) over a period of slightly more than 2 years (Set 2014-Jan 2017). The traces were from a Chrome plugin that workers used to track their hourly pay rate, among other things.
* Average hourly pay was $3.13/hr, and the median was $1.77/hr. 4% of workers earn >= $7.25/hr (USA minimum wage).
* The authors quantify various forms of unpaid work, including looking for new tasks, starting but not completing tasks, and having their work rejected. If you remove this unpaid work, the mean goes to $6.19/hr, and the median goes to $3.18/hr.
* Interestingly, the average requester pays $11.58/hr (median is $4.57). A small number of requesters bring the average/median down with large quantities of low-paying tasks.

# Questions Going In
* What income expectations do Turkers have?
* How do Mechanical Turk wages differ by region and task type?
* How much "task search" overhead can we automate away to maximize Turker wages?

# Raw Notes
This is a descriptive statistics-heavy paper, so the notes are mostly other interesting statistics that I saw
* Interesting technique to estimate wage and time on task. Turkers pick up tasks in batches, presumably to reduce task search overhead and get desirable tasks before they are snatched up. As a result, you can't estimate time on task by measuring the wallclock difference between task end and task start. Instead, they search for task pickup/submission intervals that are no more than a minute apart. If two adjacent pickup/submission times are within a minute of one-another, you expand the interval, similar to [Agglomerative clustering](https://en.wikipedia.org/wiki/Hierarchical_clustering). You then assume workers spent the time from first pickup to final submission in an expanded interval is all work time.
* 61% of workers parallelize task pickup using the technique in the previous bullet point.
* Avg tasks/Turker: 1302. Standard deviation: 4723. Max 107K!
* Ranking of overhead/unpaid work, from things that take up most time to least time: 1) Turkers start but don't finish 13% of tasks, leaving them unpaid, 2) Task search time (hard for me to understand the estimate), 3) Requesters reject 0.7% of tasks.
* Several analyses of tasks that increase effective hourly pay:
  * Tasks that have a higher per-task pay rate result in higher hourly wages per Turker. One hypothesis I have for this: perhaps tasks that pay more are more likely to have been thought out/estimated by requesters as having a fair hourly wage, whereas the hourly effective pay rate of low-paying tasks isn't considered by requesters.
  * Not all tasks with qualifications have higher effective hourly rates, but certain classes of qualification ("total approved tasks" and "question editor") do.
  * Tasks on particular topics (e.g., video evaluation) have higher effective hourly rates.

# Questions Coming Out
* In Figure 1, it looks like the overall task volume goes down near the end of the study period. Is that because the Chrome plugin became less popular, or are Turkers leaving Mechanical Turk?
* Do Turkers who don't use this plugin have a lower hourly wage by virtue of being less connected? That would be sad but not surprising.

# Questions for B12 to ponder
* B12 pays experts an order of magnitude more than these rates. Still, what can we learn from this paper? Are there quick questions we ask experts or interactions we have that go unpaid?
* How can we reduce task search overhead for workers beyond [StaffBot](http://orchestra.readthedocs.io/en/stable/bots.html#staffbot)?
* StaffBot only offers a task description when it reaches out to experts. What sort of a peak into the deeper task can we offer experts?

# Notes for the authors
* Lots of researchers pay bonus post-hoc. How do bonus payments factor in? Example: during the period studied, DHaas created a quarter million tasks where lion's share of the pay was in bonuses for variable work.
* Mean/median are reported twice in intro (with and without unpaid work), but are reported in flipped order
* It feels like there are qualitative buckets of turkers: 1) try it once, 2) hobbyists, 3) use it a lot, 4) sole profession. The statistics pooled across all of these groups are less interesting than the statistics per-group. A fun to investigate section would include a table with key metrics broken down into these groups. Paper #2 :).
