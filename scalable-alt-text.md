# Reading: Toward Scalable Social Alt Text: Conversational Crowdsourcing as a Tool for Refining Vision-to-Language Technology for the Blind
[Paper link](https://aaai.org/ocs/index.php/HCOMP/HCOMP17/paper/viewFile/15920/15272)
## Main Takeaways
* Captioning is an important tool for Blind and Visually Impaired (BVI) users to interact with images on the web, particularly on social networks where posts are illustrated with accompanying imagery.
* AI-generated captions are perceived by BVI users as trustworthy, but still fall short of human-quality captions. Seeding human captioning workflows with AI-generated captions can actually make them worse!
* A workflow for generating captions based on humans answering a series of structured questions about the image outperforms workflows using automated captions, automated captions corrected by humans, and captions generated via conversations between BVI and sighted users.
* Different workflows have different tradeoffs with respect to caption accuracy and the time and cost required to generate captions.
## Questions going in
* Is captioning a good problem for an AI + human solution? Or is AI-only good enough?
* How will they evaluate the quality of a caption? Perceived quality?
* Is real-time crowsourcing fast enough or scalable enough to handle the needs of BVI users?
## Raw Notes
* previous work has:
    * done auto-AI captioning (e.g., Microsoft CaptionBot, Google Show & Tell)
    * done human captioning/question answering via real-time interaction (e.g., VizWiz, Choros)
    * done AI+human workflows for image interpretation (but only constrained, objective tasks like object detection)


* Scope of this work: workflows for captioning images in social media (read: Twitter) posts
* BVI users trust auto-generated captions even when they're inaccurate, so it pays to get this right!
* Workflows for alt text generation
    * A workflow is steps to go from “tweet” to “explanation of the image in the context of the tweet”
    * Vision-to-language: auto-generate a caption from the image (e.g., CaptionBot). Limitation: doesn't use the tweet text, so there's no context
    * Human-corrected-captions: crowd workers clean up the auto-generated caption. Limitation: workers might not know what kinds of information in the caption is mostly helpful for BVI users
    * TweetTalk Conversational Assistant, Structured Q&A: new workflows developed in this paper.
* Simulated BVI users by giving tasks to presumably-sighted workers and hiding images from them. What are the issues with this approach? (haven't had experience being BVI, might think about images differently?). Validated the approach by evaluating on 7 true BVI users as well
* Data set: 85 tweets curated in previous work, from a limited set of popular accounts / trending hashtags, with diverse topics, and varying in the confidence of auto-captioning techniques
* Conversational Assistant Workflow:
    * built on TweetTalk, a platform for freeform conversations between BVI and non-BVI people. 
    * (simulated-)BVI person sees tweet text, but not the image. non-BVI person sees both. They have a freeform conversation where the non-BVI person tries to explain what's going on in the image, and together they write a caption
    * Steps:
        1. both people read the tweet / non-BVI person looks at the image. In some conditions, they are also shown a baseline caption from the vision-to-language or human-corrected workflows.
        2. the simulated-BVI person rates the quality of the baseline caption if it exists
        3. The simulated-BVI person asks questions of the non-BVI person until they understand what's going on in the image
        4. The simulated-BVI person writes a caption for the image..
        5. The simulated-BVI person sees the image, and rates the baseline caption and the caption they wrote for effectiveness
    * feedback is on a 1-5 Likert scale where 5 is “I think visually impaired people would find this caption helpful.”
    * after running this on MTurk, they coded 429 of the questions asked by simulated-BVI into 16 categories, e.g. action queries that asked what was happening in the image (see Table 1).
* Structured Questions Workflow
    * Using the categorization of questions described above, the authors designed structured questions to get at the core informational need of the BVI users (see Table 2). One q: where did some of these come from? In particular “Is this tweet intended to be humorous? Explain how.” and “Does this tweet contain a meme (meme images, #hashtags, etc.)? If so, describe what the meme is about.” didn't seem to come naturally from Table 1.
    * For each tweet, the system sends out each question individually as an MTurk HIT (3 votes per HIT). Workers can choose not to respond if the question is irrelevant to the tweet. The system takes the longest response (??) if the majority of workers thought the question was relevant.
    * Then, the system sends out 1 HIT to a simulated-BVI user, shows them the answers to the questions, and asks them to write a caption. (this task is way cheaper than the TweetTalk tasks because there's no need to have a slow back-and-forth conversation)
    * As w/ TweetTalk workflow, the simulated-BVI worker is shown a baseline caption, and rates that caption as well as their own generated caption after seeing the image.
* Experiments
    *  85 tweets x 3 conditions (no baseline caption, auto-caption, human-corrected-caption) x 1 conversation  = 255 conversations for conversational workflow, similar for structured questions workflow
    * Got a 3rd-party eval for every baseline and generated caption in each condition (using the same flow as for 1st-party participants)
    * Results (see Table 3):
        * auto-captions are significantly less useful than both human-corrected and the new workflows. “This suggests that automatic image captioning systems require more work before they are ready for use by social networking platforms.” (dhaas commentary: does it?)
        * no significant difference between human-corrected and tweetalk if TT was seeded w/ no caption or a human-corrected caption
        * Seeding conversational interfaces w/ auto-generated captions can make the human-powered caption worse! (technically: less 'satisfying', i.e. the caption was believable before seeing the image, but disappointing after seeing it).
        * Structured Questions workflow significantly outperforms other approaches
        * Cost: structured questions is slightly more expensive than conversations ($1.20 + $0.15 vs $0.95), but could be amortized across multiple users (so in effect it's a lot cheaper). 
    * Validation study with actual BVI users
        * 7 BVI users were shown baseline auto-captions for a random tweet, then had a conversation w/ a member of the research team to generate a caption (“the experiment could not be conducted through AMT due to screen reader accessibility issues” :-( :-( :-( )
        * 3rd party raters evaluated the captions, and there was no significant difference between these evaluations and those from the matching condition in the MTurk experiments.
        * The questions asked by BVI users fell under the categories in Table 1 w/ about the same frequency as the simulated-BVI users' questions
        * qualitative results: BVI users enjoyed the experience, but one thought that it was excessive for simple images, and one reflected that some images are harder than other to explain. All 7 said they would use a similar interface to get more information about images they encountered on social networks
## Questions coming out
* Why does the structured questions approach do so well? Why is it better than the conversational approach? (seems like this wasn't true for 1st-party ratings, do conversations generate captions that are only useful for the BVI user in the conversation?)
* Third-party evaluations were done by sighted users. Would BVI users have a different standard for the usefulness of a caption?
* Do captioning systems like these bias users' understanding of posts? What would happen when using humans to caption politically-charged or hot-button issues?
* Does the fact that human-in-the-loop workflows for captioning improves the quality of the captions mean we should stop using auto-captions until they're better?
* How do interventions like this affect the experience of browsing through a twitter feed (not just captioning a single image). Is it practical to have to wait a minute to get a caption?
* I wonder if automated approaches could also use the 'structured questions' workflow to improve performance?
## Questions for B12
* Could we use something like this to generate alt-text for customer images on their websites?
* In general, how can we be more sensitive to accessibility issues on our and our customers websites?
* Given how well coding structured responses from an unstructured conversational process works, how well would it work for internal processes we have, like design review or customer website feedback?
## Other references
* [VizWiz](http://up.csail.mit.edu/other-pubs/vizwiz.pdf)
* [CaptionBot](https://www.captionbot.ai/)
* [Turk Server (that TweetTalk was built on top of)](https://www.aaai.org/ocs/index.php/WS/AAAIW12/paper/download/5315/5598)
