# Mining Precision Interfaces From Query Logs
[Paper link]()

# Main Takeaways
* The authors present a tool to automatically generate task-specific interactive interfaces from query logs.
* To do so, the authors represent queries as ASTs and find common interactions by detecting differences between the ASTs. The interactions are then mapped to interactive widgets, where widgets handle a domain of allowable values and a measure of how "good" the widget is for a given domain. A interface is made up of multiple widgets, and is selected by minimizing the sum of the widget cost functions.
* Precision Interfaces was evaluated on 4 query logs, where expressivity, performance and user preference were evaluated.

# Questions Going In
* How would you model queries and visualizations in order to automatically generate one from the other?
* How would you be able to make this performant?

# Raw Notes
* Query logs as the API for interactive interface generation.
* Develop a unified mathematical model for queries and interfaces.
* Decompose problem into: finding structural changes between queries and mapping those changes to interactions.
* Must bound the complexity of structural changes and provide simple mechanisms to specify the types of changes that are meaningful - arbitrarily complex interfaces are not useful
* Three logical steps: 1. Representation Canonicalizer, 2. Interaction Miner and Distiller, and 3. Interaction Mapper.
* They do not assume semantic understanding of the queries beyond near-universal features like primitive data types.
* Ranking interfaces - some scoring function so we select the “best” interfaces
* Interface Mapper
  * Goal: generate a set of interfaces that can express the queries in this graph
  * 3 challenges: 1. identifying candidate widgets for each edge, 2. extracting domain and template functions to substantiate those widgets, 3. mapping subsets of the interaction graph to widgets in an interface

# Questions Coming Out
* Can Precision Interfaces scale to arbitrarily complex queries? (joins, subqueries)
* Can Precision Interfaces handle queries where the variables are buried in a join condition or a nested subquery? e.g. cohort analysis.
* Don't fully understand the widget definition and the reduction of the interface mapping proeblem to a set cover problem.
* With clique optimization for interaction mining, what other times are structural changes are you detecting?

# Questions for B12 to ponder
* Can we apply this to our Metabase queries to automatically generate interfaces for common analyses?
* Does this have application in Orchestra? Can we use this to automatically turn our sql queries into dashboards for a client success manager to manage multiple projects?
