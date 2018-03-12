# Reading
Self-Disclosure and Perceived Trustworthiness of Airbnb Host Profiles by Xiao Ma, et al.

# Questions I had before reading the paper
* How do you measure perceived trustworthiness?

# Takeaways

# Notes
* _trustworthiness vs trust_: trustworthiness is an attribute of the trustee while trust is exhibited by a trustor.
* The authors build on the Profile as Promise framework conceptual framework, which describes the risks and rewards associated with assessing signals in a profile for whether said profile's promises can be trusted, by drawing on theories from economics and commmunication:
  * *uncertainty reduction theory (URT):* strangers are concerned with increasing the predictability of the behaviors of both themselves and others in the first encounter.
  * *signaling theory*: studies the relationship between explicitly stated signals and the underlying qualities they are likely to represent. Assessment signals are difficult to fake (degree, employer), while conventional signals are relatively easy to fake (reliable, hard-working).
* These theories are used to create hypotheses around self-disclosure and preceived trustworthiness which.
* There are 3 research questions addressed in this paper:
  1. What kinds of information do hosts self-disclose to signal their trustworthniess?
  2. What is the effect of different types of self-disclosure on perceived trustworthiness?
  3. Do profile-based perceptions of trustworthiness predict choice of host on Airbnb?
* Study 1 - How do hosts self-disclose?
  * The goal of Study 1 is to categorize and describe trends in the types of information hosts disclose in their profiles. The study consists of 2 parts: 1. developing the coding scheme, and 2. applying the coding scheme to a large set of profiles and analyzing trends in self-disclosure.
  * Phase 1 - developing and validating coding scheme. Each sentence in an Airbnb profile is tagged with one or more topics (e.g. Interest, Travel, Personality). The topics were manually curated by the authors on 300 sentences from 203 host profiles. The coding scheme was then validated with AMT workers using 2 metrics: level of agreement among crowd workers and level of agreement between crowd workers consensus and the authors.
  * Phase 2 - applying the coding scheme to profiles.
    * The authors had 2 hypotheses. They also emphasize that there are two types of hosting situations: onsite (where hosts share their space with guests during the stay) and remote (hosts are not present during the stay).
      1. Hosts will disclose more about categories that have more assessment value (work, education, origin), than about categories that have more conventional value (Interests, Personality).
      2. On-site hosts will disclose more, especially for topics that can reduce uncertaint during the interaction of sharing spaces (Interests, Personality) than remote hosts.
    * The authors used a large dataset collected by Inside Airbnb, which periodically scrapes the Airbnb website, tracking 35 cities in 13 countries.
    * Analysis was limited to English-language host profiles in the 12 largest US cities (excluding 3 that have fewer than 1000 hosts). After filtering out empty and non-English containing profiles, there were 40,005 profiles.
    * They created a dataset of 5248 sentences from 1234 profiles.
    * Trends:
      * Popularity of topics: _Origin or Residence_, _Work or Education_, _Interests & Tastes_, _Travel_, _Hospitality_. _Relationships_, _Peronsality_ and _Life Motto & Values_ were mentioned much less.
      * On-site hosts wrote longer profiles than remote hosts on average.
      * On-site hosts were more likely than remote hosts to write about topics that signal their personality and tastes. To rule out the possiblity that the differences are due to a host's level of experience, the authors looked at superhosts (Airbnb qualification type for hosts that are frequent hosters, have a high response rate and high review scores) vs. average hosts. There was no siginificant difference between the two in likelihood of mentioning _Interests & Tastes_ or _Personality_
* Study 2 - Self-disclosure and perceived trustworthiness.
  * Study 2 addresses the question of whether the information hosts are disclosing enhances perceived trustworthiness.
  * Trustworthiness can be evaluated by 3 key dimensions: ability, benevolence and integrity.
  * The authors use the Profile as Promise concept of the online profile as a psychological contract and URT to make the following hypotheses:
    1. Longer and more diverse self-disclosures are perceived as more trustworthy.
    2. Self-disclosure topics used most frequently by hosts will be associated with increased perceived trustworthiness compared to less frequent topics.
  * Study procedure: AMT workers rate host profiles in the dataset described above on a six-item perceived trustworthiness scale. Each item is rated from 0-100, in steps of 10. The dataset is split into batches of 20, and 5 workers annotate each batch. At the beginning of each task, they used a paraphrase question to check the linguistic attentiveness of each worker. The final score is an average across workers and across the six items.
  * There is a clear relationship between increased profile length and perceived trustworthiness score. The relationship is linear with log transformation on profile length.
  * The number of topics was found to contribute to perceived trustworthiness.
  * Topic and perceived trustworthiness: the authors looked at one-topic (117), two-topic (231) and three-topic (239) profiles and whether the perceived trustworthiness scores were affected specific topic combinations, referred to as "stragegy".
    * _Hospitality_ was by far the most successful single-topic strategy.
    * OW and HO were the most popular two-topic strategies.
    * The most popular topic combinations also had the highest perceived trustworthiness, supporting the second hypothesis.
* Study 3 - From perception to choice
  * This study looks at how perception of trustworthiness leads to differences in host choice.
  * Hypothesis: higher perceived trustworthiness scores for text-based host profiles predict the likelihood of guest choice.
  * Study procedure: create pairs of low score / high score host profiles with roughly the same length. The pair is shown to a respondent and she is asked which host she feels more comfortable staying with. Each respondent was asked to evaluate 50 pairs. 3 pairs were repeated to evaluate the consistency of the worker's answers. After cleaning / filtering, there are responses from 355 workers (16,685 pairs).
  * Used Bradley-Terry model to evaluate if preceived trustworthiness accurately predicts choice.
  

# Things that went unanswered

# Questions / Applications for B12