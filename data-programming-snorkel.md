# Reading
* [Data Programming with DDLite: Putting Humans in a Different Part of the Loop](http://cs.stanford.edu/people/chrismre/papers/DDL_HILDA_2016.pdf)
* (The [Snorkel](https://hazyresearch.github.io/snorkel/) project used to be called DDLite.)


# 3 Takeaways
* Training machine learning models requires training data, which is typically expensively curated by experts or paid crowd workers. In this paper, the authors propose using those experts/crowd workers to create labeling rules that, in aggregate, can be used to provide weak labels for a large dataset that can be used for training.
* Once humans are creating labeling rules rather than labeling data manually, the challenge becomes to tell them which aspects of the data aren't covered nicely by the labeling rules. The authors do this by reporting metrics like the coverage and accuracy of each rule, as well as highlighting conflicts/inconsistencies between rules.
* In a one-day hackathon, domain-experts in biology (not machine learning) generated a DDLite/Snorkel-powered model with an F1 score of 0.72, whereas the best-of-class model that took months/years to generate data for and train has an F1 score of 0.82.

# Questions I have going in
* Since this paper is largely focused on a new way to generate training data, I'm curious what sort of "autoclassification" or "autofeaturization" makes it possible. Why don't you have to feature engineer and pick appropriate models for whatever you're feeding your training data into?


# Overall notes
* This paper uses knowledge base construction as its motivating example. This is the act of taking a bunch of documents and turning them into facts about entities you extract from those documents. As a result, they spend a decent amount of time on candidate generation: how do you identify candidate entities or facts that you want to make decision on? That said, the lessons and ideas in this paper can be applied to any supervised learning problem: given a bunch of inputs, how do you create rules to label the data rather than labeling it manually?
* Typically for training a (e.g., binary) classifier, you need a balanced training set of positive and negative examples. This costs a lot of human capital and attention.
* Instead, the DDLite/Snorkel authors propose that human capital be spent on writing simple labeling functions. These functions, given a candidate input item, emit a negative (-1), positive (1), or non-participating (0) decision. By allowing non-participation, label writers can trade off precision (don't participate in every decision) for recall (trying to make a decision on every data point).
* The rules are 2-10-line Python functions. For example, if training an email spam classifier, one labeling function might return a 1 if words like `viagra` appear in the text, or a 0 (no decision) otherwise.
* The system asks the labeling function-writer to hand-label some data, and shows the writer statistics on each function they write. *Coverage* is the number of data points a function emits -1/1 on. Two forms of *accuracy* report how accurately the rule performs on the labeled data. *Conflict* indicates how frequently two rules that emit -1/1 disagree with one-another.
* This process is iterative. At any step, a labeling function writers looks at the coverage/accuracy/conflict of their rules and decides to fix coverage/accuracy issues in a rule or write more rules.
* An interesting area of future work is which examples to show labeling function writers to motivate them to improve their rules. Do you show unlabeled data? Conficting data? Hypothetical new rules that you automatically detected?


# Questions I have coming out
* Can't this aproach be used to generate training data for any classifier, even if you're training it w/ traditional feature engineering, model-building, etc.? It seems like the important contribution is a new approach to generate training data, which is very broad! There's a bit of magic at the beginning (candidate generation) and end (magic model building) that seems like it limits the generalizability of the broader training data takeaways.
* If, rather than having domain experts in biology create labeling rules, you had a data engineer do the work, how accurate could their model get with one day of work? I'm curious because I feel that this approach is useful even in traditional model-building scenarios.
* Is it that much easier to construct labels than it is to engineer features? Lots of features I've written/reviewed are also 2-10-line Python functions. Turning feature data (e.g., the number of times a word appears) into a label (e.g., does the word appear at all?) certainly causes signal loss, but it doesn't seem that much easier to for the feature engineer to do one task vs. another. To argue against myself, the benefit of labeling functions over features is that you can report things like accuracy/conflict more intuitively than you can feature importance/correlation.
* Can you use the labeling functions as features in the final model? Dpes that improve model accuracy?
* I didn't fully get this, but I think the authors say they labeled the training data by building a logistic regression of the labels against the hand-labeled data. I'd imagine that there's quite a bit of feature correlation/interaction/nonlinearity. Would adding interaction terms to the logistic regression, or using a model like a random forest that allows inputs to interact with one-another result in better labels?


# Questions for B12 to ponder
* We've spent quite a bit of time trying to generate training data on Mechanical Turk. Could we leave the rest of our training pipelines in place, but generate training data using this label function-based approach?

# Other references
* [The project page/github repo](https://hazyresearch.github.io/snorkel/)
* [This tutorial helped me understand how it works in practice](https://github.com/HazyResearch/snorkel/tree/master/tutorials/intro)
