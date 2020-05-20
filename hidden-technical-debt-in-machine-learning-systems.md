# Reading

## Hidden Technical Debt in Machine Learning Systems
D. Sculley, Gary Holt, Daniel Golovin, Eugene Davydov, Todd Phillips, Dietmar Ebner, Vinay Chaudhary, Michael Young, Jean-Franc¸ois Crespo, Dan Dennison

Paper link: https://papers.nips.cc/paper/5656-hidden-technical-debt-in-machine-learning-systems.pdf

## Takeways:
- Machine Learning Systems are a combination of normal code and some machine learning specific code. The debts in these systems are therefore a combination of Software engineering debts and ML related debts.

- The actual machine learning code is only a small portion of the actual work. There are a lot of processes that happen before and after the actual machine learning program runs.

- With everything being packed in to a library these days and with the increase of ready to use code by Hugging Face, it is important to know about these debts. 

## Notes:

**Debts:**
- Boundary erosion: The nature of ML problems makes it difficult to abstract code.
- Entanglement: Changing Anything Changes Everything (CACE). Example: adding or removing a feature significantly affects the model output.
- Correlation Cascades: Adding corrections to existing model to create a new model.
- Hidden Feedback loops: Machine learning systems have a lot of feedback systems where it influences its own data.
- Data Dependencies: Data plays a key role in ML models. Changing inputs affects the model performance.
- Glue code: Running a deep learning model using 10 lines of code is cool but getting them to run is a task as everything is a black box. Difficult to debug.
- Pipeline Jungles: Running a ML model successfully involves a series of steps. It is not limited to running the model successfully.

**Solutions:**
- Versioning the models
- Testing


## Questions coming out:
- It is good to know these things in theory, how many of these practices can we implement?
- How do we decide when to reuse a model?


## Applications for B12:
- We are already using ML models for churn prediction and lead scoring. We can try to see if any of these debts are applicable to those models and what can we do about them.
- We plan to use transformer models in the future which are extremely huge models and are expensive to train. We can have a list of things to think about before when we deploy the model and how can we monitor its performance over time.
