# Reading: The principles and limits of algorithm-in-the-loop decision making
* [Paper](https://www.benzevgreen.com/wp-content/uploads/2019/09/19-cscw.pdf)

# Takeaways
* Three desirable principles to consider when designing an algorithm-in-the-loop interaction
  * Accuracy - The algorithm should help people make more accurate prediction
  * Reliability - People should have a sense of how accurate their own and the algorithm predictions. This allows them to decide how to use the algorithm's output.
  * Fairness - The decision made together with the algorithm should be unbiased with regard to sensitive attributes (e.g., race and gender).
* People are not very good at judging the accuracy of prediction (either their own or the algorithm's).
* People do not adjust their strategy on taking the algorithm information based on their performances.
* People exhibited bias with the algorithms.
* We need to be careful in our assumptions on how algorithms affect people's decision making. There are some unexpected results (See note)


# Questions I have going in
* How would algorithms-in-the-loop help with decision making?
* What are the potential setbacks of algorithms-in-the-loop?
* How do we design a system to offset tht feedback.

# Questions/thoughts coming out?
* One big limitation of the paper is the choice of their participants. Here, the model knows more about the domains than the users. Would we get similar results if we run the same experiment with experts?
* What if the study also ask them to give a binary answer on top of risk prediction?
* The paper mentions the effecto of learning a little bit. However, each participant probably didn't spend longer than a few minutes on it. Would their predictions improve if they had done it for longer? 
* How might we improve algorithm-in-the-loop decision making? What does the design space look like?
* On a larger scale, how do decision making tools affect our critical thinking? How might we guide it into a more positive direction?
* Did what participants say about their strategy match with what they actually did?
* We can decide a system that helps with the gap identified in this paper. It would require some trials and erros. :)
* Can model help us detect hidden biases/assumptions in the field?

# Questions / Applications for B12
* If we implement a model that helps an expert makes design decisions, how might we make sure that it helps instead of hurts their performances? What if we provide the same tools to our customers (novices), would they need a different kind of setup?
* We are brining more ML into our process (lead scoring, churn prediction). how to design an interaction in such a way that our models support people to make the right decision?
* What are the trade-offs between efficiency and correctness. Our applications might have higher error tolerance than say deciding whether to send someone to jail.

# Notes
* Clever measures. This is a very neat study!
* Two domains: pre-trial risk assessment and loans risk assessment
* Five conditions:
  * Baseline: No exposure to the risk assessment prediction
  * RA Prediction: See the prediction
  * Default: The predicted risk is chosen by default but participants can change.
  * Update: Predict the risk before seeing the RA prediction then make the final prediction
  * Explanation: provided with extra explanation (why the risk of this case is X%)
  * Feedback: RA prediction condition. Get the real outcome of the case right after.
* I am surprised that people didn't "learn" in the Feedback condition. The proposed hypothesis in the paper makes senses.
