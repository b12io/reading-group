# Reading: Using Rubrics for Crowdsourced Design Critique
* [Almost an Expert: The Effects of Rubrics and Expertise on Perceived Value of Crowdsourced Design Critiques](http://www.cs.cmu.edu/~spdow/files/CrowdCrit-rubrics-cscw2016.pdf)

# 3 Takeaways
* You can provide very rudimentary rubrics (e.g., "Is the visual hierarchy off?") to novice crowd workers and have them provide feedback that designers rate equally well as experts.
* Both novice and expert feedback improves with rubrics (from the perspective of the person getting feedback), but novice feedback ratings improve way more than expert ones.
* Experts still provide better justification for why they are giving certain feedback. Better justification appears to result in more helpful feedback. Writing styles also affect the perceived helpfulness, which rubrics help with.

# Questions I have going in
* How can we improve the quality of feedback given by novices?
* What are the attributes of helpful feedback? How can we ensure feedback of a certain quality?

# Overall notes
* Helpful feedback is positive, specific, and justifiable.
* Measures of feedback quality
  - Rating by feedback receivers
  - Rating of revised artifacts
  - Contrasting with feedback from experts
* 2x2 between subjects experiment
  - Independent variables: expertise (expert, novice) and rubrics (rubric, no rubric)
  - Dependent variables: feedback ratings of the students who received feedbacks
  - Covariants: student raters' design experience and vocabularly richness
* Active sentences ("Why don't you increase the constrast?") are rated as more helpful than non-active statement ("The constrast is low.")
* Experts provide feedback with clearer justifications.
* Repeated multiple feedback helps with prioritization.

# Questions I have coming out
* How do we ensure that the generated feedback is good?
* How do we build good design rubrics?
* Could _bad_ rubrics harm the feedback?
* If gathering feedback from multiple sources is helpful, how can we scalably do that?
* How does perceived helpfulness correlate with improvement in design?
* How much does the perceived helpfulness depend on personal traits of the recipient?
* How can automation help in providing feedback?

# Areas for future work
* When we do design review internally, it's often hard to provide the reviewer with enough context about what the customer wanted. So sometimes reviews come back with "the colors contrast poorly" when the customer requested that palette. How do we provide context/constraints to reviewers?
* This evaluation talks about perceived quality of review from the perspective of the recipient. Another dimension is the diversity of review, which the paper touches on a ittle bit. Every day we have a different design reviewer provide our designers with feedback. Our reviewers look for different things, and have pretty different feedback. Does standardizing a rubric increase the diversity of the feedback? Two references:
  * [Nielsen Normal Group report](https://www.nngroup.com/articles/how-to-conduct-a-heuristic-evaluation/) says one heuristic review covers something like 30% of feedback (Figure 2).
  * [Get Another Label](http://crowdsourcing-class.org/readings/downloads/econ/get-another-label.pdf) asks when we should stop asking the crowd for more feedback, albeit in a very different context.

# Questions for B12 to ponder
* We should provide rubrics to our design reviewers.
* We should provide rubrics to our customers.
* We should support customers in providing helpful rationale for their feedback.
* Experts should be able to communicate justification of their solutions to the customers.
* Our designer-powered recommendations are a form of design critique as well. What can we learn from that?
* CrowdCrit provides feedback with visual annotations---until we have that, how will our results be different?
* Can we open our dataset to one of these researchers?
* How does our internal AutoQAing tooling combine with design feedback? Can you combine machine feedback with designer feedback?

# Other references
* [The original CrowdCrit Paper](http://www.cs.cmu.edu/~spdow/files/CrowdCrit-cscw2015.pdf)
* [CritViz, another reference](http://www.ieeetclt.org/issues/january2013/Tinapple.pdf)
* [Voyant: Generating Structured Feedback on Visual
Designs Using a Crowd of Non-Experts](https://pdfs.semanticscholar.org/87d9/5dc96c90e1e371ffc484ac6bfa83a3be75b5.pdf)
* [Nielsen Normal on Heuristic Evaluations](https://www.nngroup.com/articles/how-to-conduct-a-heuristic-evaluation/)
* [Get Another Label](http://crowdsourcing-class.org/readings/downloads/econ/get-another-label.pdf) 
* [Parallel Prototyping](http://spdow.ucsd.edu/files/PrototypingParallel-TOCHI10.pdf)
