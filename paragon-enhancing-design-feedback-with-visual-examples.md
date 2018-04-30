
# Reading
*Paragon: An Online Gallery for Enhancing Design Feedback with Visual Examples*

Hyeonsu B. Kang, Gabriel Amoako, Neil Sengupta, Steven P. Dow

# Questions I had before reading the paper
* How might examples help novices provide design feedback? What about experts?
* When given examples, how do novices incorporate examples into their feedbacks? How do they help/hurt? What are the trade-offs?
* How do feedback providers choose examples? What are their exploration strategies?
* What are the limitations of example uses for novices?

# Takeaways
* Examples make design feedback more specific, actionable and novel. 
* Usage pattern:
  * Use the examples to better explain certain points in the feedback.
  * For novices, examples reveal design concepts (which may correspond to some expert-created rubrics).
* Novice feedback providers tend to leverage examples with similar content to the target artifact due to lack of design knowledge. (Not a problem per se, but important to keep in mind when design a tool to support this process).
* Finding relevant examples takes time. Paragon allows feedback providers to filter examples based on some low-level and high-level features but we need more findings about the effectiveness of the tool.

# Notes
* Examples can help both feedback providers and receivers. This paper focuses mostly on the providers' side.
* The whole-process challenges:
  * How do we curate examples?
  * How do feedback providers find relevant examples?
  * How do feedback providers integrate examples to their feedback?
  * How do feedback recipients apply the feedback to improve their work?
* Novices generally comprehend surface-level features not deep features.
* Faceted metadata and query preview helps with visual gallery exploration.
* Study 1: How feedback provider uses examples
  * Within-subject study. 32 Mturk participants, 3 design students (in-person observations).
  * Task: Give feedback on a poster design following expert-generated rubrics.
  * 3 conditions
    * Control (Just feedback)
    * Content-similar examples (See examples of posters with content similar to the target design).
    * Content-curated examples (See examples of posters from the web).
  * Measures
    * Subjective responses: How did they choose examples? Would they like to use an example w/ feedback? Would they like to use similar examples? etc.
    * A professional designer rate feedback
  * Results:
    * Examples provide new ideas for critique.
    * Examples demonstrate the point given.
    * Novice participants had a hard time giving feedback when the content of the example is different from the target design.
    * No significant different in how rubrics were used
  
    
* Study 2: Examples' effect on feedback quality
  * Between-subject study
  * 124 online MTurk participants
  * 3 x 2 experiment
    * Example tool: Control (no example), Examples, and Examples+Metadata
    * Artifacts: 2 different topics for posters
  * Example tool (Paragon)
    * 287 design examples (29 had the same content)
    * Crowdsourced meta-data generation. (low level: amount of text, white-space, primary colors, content-alignment, high level: effectiveness of visual hierarchy, focus, structure)
  * Measures:
    * Four expert grade feedback (pairwise comparisons). Which on is more specific, actionable, and novel
  * Results:
    * Feedback with examples are of higher quality
    * Participant wrote longer feedback with examples
    * Writing feedback with examples takes more time (6.2min vs 13-15min)
    * Faceted filter helps when there are a lot of examples. (But no significant benefits).

# Questions coming out?
* How do attributes (quantity, diversity, quality, similarity to the subject under evaluation) of an example set affect the quality of generated feedback? 
* Are example-based feedback positive or negative?
* How do the results generalize beyond the visual design domain? How does it apply to writing, music composition, etc.?
* What are possible strategies in example curation and selection? How might we design a tool to support them? How might an intelligent system help people find relevant examples?
* How might feedback recipients make use of examples that integrated into the feedback?

# Questions / Applications for B12
* How might B12 customers integrate examples in their feedback on algo-generated websites? B12 has an unstructured way for the customers to do that (a list of websites that a customer likes and text description). However, these requires some work from the customers who might not know much about web design. Could we curate an example website gallery that the customers can explore?
* There will be difference between customer-to-designer feedback and designer-to-designer feedback.
* Can designers also use examples in explaining concepts to the customers?
