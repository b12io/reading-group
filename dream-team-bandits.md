# Reading
*In Search of the Dream Team: Temporally Constrained Multi-Armed Bandits for Identifying Effective Team Structures*
Sharon Zhou, Melissa Valentine, Michael S. Bernstein

# Questions I had before reading the paper
* How do you change a team's organizational structure in the middle of their work?
* Which is more important for performance, the particular individuals on the team or the organizational structure of the team?
* What dimensions of team structure matter, and how can they be explicitly controlled with software?
* Why a network of few-armed bandits instead of one many-armed bandit?

# Takeaways
* There are a number of important dimensions of team structures, and the optimal choices vary by team and by task.
* Using a network of bandits to adaptively explore the space of team structures can lead to better outcomes than letting teams set their structure organically or having a manager decide on the structure.
* However, naively applying the theory of bandits to team structures would lead to jarring and rapid team changes. Adding temporal constraints makes the changes feel more natural and improves outcomes.

# Notes
* The high-level pitch: different teams are successful with different organizational structures. Use a bandit algorithm to adapt aspects of a team's structure over time (hierarchy structure, feedback norms, etc.). This will optimize the team's performance without sudden, jarring changes to the team.

* The DreamTeam system: takes a set of dimensions (e.g. hierarchy), and reacts based on an objective function that combines observed and self-reported performance metrics. A slackbot instructs workers around their team hierarchies and records their scores.

* Dimensions were picked from pre-existing literature on what matters for team structure (see Table 1).

* Network of bandits:
  * Each dimension is represented by one bandit with 3-5 'arms', one for each value of the dimension (e.g., the 'hierarchy' bandit has an arm for 'centralized', one for 'decentralized', and one for 'none').
  * a Thompson sampling-based algorithm is used to select the arm that will be played in the next round (e.g., what style of hierarchy the team will use for the next phase of work).
  * Thompson sampling uses past rewards to update a probability distribution for the payout of each arm, then picks the arm to play in the next round based on those distributions
  * If the bandit for every dimension changed arms every round, it would completely transform the team, which would be jarring. Instead, the authors introduce two kinds of constraints on arm selection:
    * Global temporal constraints: controls the expected number of changes to a team over time
    * Dimensional temporal constraints: forces a dimension to change only at the beginning or only at the end of the work.
  * How to enforce these constraints on the Thompson sampling algorithm? Renormalize the posterior distributions to favor the most-recently used arm in order to discourage change. Delta = 0: no change. Delta = 1: only the recent arm can be selected.
  * Note: the formulation here is incorrect (example from figure 3 reverses the 0 and 1 from the description in the text).

* How to pick delta for each dimension? look at existing literature and choose 'early', 'late', or 'ongoing'. Sigmoid functions to capture 'early' or 'late' (this requires knowing the duration of the project).

* How to pick global delta? inverted parabola emphasizes that more changes should occcur overall in the middle than beginning or end. Then, look at the expected number of changes the network of bandits wants to make (z), the current progress in the parabola (y), and if z > y, renormalize probabilities so that z = y (Figure 4).

* Eval:
  * Recruited teams of MTurk workers (135 workers total) and asked them to play a codenames-style game via slack. Paid $12-23 for the 1-2 hour task, with a $1 bonus if they performed above average.
  * Two training rounds: 1 for workers to learn the game, 1 to establish priors for the bandits system
  * Experimental conditions: control (no team structures were imposed, no slackbot appeared), collective (teams picked their structures at the beginning of each round), manager (one individual picked the structure at the beginning of each round) bandit (Dream Team w/out temporal constraints), dreamTeam.
  * DreamTeam outperformed other conditions on average score by >= 38%. No other significant differences between conditions.
  * Final team structures were very different across DreamTeam teams. No one like critical feedback
  * In the unconstrained bandit condition, people stopped listening to the slackbot (dhaas: how did they test this?)
  * Lots of other interesting qualitative comments on the various conditions--worth a read!

# Questions coming out?
* Unanswered: how did the particular individuals on the team influence performance?
* How realistic was the 'slackbot tells you how to behave' interface for deciding team structure? What other mechanisms could the authors have used to (e.g.) enforce positive feedback or hierarchical structure?
* How much did the global delta matter vs. the individual deltas?
* Lots of interesting qualitative insights around when teams "ignored suggestions" from the slackbot. How was this evaluated?
* Beyond the chosen dimensions, what other aspects of team structure could be important for success? Are they all equally amenable to exploring in this way?

# Questions / Applications for B12
* We've been thinking of a global model of how a team should be structured to deliver a website. What dimensions of team structure are flexible in our model, and could we use a bandit-like adaptive exploration of them to improve the performance of particular teams of CSMs and designers?
* Our project teams currently have some dimensions of team structure enforced by the software (e.g., CSMs sit hierarchically above designers based on the workflow), but some dimensions unenforced (e.g., feedback style or other interactions on slack). In what ways could we make dimensions of team structure more explicit throughout our workflows? 
* The slackbot in this paper provided a very hands-off enforcement of team structure (just one slack message instructing folks how to behave). What level of enforcement is right for us? We've talked about guidelines / rubrics for design feedback, what about for things like norms of engagement, hierarchy, or decision-making?
