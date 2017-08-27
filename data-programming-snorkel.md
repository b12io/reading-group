# Reading
* [Data Programming with DDLite: Putting Humans in a Different Part of the Loop](http://cs.stanford.edu/people/chrismre/papers/DDL_HILDA_2016.pdf)
* (The academic project [Snorkel](https://hazyresearch.github.io/snorkel/) used to be called DDLite.)

# Questions I have going in
*

# 3 Takeaways
* Use humans for labeling functions, machines for trsining data
* Report coverage and accuracy of functions, and show example data that they conflict on
* Larger training data with imperfect labels in 1 day gets within 0.1 F1 of a model with months or years of training data


# Overall notes


# Things that went unanswered
* Why labels instead of features? Currently they lose data by enforcing binary/terenary labels.
* What if they also used labels as features for final model? Improve model accuracy?
* Stronger models than logistic regressions might get better feature interaction.
* Why not use GAL to aggregate labels? I guess because there's hand-labeled data whereas GAL has no ground truth?


# Questions for B12 to ponder
* 

# Other references
* [The project page/github repo](https://hazyresearch.github.io/snorkel/)
* [This tutorial helped me understand how it works in practice](https://github.com/HazyResearch/snorkel/tree/master/tutorials/intro)
