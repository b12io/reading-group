# Reading
* [Data Programming with DDLite: Putting Humans in a Different Part of the Loop](http://cs.stanford.edu/people/chrismre/papers/DDL_HILDA_2016.pdf)
* (The academic project [Snorkel](https://hazyresearch.github.io/snorkel/) used to be called DDLite.)


# 3 Takeaways
* Training machine learning models requires training data, which is typically expensively curated by experts or paid crowd workers. In this paper, the authors propose using those experts/crowd workers to create labeling rules that, in aggregate, can be used to provide weak labels for a large dataset that can be used for training.
* Once humans are creating labeling rules rather than labeling data manually, the challenge becomes to tell them which aspects of the data aren't covered nicely by the labeling rules. The authors do this by reporting metrics like the coverage and accuracy of each rule, as well as highlighting conflicts/inconsistencies between rules.
* In a one-day hackathon, domain-experts in biology (not machine learning) generated a DDLite/Snorkel-powered model with an F1 score of 0.72, whereas the best-of-class model that took months/years to generate data for and train has an F1 score of 0.82.

# Questions I have going in
* Since this paper is largely focused on a new way to generate training data, I'm curious what sort of "autoclassification" or "autofeaturization" makes it possible. Why don't you have to feature engineer and pick appropriate models for whatever you're feeding your training data into?


# Overall notes
* Typically for training a (e.g., binary) classifier, you need a balanced training set of positive and negative examples. This costs a lot of human capital and attention.
* Instead, the DDLite/Snorkel authors propose that huamn capital be spent on writing simple labeling functions. These functions, given a candidate input item, emit a negative (-1), positive (1), or non-participating (0) decision. By allowing non-participation, label writers can trade off precision (don't participate in every decision) for recall (trying to make a decision on every data point).
* The rules are 2-10-line Python functions. For example, if training an email spam classifier, one labeling function might return a 1 if words like `viagra` appear in the text, or a 0 (no decision) otherwise.
* The system asks the labeling function-writer to hand-label some data, and shows the writer statistics on each function they write. *Coverage* is the number of data points a function emits -1/1 on. Two forms of *accuracy* report how accurately the rule performs on the labeled data. *Conflict* indicates how frequently two rules that emit -1/1 disagree with one-another.
* This process is iterative. At any step, a labeling function author can fix issues in a rule, write more rules,


# Questions I have coming out
* More broadly, can't this be used to generate training data for any classifier, even if you're training it w/ traditional feature engineering, etc.? Is the problem that your features and your labels will be too correlated?
* If, rather than having domain experts in biology create labeling rules, you had a data engineer do the work, how accurate could their model get with one day of work?
* Why labels instead of features? Currently they lose data by enforcing binary/terenary labels.
* What if they also used labels as features for final model? Improve model accuracy?
* Stronger models than logistic regressions might get better feature interaction.
* Why not use GAL to aggregate labels? I guess because there's hand-labeled data whereas GAL has no ground truth?


# Questions for B12 to ponder
* 

# Other references
* [The project page/github repo](https://hazyresearch.github.io/snorkel/)
* [This tutorial helped me understand how it works in practice](https://github.com/HazyResearch/snorkel/tree/master/tutorials/intro)
