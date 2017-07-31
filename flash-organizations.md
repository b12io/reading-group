# Reading
Fellow B12er [Daniela Retelny](http://danielaretelny.com/)'s final chapter of her thesis is on [Flash Organizations](http://hci.stanford.edu/publications/2017/flashorgs/flash-orgs-chi-2017.pdf). We read her and her collaborators' CHI paper on the topic.

# Questions I have going in
* How much structure comes from the initial scaffold laid down by the person forming the organization, and how much comes from forks/teams?
* How much fluidity in membership does this model see vs. traditional organizations and vs. Flash Teams?
* How does promotion work? Is there a notion of demotion? What does it look like when the task you are working on gets "refactored?"
* What does a branch/merge conflict look like in a running organization?
* How does leadership/expertise come into play? A Tech Lead leads a team of engineers, but does Foundry help in determining who the Tech Lead should be?
* How much did each of the Flash Organizations cost in terms of human labor? How would this compare to hiring a small agency to solve the problem?

# Notes
* Current crowd workflows can't handle complex and open-ended goals, like
creating a game or web application
* Take inspiration from modern organizations because they have to create large
groups to pursue complex open ended goals
* The paper describes two challenges to structuring crowds like organizations:
  * *Asset specificity*. To address this challenge, the paper structures
  workers in a de-individualized role hierarchy
      * Workers coordinate based on clear understanding of what each person's
      role is and what that role entails.
  * *Organizational structures need to be continuously reconfigured so that
  the organization can adapt as work progresses.* To address this challenge,
  the paper introduces a model for handling reconfigurations to the
  organizational structure.
* Computational organizational structures
  * Role structures
  * Specifies what skills are required
  * Arranges roles into hierarchy - encodes authority and decision rights
  * Roles can be assigned tasks.
* Reconfigurable organizational structures
  * Organizations must be able to adapt to changing circumstances, but in a
  coordinated way to avoid conflicting adaptations.
  * This paper borrows from software version control to handle changes to
  organizational structure: changes are submitted as pull requests similar to
  that used in git.
  * The version-controlled data are the roles, teams and task details, stored
  as hierarchical objects
* On-demand hiring
  * Create panels of workers pre-approved for certain skills.
  * When an opening appears, fill the opening with a worker from the appropriate
  panel.
* Evaluated system with three cases:
  * EMS Trauma Report - used the crowd to create a prototype mobile and web
  application for METs to report trauma injuries from an ambulance en route to
  the hospital.
  * True Stroy - used the crowd to design, manufacture and playtest a
  storytelling card game and an accompanying mobile app
  * Enterprise Workshop Planning Portal - used the crowd to create an
  enterprise web portal to administer client workshops
* There was a lot of PRs submitted for adaptations to the organizational
structure (566 over 6 weeks).
* Hired 75 workers on-demand across the three organizations. Median time of
13.7 minutes to fill a role.
* Organizations used rehiring functionality to rehire members for new tasks -
reduces amount of onboarding
* Challenge: skill fit of workers were unreliable - quality hiring was an issue


# 3 Takeaways
* Flash Organizations are role-based (e.g., movie crews) rather than asset-specific (i.e., requiring Jane on a particular team) to facilitate fast hiring based on skills/roles.
* Organizational change (hierarchical structure, roles, new tasks, task changes) can be proposed by anyone like a Pull Request on GitHub, and are reviewed by the leader of the team that the submitter is on. Reviewed changes/branches can be merged into the master organization, which results in new hiring, etc.
* In three applications (an EMS Android app, an actually manufactured/crowdfunded card game, an enterprise workshop web application), a leader used Flash Organizations to accomplish their goal satisfactorily in six weeks!

# Things that went unanswered
* How are these real world deployments more complex than building a mobile app (flash teams)?
* Did personality / working style of individuals affect the quality / speed of
work?
* How did workers react to the strict hierarchy?

# Questions for B12 to ponder
* What did we learn from our experience with experts in Orchestra that aligns
with the learnings from this paper? What doesn't align?
* What techniques from Foundry can we adapt and use in Orchestra?
* Do we have (will we have) tasks that require Flash Organizations? What might
they be?

# Other references
[Flash Organization slides](http://hci.stanford.edu/publications/2017/flashorgs/chi2017-flashorgs-final.pdf)
