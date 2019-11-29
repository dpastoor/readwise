# Highlights 

## Agile Project Management with Kanban (Developer Best Practices) 

A large part of project management is limiting the chaos inherent in group work. This step is so important that you can often identify the essence of a project-management methodology by how it limits chaos. In a traditional Waterfall approach, chaos is limited by specifying all the work up front, enforcing a formal change-request procedure, and synchronizing work across teams at predetermined milestones. In Scrum, chaos is limited by planning time-boxed sprints, withholding plan changes until the next sprint, and synchronizing with the customer at the end of each sprint. In Kanban, chaos is limited by directly limiting the amount of work in progress (WIP)—literally, the number of note cards allowed at each step. Simple, yet effective.

 The Bugs/Other backlog is the stack-ranked list of bugs to address. The source of a bug is a previous escalation or a bug that was added directly to this backlog after triage. Note the “Other” classification. An example of a work item in the Other category is a small product improvement (such as improved logging in the software) that would make sustained engineering more effective. A second example is an operational improvement, such as a diagnostics tool, that makes the team more efficient.

 The Validate column indicates that a member of the team—likely a QA engineer—needs to validate the acceptance criteria for the bug by running a set of acceptance tests on an automated build. (You do have an automated build, right?) The Validate done rule is, “All acceptance criteria met and any issues found are resolved.”

 Items often get blocked midstream awaiting external review, dependencies, questions, approvals, or other input from outside the team. For my Xbox teams, this happens most often at the Implement step. To handle the issue, we add a Track column to the middle of the Implement step. Items are moved to the Track column whenever they are blocked awaiting external input. Tracked items don’t count toward the Implement WIP limit. We talk about their status during every daily standup until they are unblocked. When a tracked item is unblocked, it moves back to the Active column as soon as a slot becomes available. The logic is that any item already in Implement has higher priority than the next item from Specify.

 Improvements might be identified with a simple root-cause analysis process such as the “5 Whys” (http://en.wikipedia.org/wiki/5_Whys) or, my personal favorite, the Six Boxes (http://www.sixboxes.com). The Six Boxes provide a root-cause analysis and solution framework that helps you look above and beyond the obvious symptoms by focusing on expectations and feedback, tools and processes, incentives, motivation, selection and assignment (or capacity), and skills and knowledge. The root-cause analysis done rule is, “Analysis complete and recommended actions are inserted back into the SE team’s backlog or fed back to the core engineering team for inclusion in their backlog.”

 Estimate the number of tasks needed to complete work items I recommend using a Wideband Delphi method, which utilizes iteration and consensus to provide accurate estimates. My favorite method is a simplified form of Wideband Delphi called “planning poker.” To estimate task breakdown using planning poker, team members sit around a table (or an online messaging room), and each team member privately estimates the number of tasks needed to complete the work item in question. They can write their estimates on a slip of paper or use preprinted cards. (Planning poker cards typically follow a geometric or Fibonacci sequence.) Everyone reveals his or her estimate simultaneously so that no one exerts undue influence. If the estimates match, you’re done (write the estimate on the work item note card). If they differ, the high and low estimators explain themselves, the team members discuss their thinking, and then the process repeats until the estimates agree. The process also identifies assumptions before they become problems.

 The Develop done rule is, “All relevant unit tests pass, including new unit test(s) that validate the fix; fixes are ‘buddy tested’ on a separate machine (typically by QA); and integration tests are enhanced as appropriate to exercise the exposed area.”

 Small batches require a coordinated flow of work. If analysts specify more features in a week than developers can implement, specifications start piling up, and you’re back to doing work in bulk. Likewise for developers implementing more features than testers can validate. If you can’t pace specification, implementation, and validation to run at similar rates, you’re stuck working in bulk and dealing with wasted effort, large bug backlogs, and substantial rework.

 Work item assignments are made “just in time.” This avoids blocking an item because a previously assigned team member is busy at the time the task is ready. (This chapter’s “Troubleshooting” section has more details.)

 time-boxing of Scrum sprints enforces artificial boundaries on plan changes, customer feedback, release dates, and process improvements.

 one required agenda item is asking whether any team members are blocked or otherwise need assistance, then assigning people (often the project manager) to resolve the issues. Experienced teams can complete the standup in five minutes.

 root-cause analysis exercise is undertaken to determine why a bug escaped the defenses of the core engineering team. This exercise identifies operational improvements that could prevent similar bugs from being released to customers in the future. This exercise could be part of your Develop or Validate done rule, but I prefer to have a specific step in the workflow to make the practice explicit. Examples of improvements include a more rigorous acceptance criteria definition, modification of development practices such as code review or unit testing procedures, testing in a staging area that mirrors production, or including a user acceptance test stage before releasing to a wider audience. The act of practicing continuous improvement is often called kaizen in Lean and Agile development circles.

 If your upstream dependencies define “complete,” “done,” and “ready” as code that is implemented but far from production-ready, you’ll need to mitigate the problem. Here are a few approaches: Treat unstable dependencies as you would late dependencies (described earlier in this section). This includes the options of using a Track column on your signboard, creating fakes or shims, or assisting your upstream partner team with implementation. This approach works best during the early portion of a project, when you’ve got time to do other work or extra work. Implement your work items on top of unstable dependencies, using a combination of fakes and shims to fill in gaps as necessary. You’ll need to create a new task for removing the fakes and shims and validate again when your upstream partner teams stabilize the dependencies. This approach is often required late in a project when you can’t delay implementation any longer. Align your Validate done rule with a lower quality bar. For example, you might replace the rule “The work is deployed to production, tried by a significant subset of real customers, and all issues found are resolved” with “The work is successfully integrated into the main branch, basic test cases function, and all issues found are logged in the bug-tracking system.” This passive “When in Rome, do as the Romans do” approach is far from ideal, but in certain situations, it may be the most pragmatic solution. Push your upstream partner teams to make their deliverables production-ready. Log bugs for every malfunctioning scenario, feature, story, and component; engage your partner teams on every bug; and drive for resolution on those bugs in time to meet your committed delivery dates. This aggressive approach can be effective, but you’ll need executive sponsorship to use it successfully, should your partner teams complain and escalate.

 I recommend using a test-driven development approach to address bugs. First, write a unit test (or an integration test) that exercises intended behavior. This test should fail because of the presence of the bug. Next, fix the bug, and then run the test again.

 Kanban regulates quality through a deceptively simple mechanism. Before a note card is moved from the left to the right column of a step, the work on that item must pass certain rules—your definition of “done” for that step (also known as the pull criteria).

 McGrath and MacMillan’s Options Portfolio has you place your current and future work focus on a two-dimensional grid. The higher you are on the vertical axis, the more execution risk is involved (technical or operational). The farther right you are on the horizontal axis, the more market risk is involved (customer or competitive). The lower-left corner tends to hold your current core capabilities. The upper right holds game-changing ideas. For strategic planning, you want a balanced portfolio, with work spread across all portions of the grid—not enough in the core and your current business suffers; not enough on the edges and you’ve got no future business.

 Separating the completion of one step from the initiation of the next decouples the steps. This frees you to have rules that define what it means to be done with each step, regardless of what the next step happens to be.

 The triage team typically consists of a representative of the customer-support team, a product manager (or business analyst or program manager), a development leader, and a QA leader. The primary goal of the triage team is to prevent distractions for the core engineering team. Specifically, the triage team does the following: Answers workaround and resolution feasibility questions without involving the rest of the core engineering team. Removes any duplicate escalations. Validates that enough data is supplied with the escalation. Stack-ranks any incoming escalations on the Kanban board. Recommends the release vehicle for any escalations that are immediately deemed bugs, such as a customer hotfix or general service pack. Ensures cross-team synchronization on new escalations as well as any escalations currently in progress.

 Specify done rule All items broken down into tasks that can be finished in less than a week each, and quick specs completed for each item. Implement done rule Code is reviewed and unit tested, the static analysis is clean, the code is checked in, acceptance tests pass, and the customer-facing documentation is complete. Validate done rule The work is deployed to production and tried by a significant subset of real customers. All issues found are resolved.

 Kanban distinguishes between finishing one step and starting the next. Of course, those are always two different things. However, signboards used for Scrum or other daily standup meetings typically move an item to the next step on the board as soon as it’s done, thus losing the important distinction between items ready for the next step and items actively in the next step.

 Choosing to write a detailed spec should not be a matter of dogma or habit. It should be a decision based on the needs of the team (and the customer, should the customer require it). If a feature or feature area is unclear, or the tradeoffs and architecture are in question, you should write a detailed spec and flesh out the design. Otherwise, a quick, informal electronic notebook or wiki should be sufficient.

 Investigate column tracks which issues are actively being investigated. Typical activities include clarifying the escalation, attempting to reproduce a problem, and identifying a suitable workaround. The Investigate done rule, which completes an escalation, is “Incident-tracking system updated with investigation results; customer notified; tasks to avoid future incidents created (such as writing a knowledge base article); and any resulting product bugs added to the second row of the signboard.” Modify your own done rule as you need to.

 Problem: The core engineering team is inundated with escalations from customer support, creating an unsustainable backlog Kanban provides an easy visualization of the number of escalations and bugs that a team must deal with. An excessive number of escalations may indicate one or more problems: The support team relies too much on the core engineering team. Use the triage team to help shield the core engineering team from distractions and to ensure that only the appropriate escalations get through. Difficult escalations result in long lead times. Aim to improve diagnostic tools (such as tracing and logging) to help resolve more technical problems. Insufficient help or documentation for customers and the support organization. The core engineering team should spend a reasonable amount of time prior to release educating stakeholders on new functionality. Post-ship product-quality issues. In the spirit of continuous improvement, work with the core engineering team to refine their processes and improve early cycle quality.

 My favorite steps that start prior to specification are from Scenario-Focused Engineering (SFE). Here’s what an SFE signboard might look like: The Backlog column contains high-level initiatives, each of which is a desired outcome for a target customer segment, such as “Immersive holographic environment for gamers” (a fictitious example). The Observe step takes a high-level initiative and observes the target customers, capturing everything about who they are, what they do, how they act, and why they care. The Observe done rule might be, “Captured mix of quantitative, qualitative, seeing, and doing customer data, and documented insights from that data.” The Frame step takes customer data and insights and uses them to frame a series of success metrics and SPICIER scenarios. (SPICIER stands for “tells a customer Story,” “includes Personal details,” “is Implementation-free,” “told in the Customer’s voice,” “reveals deep Insight about customer needs,” “includes Emotion and Environment,” and “is based on Research.”) The Frame done rule might be, “Produced a prioritized collection of SPICIER scenarios with associated success metrics.” The Brainstorm step takes a scenario and brainstorms all the different ways it could be brought to life. The choices that best fulfill the scenario and meet the requirements are considered for prototyping. The Brainstorm done rule might be, “Generated a dozen or more alternatives, and settled on three to five promising designs.” The Prototype step takes a design and rapidly conjures a prototype sufficient for customer feedback. That prototype could be a paper model, a PowerPoint animation, or a simple code change that can be the subject of A/B testing. The expectation is that your first guess won’t be quite right, so you want to spend just a few days on two or three variations and then get customer feedback. The Prototype done rule might be, “Captured customer feedback on one or more related prototypes.” Conceptually, note cards from prototyping might move back to the Brainstorm column or earlier if customer feedback indicates that more design work is needed. (In practice, you typically create new cards with a slightly different focus.) The Breakdown step is basically the Specify step from the Kanban quick-start guide (Chapter 2), but here much of the specification is already provided by the previously created scenarios, designs, prototypes, and customer feedback. The Breakdown done rule might be, “All items broken down to less than a week of work each, with specification materials available.” The remaining Implement and Validate steps are as described in the Kanban quick-start guide. You could also add on sections at the end to track deployments as described in Chapter 6. Once your product or service is deployed, you can get more customer feedback on working code, which is then fed back in for observation, framing, and brainstorming new ideas. Scenario-Focused Engineering relies heavily on iteration and customer feedback…

 At the beginning of the daily standup, the project manager starts at the last step, opening up slots when items are done, and works his way to the left. (Because of WIP limits, items can move to the right only if there’s room. Pulling cards from the left to the right is what makes Kanban a “pull” system.)

 Problem: The team is having problems planning for maintenance because it doesn’t know how many escalations will come its way Many teams struggle with unplanned work. This is the primary reason why Kanban is such a great model—there is less need to plan for an iteration; instead, accept unpredictability and stack-rank accordingly. Large backlogs of items might require you and others to set expectations, but a transparent backlog and signboard help shed light on the capacity and throughput of the core engineering team.

## An Elegant Puzzle: Systems of Engineering Management 

Baseline metrics are useful for narrowing the solution space that you explore in order to accomplish your investment goals. They are also useful for identifying when you should pause pursuing your goals and instead invest in platform quality.

 There are two particularly interesting kinds of goals: investments and baselines. Investments describe a future state that you want to reach, and baselines describe aspects of the present that you want to preserve.

 The two tests of an effective goal are whether someone who doesn’t know much about an area can get a feel for a goal’s degree of difficulty, and whether afterward they can evaluate if it was successfully achieved.

 Good goals are a composition of four specific kinds of numbers: A target states where you want to reach. A baseline identifies where you are today. A trend describes the current velocity. A time frame sets bounds for the change.

 A good vision is composed of: Vision statement: A one- or two-sentence aspirational statement to summarize the rest of the document. This is your core speaking point, which you will repeat at each meeting, planning period, and strategy review. It shouldn’t try to capture every detail of your vision, but it does need to memorably evoke your vision effectively. Value proposition: How will you be valuable to your users and to your company? What kinds of success will you enable them to achieve? There is a sequencing question of whether you should start with capabilities (the next bullet) and reason into value proposition or do the opposite, but I’ve found that starting from your users leads to visions that are both more ambitious and more grounded. Capabilities: What capabilities will the product, platform, or team need in order to deliver on your value proposition? Will it need to support multiple independent business lines? Will it need to deliver against the disparate needs of several distinct customer cohorts? Solved constraints: What are the constraints that you’re limited by today, but that in the future you’ll no longer be constrained by? For example, if you’re currently “spending into” developer velocity, perhaps in the future you’ll be able to achieve significant developer velocity while also maintaining low costs. Future constraints: What are the constraints that you expect to encounter in this wonderful future? Hopefully, these new constraints will be things that are easy to adjust, like funding or hiring. Reference materials: Link all the existing plans, metrics, updates, references, and documents into an appendix for those who want to understand more of the thinking that went into the vision. This allows you to shed complexity from your vision document without sacrificing context. Narrative: Once you’ve written the previous sections, the last step of writing a compelling vision is to synthesize all those details into a short—maybe one-page—narrative that serves as an easy-to-digest summary. In your final document, this is probably the second section, following the statement.

 If strategies describe the harsh trade-offs necessary to overcome a particular challenge, then visions describe a future in which those trade-offs are no longer mutually exclusive. An effective vision helps folks think beyond the constraints of their local maxima, and lightly aligns progress without requiring tight centralized coordination.

 When you apply your guiding policies to your diagnosis, you get your actions. Folks are often comfortable with hard decisions in the abstract, but struggle to translate policies into the specific steps to implement them.

 The diagnosis is a theory describing the challenge at hand. It calls out the factors and constraints that define the challenge, and at its core is a very thorough problem statement.

 A strategy recommends specific actions that address a given challenge’s constraints. A structure that I’ve found extremely effective13 is described in Good Strategy/Bad Strategy by Richard Rumelt,14 and has three sections: diagnosis, policies, and actions.

 Strategies are grounded documents which explain the trade-offs and actions that will be taken to address a specific challenge. Visions are aspirational documents that enable individuals who don’t work closely together to make decisions that fit together cleanly.

 The elements that I’ve found effective for solution validation are: Write a customer letter. Write the launch announcement that you would send after finishing the solution. Are you able to write something exciting, useful, and real? It’s much more useful to test it against your actual users than to rely on your intuition. Identify prior art. How do peers across the industry approach this problem? The fact that others have solved a problem in a certain way doesn’t mean that it’s a great way, but it does at least mean it’s possible. A mild caveat: it’s better to rely on people you have some connection to instead of on conference talks and such, since there is a surprisingly large amount of misinformation out there. Find reference users. Can you find users who are willing to be the first users for the solution? If you can’t, you should be skeptical whether what you’re building is worthwhile. Prefer experimentation over analysis. It’s far more reliable to get good at cheap validation than it is to get great at consistently picking the right solution.

 Users’ pain. What are the problems that your users experience? It’s useful to go broad via survey mechanisms, as well as to go deep by interviewing a smaller set of interesting individuals across different user segments. Users’ purpose. What motivates your users to engage with your systems? How can you better enable users to accomplish their goals?

 The first phase of a planning cycle is exploring the different problems that you could pick to solve. It’s surprisingly common to skip this phase, but that, unsurprisingly, leads to inertia-driven local optimization. Taking the time to evaluate which problem to solve is one of the best predictors I’ve found of a team’s long-term performance.

 These dimensions kind of intuitively make sense as measures of productivity, but let’s see if we can model them into a system that we can use to reason about developer productivity: Pull requests are converted into ready commits based on our code review rate. Ready commits convert into deployed commits at deploy rate. Deployed commits convert into incidents at defect rate. Incidents are remediated into reverted commits at recovery rate. Reverted commits are debugged into new pull requests at debug rate. Linking these pieces together, we see a feedback loop, in which the system’s downstream behavior impacts its upstream behavior. With a sufficiently high defect rate or slow recovery rate, you could easily see a world where each deploy leaves you even further behind.

 four measures of developer velocity: Delivery lead time is the time from the creation of code to its use in production. Deployment frequency is how often you deploy code. Change fail rate is how frequently changes fail. Time to restore service is the time spent recovering from defects.

 the idea of organizational debt. This is the organizational sibling of technical debt, and it represents things like biased interview processes and inequitable compensation mechanisms. These are systemic problems that are preventing your organization from reaching its potential. Like technical debt, these risks linger because they are never the most pressing problem. Until that one fateful moment when they are.

 Finally, a related antipattern is the gatekeeper pattern. Having humans who perform gatekeeping activities creates very odd social dynamics, and is rarely a great use of a human’s time. When at all possible, build systems with sufficient isolation that you can allow most actions to go forward. And when they do occasionally fail, make sure that they fail with a limited blast radius.

 if you can keep your interfaces generic, then you are able to skip the migration phase of system re-implementation, which tends to be the longest and trickiest phase, and you can iterate much more quickly and maintain fewer concurrent versions. There is absolutely a cost to maintaining this extra layer of indirection, but if you’ve already rewritten a system twice, take the time to abstract the interface as part of the third rewrite and thank yourself later.

 Finally, the one thing that I’ve found at companies with very few interruptions and have observed almost nowhere else: really great, consistently available documentation. It’s probably even harder to bootstrap documentation into a non-documenting company than it is to bootstrap unit tests into a non-testing company, but the best solution to frequent interruptions I’ve seen is a culture of documentation, documentation reading, and a documentation search that actually works.

 the real productivity killer is not system rewrites but the migrations that follow those rewrites. Poorly designed migrations expand the consequences of this rewrite loop from the individual teams supporting the systems to the entire surrounding organization.

 For every additional order of magnitude of engineers, you need to design and maintain a new layer of management. For every ~10 engineers, you need an additional team, which requires more coordination.14 Each engineer means more commits and deployments per day, creating load on your development tools. Most outages are caused by deployments, so more deployments drive more outages, which in turn require incident management, mitigations, and postmortems. Having more engineers leads to more specialized teams and systems, which require increasingly small on-call rotations so that your on-call engineers have enough system context to debug and resolve production issues. Consequently, relative time invested in on-call goes up.

 The other approach that I’ve seen work well is to rotate individuals for a fixed period into an area that needs help. The fixed duration allows them to retain their identity and membership in their current team, giving their full focus to helping out, rather than splitting their focus between performing the work and finding membership in the new team. This is also a safe way to measure how much slack the team really has!

 Shifting scope works better than moving people because it avoids re-gelling costs, and it preserves system behavior. Preserving behavior keeps your existing mental model intact, and if it doesn’t work out, you can always revert a workload change with less disruption than would be caused by a staffing change.

 My rule of thumb is that it takes eight engineers on a team to support a two-tier on-call rotation, so I’m generally reluctant to move any team with membership below that line. However, fixed costs come in many other varieties: “keeping the lights on” work, precommitted contracts, support questions from other teams, etc.

 Fundamentally, I believe that sustained productivity comes from high-performing teams, and that disassembling a high-performing team leads to a significant loss of productivity, even if the members are fully retained. In this worldview, high-performing teams are sacred, and I’m quite hesitant to disassemble them.

 Adding new individuals to a team disrupts that team’s gelling process, so I’ve found it much easier to have rapid growth periods for any given team, followed by consolidation/gelling periods during which the team gels. The organization will never stop growing, but each team will.

 The framework starts with a vocabulary for describing teams and their performance within their surrounding context. Teams are slotted into a continuum of four states: A team is falling behind if each week their backlog is longer than it was the week before. Typically, people are working extremely hard but not making much progress, morale is low, and your users are vocally dissatisfied. A team is treading water if they’re able to get their critical work done, but are not able to start paying down technical debt or begin major new projects. Morale is a bit higher, but people are still working hard, and your users may seem happier because they’ve learned that asking for help won’t go anywhere. A team is repaying debt when they’re able to start paying down technical debt, and are beginning to benefit from the debt repayment snowball: each piece of debt you repay leads to more time to repay more debt. A team is innovating when their technical debt is sustainably low, morale is high, and the majority of work is satisfying new user needs.

 Fitting together those guiding principles, the playbook that I’ve developed is surprisingly simple and effective: Teams should be six to eight during steady state. To create a new team, grow an existing team to eight to ten, and then bud into two teams of four or five. Never create empty teams. Never leave managers supporting more than eight individuals.

 Keep innovation and maintenance together. A frequent practice is to spin up a new team to innovate while existing teams are bogged down in maintenance. I’ve historically done this myself, but I’ve moved toward innovating within existing teams.5 This requires very deliberate decision-making and some bravery, but in exchange you’ll get higher morale and a culture of learning, and will avoid creating a two-tiered class system of innovators and maintainers.

 I’ve sponsored quite a few teams of one or two people, and each time I’ve regretted it. To repeat: I have regretted it every single time. An important property of teams is that they abstract the complexities of the individuals that compose them. Teams with fewer than four individuals are a sufficiently leaky abstraction that they function indistinguishably from individuals. To reason about a small team’s delivery, you’ll have to know about each on-call shift, vacation, and interruption.

 On-call rotations want eight engineers For production on-call responsibilities,4 I’ve found that two-tier 24/7 support requires eight engineers. As teams holding their own pagers have become increasingly mainstream, this has become an important sizing constraint, and I try to ensure that every engineering team’s steady state is eight people. Shared rotations. It is sometimes necessary to pool multiple teams together to reach the eight engineers necessary for a 24/7 on-call rotation. This is an effective intermediate step toward teams owning their own on-call rotations, but it is not a good long-term solution. Most folks find being on-call for components that they’re unfamiliar with to be disproportionately stressful.

 Organizational design gets the right people in the right places, empowers them to make decisions, and then holds them accountable for their results.

 Compounding leverage. What are the composable blocks you could start building today that would compound into major product or technical leverage10 over time? I think of this category of work as finding ways to get the benefit at least twice. These are potentially tasks that initially don’t seem important enough to prioritize, but whose compounding value makes the work possible to prioritize.

 Competitive moats. Moats are a more extreme version of a competitive advantage. Moats represent a sustaining competitive advantage, which makes it possible for you to pursue offerings that others simply cannot. It’s useful to consider moats in three different ways: What do your existing moats enable you to do today? What are the potential moats you could build for the future? What moats are your competitors luxuriating behind?

 you only get value from projects when they finish: to make progress, above all else, you must ensure that some of your projects finish.

## Apprenticeship Patterns: Guidance for the Aspiring Software Craftsman 

As you begin to make the transition to the role of journeyman you will become less dependent on these skills, as you start to be hired on the basis of your reputation, your portfolio of previous work, and the deeper qualities you bring to a team. Until then, your virtues must be a little more overt.

 Expertise is a by-product of the long road we’re all on, but it is not the destination.

 Eventually you’ll acquire a toolbox of tricks and subtleties gleaned from other people’s code. This hones your ability to solve small problems quickly and easily, just because you’ve seen something similar before. You’ll be able to tackle problems that others consider impossible because they don’t have access to your toolbox.

 Having knowledge is not the same as having the skill and practical ability to apply that knowledge to create software applications. This is where craftsmanship comes in. — Pete McBreen, Software Craftsmanship

 One of the most important traits that a craftsman can possess is the ability to learn, identifying an area of ignorance and working to reduce it. Like bare patches in a garden, ignorance can be reduced by cultivating your seeds of knowledge.

 If you’re only skimming the surface, then you won’t know the things you don’t know, and without understanding the bounds of your knowledge you can’t discover new things.

 Your grandmother may have told you that practice makes perfect. She was wrong. In fact, practice makes permanent. So be careful what you practice, and constantly evaluate it to ensure you haven’t gone stale. Choosing the right thing to practice every day is a skill almost as important as the act of repeated practice.

 Successful apprentices learn to create situations where they can quickly and frequently receive data about whether they need to do more or less of an activity. This often means learning to communicate your ideas and listening without interrupting.

 When you read a tutorial, you should not be looking for code to copy but for a mental structure in which to place your new knowledge.

 This is why your goal should be to become skilled rather than experienced. The increase in your skill level is the only meaningful testament to the effort you have spent inspecting, adapting, and improving your working habits.

 Focus on delivering value to your customer over advancing your own self-interests.

 A pattern language is an interconnected set of solutions to common problems in a specific domain.

 The length of the journey merely multiplies the possibilities that are open to you.

 Show the people who are depending on you that the learning process is part of delivering software. Let them see you grow.

 The concrete skills you possess are your answer to the question: “If we hire you today, what can you do on Monday morning that will benefit us?”

 willing to Expose Your Ignorance as well. Using this pattern in isolation (that is, confronting your ignorance without exposing it) runs the risk of encouraging a culture where failure and learning are unacceptable because everybody does their learning in secret. Remember that learning in public is one of the ways in which an apprentice begins the transition to journeyman. It’s a small step from learning where people can see you to teaching.

 important to be aware of the distinction that systems thinkers make between reinforcing and balancing feedback. Reinforcing feedback encourages you to do more of something. Balancing feedback encourages you to do less of something. By combining the two types of feedback, a system can be kept relatively stable by making lots of small adjustments.

 As an apprentice, one of the beliefs that can hold you back is the idea that the people who built the tools that you depend on are somehow different or special or better than you are.

 Even though we advocate seeking out the most challenging tasks you are capable of, you still need to remember that if the water level is above your head it means you’re drowning.

 Risks are opportunities seen through the half-shut eyes of fear.

 Software craftsmen build their reputations through strong relationships with their clients and colleagues. Conceding to unspoken pressures and telling people what they want to hear is not a good way to build strong relationships. Tell people the truth. Let them know that you’re starting to understand what they want and you’re in the process of learning how to give it to them. If you reassure them, reassure them with your ability to learn, not by pretending to know something you don’t. In this way, your reputation will be built upon your learning ability rather than what you already know.

 The more experience you already have, the more effort you will need to put into “emptying your cup,” clearing your mind of bad habits, setting aside the pride you have in your skills, and opening yourself up to the different, often counterintuitive, approaches of your more experienced colleagues.

 Mastery involves taking that skill and turning it into a magnifying glass that can enhance the skills of others by orders of magnitude.

 For every step you take toward mastery, your destination moves two steps further away. Embrace mastery as a lifelong endeavor. Learn to love the journey. — George Leonard, Mastery

 For each person, identify five discrete skills noted on the CV, and determine which of these skills would be immediately useful on the kind of team you want to join. Put together a plan and a toy project that will demonstrate that you have acquired these skills.

 If you hang on long enough, people will start calling you “experienced,” but that should not be your goal. All experience indicates is that you have been able to survive. It does not indicate the amount you have learned, only the time you have spent.

 Useful feedback is data that can be acted upon and that gives you the option of doing more or less of a certain behavior. If you can’t do anything about it, then it’s not useful feedback.

 Criticism on its own is seldom useful feedback because it doesn’t tell you what is expected of you.

 In short, masters view the acquisition, usage, and sharing of superior skill as the most important part of being a software craftsman.

 Your goal is to measure your abilities and find ways to be better than you were yesterday. We’re all on the same journey, and comparing ourselves to others is useful only when it allows us to find ways to help each other improve.

 just telling people to do things doesn’t create lasting or sustainable change. When the people you’ve advised encounter a situation that isn’t covered by the rules, they’re lost. However, if those same people have imbibed the values that underpin the rules, they can come up with new rules to fit any situation.

## Clean Code: A Handbook of Agile Software Craftsmanship (Robert C. Martin Series) 

Anything that forces you to check the function signature is equivalent to a double-take. It’s a cognitive break and should be avoided.

 In order to make sure our functions are doing “one thing,” we need to make sure that the statements within our function are all at the same level of abstraction.

 another way to know that a function is doing more than “one thing” is if you can extract another function from it with a name that is not merely a restatement of its implementation

 There are several problems with this function. First, it’s large, and when new employee types are added, it will grow. Second, it very clearly does more than one thing. Third, it violates the Single Responsibility Principle7 (SRP) because there is more than one reason for it to change. Fourth, it violates the Open Closed Principle8 (OCP) because it must change whenever new types are added.

 This implies (as in the example above) that if the keyword try exists in a function, it should be the very first word in the function and that there should be nothing after the catch/finally blocks.

 Avoid Disinformation Programmers must avoid leaving false clues that obscure the meaning of code.

 Sometimes a comment goes beyond just useful information about the implementation and provides the intent behind a decision.

 Functions should hardly ever be 20 lines long.

 When a function seems to need more than two or three arguments, it is likely that some of those arguments ought to be wrapped into a class of their own. Consider, for example, the difference between the two following declarations:    Circle makeCircle(double x, double y, double radius);    Circle makeCircle(Point center, double radius);

 The proper use of comments is to compensate for our failure to express ourself in code.

 Make Meaningful Distinctions

 We want the code to read like a top-down narrative.5 We want every function to be followed by those at the next level of abstraction so that we can read the program, descending one level of abstraction at a time as we read down the list of functions. I call this The Step-down Rule.

 The solution to this problem (see Listing 3-5) is to bury the switch statement in the basement of an ABSTRACT FACTORY,9 and never let anyone see it. The factory will use the switch statement to create appropriate instances of the derivatives of Employee, and the various functions, such as calculatePay, isPayday, and deliverPay, will be dispatched polymorphically through the Employee interface.

 Inaccurate comments are far worse than no comments at all. They delude and mislead. They set expectations that will never be fulfilled. They lay down old rules that need not, or should not, be followed any longer.

 One difference between a smart programmer and a professional programmer is that the professional understands that clarity is king. Professionals use their powers for good and write code that others can understand.

 Function Arguments The ideal number of arguments for a function is zero (niladic). Next comes one (monadic), followed closely by two (dyadic). Three arguments (triadic) should be avoided where possible. More than three (polyadic) requires very special justification—and then shouldn’t be used anyway.

 There are times, of course, where two arguments are appropriate. For example, Point p = new Point(0,0); is perfectly reasonable. Cartesian points naturally take two arguments. Indeed, we’d be very surprised to see new Point(0). However, the two arguments in this case are ordered components of a single value!

 So accountGroup or bunchOfAccounts or just plain accounts would be better. 1. As we’ll see later on, even if the container is a List, it’s probably better not to encode the container type into the name.

 Each blank line is a visual cue that identifies a new and separate concept.

 Others who see that commented-out code won’t have the courage to delete it. They’ll think it is there for a reason and is too important to delete. So commented-out code gathers like dregs at the bottom of a bad bottle of wine.

 Flag arguments are ugly. Passing a boolean into a function is a truly terrible practice. It immediately complicates the signature of the method, loudly proclaiming that this function does more than one thing. It does one thing if the flag is true and another if the flag is false!

 Arguments are even harder from a testing point of view. Imagine the difficulty of writing all the test cases to ensure that all the various combinations of arguments work properly.

 Error Handling Is One Thing

 If you follow the rules herein, your functions will be short, well named, and nicely organized. But never forget that your real goal is to tell the story of the system, and that the functions you write need to fit cleanly together into a clear and precise language to help you with that telling.

 Listing 3-4 Payroll.java    public Money calculatePay(Employee e)    throws InvalidEmployeeType {        switch (e.type) {          case COMMISSIONED:            return calculateCommissionedPay(e);          case HOURLY:            return calculateHourlyPay(e);          case SALARIED:            return calculateSalariedPay(e);          default:            throw new InvalidEmployeeType(e.type);        }      }

 Use Intention-Revealing Names

 On the other hand, if you use exceptions instead of returned error codes, then the error processing code can be separated from the happy path code and can be simplified:

 Use Searchable Names

 when you find yourself in a position where you need to write a comment, think it through and see whether there isn’t some way to turn the tables and express yourself in code. Every time you express yourself in code, you should pat yourself on the back. Every time you write a comment, you should grimace and feel the failure of your ability of expression.

 Avoid Mental Mapping

 In general output arguments should be avoided. If your function must change the state of something, have it change the state of its owning object.

 And all too often the comments get separated from the code they describe and become orphaned blurbs of ever-decreasing accuracy.

 If openness separates concepts, then vertical density implies close association. So lines of code that are tightly related should appear vertically dense. Notice how the useless comments in Listing 5-3 break the close association of the two instance variables.

 A comment like this can sometimes be useful, but it is better to use the name of the function to convey the information where possible.

 Noise words are redundant. The word variable should never appear in a variable name. The word table should never appear in a table name. How is NameString better than Name? Would a Name ever be a floating point number? If so, it breaks an earlier rule about disinformation. Imagine finding one class named Customer and another named CustomerObject. What should you understand as the distinction? Which one will represent the best path to a customer’s payment history?

 Truth can only be found in one place: the code. Only the code can truly tell you what it does.

 The first rule of functions is that they should be small. The second rule of functions is that they should be smaller than that.

 A comment may be used to amplify the importance of something that may otherwise seem inconsequential.

 Sometimes it is useful to warn other programmers about certain consequences. For example, here is a comment that explains why a particular test case is turned off:

 For instance, it’s confusing to have fetch, retrieve, and get as equivalent methods of different classes.

 After all, the reason we write functions is to decompose a larger concept (in other words, the name of the function) into a set of steps at the next level of abstraction.

 Pick One Word per Concept

 Functions should do one thing. Error handing is one thing. Thus, a function that handles errors should do nothing else.

 Prefer Exceptions to Returning Error Codes Returning error codes from command functions is a subtle violation of command query separation. It promotes commands being used as expressions in the predicates of if statements.

 Functions that do one thing cannot be reasonably divided into sections.

 Code formatting is about communication, and communication is the professional developer’s first order of business.

 Any comment that forces you to look in another module for the meaning of that comment has failed to communicate to you and is not worth the bits it consumes.

 Do not refer to a grouping of accounts as an accountList unless it’s actually a List.

 Don’t Pun Avoid using the same word for two purposes. Using the same term for two different ideas is essentially a pun.

 Functions should either do something or answer something, but not both.

 Have No Side Effects Side effects are lies. Your function promises to do one thing, but it also does other hidden things.

## Cold Calling Techniques (That Really Work!) 

Most salespeople think they have to say something unique or provocative to grab a prospect’s attention. Such as, “If I could show you a way in which you could …” Actually, that approach builds mistrust and makes your job harder.

 regain control of a conversation by asking a question.

 Instead of asking, “What’s a better time to call?” I say: “Mr. Jones, the only reason I was calling was to set an appointment. Would next Tuesday at 3:00 be okay?”

 The biggest mistake most salespeople make is that they fail to ask directly and specifically for the appointment.

 responses roll into each other. They’re not isolated. Very rarely does anybody simply say “no.” People usually say “no,” and add a story of some kind: “No, I’m not interested because this is what we’re doing now.” My experience is that it’s the second response that really matters. Once you understand that, you can start to see how well what you’re suggesting is going to work. The key is the second response, not the first.

 My rule of thumb is that three sales calls to the same person is enough. I typically either close on my third call or conclude that the sale isn’t going to happen right now.

 The easiest, simplest way of opening up and getting the prospect’s attention is by saying his or her name. Call up and say, “Good morning, Mr. Jones.”

## Crucial Conversations Tools for Talking When Stakes Are High, Second Edition (Business Books) 

Second, clarify what you really don’t want. This is the key to framing the and question.

 The Pool of Shared Meaning is the birthplace of synergy.

 the real problem never was in the process, system, or structure—it was in employee behavior. The key to real change lies not in implementing a new process, but in getting people to hold one another accountable to the process.

 Third, present your brain with a more complex problem. Finally, combine the two into an and question that forces you to search for more creative and productive options than silence and violence.

 The mistake most of us make in our crucial conversations is we believe that we have to choose between telling the truth and keeping a friend.

 Each of us enters conversations with our own opinions, feelings, theories, and experiences about the topic at hand. This unique combination of thoughts and feelings makes up our personal pool of meaning. This pool not only informs us, but also propels our every action. When two or more of us enter crucial conversations, by definition we don’t share the same pool.

 First, clarify what you really want. You’ve got a head start if you’ve already Started with Heart. If you know what you want for yourself, for others, and for the relationship, then you’re in position to break out of the Fool’s Choice.

 The predictor of success or failure was whether people could hold five specific crucial conversations. For example, could they speak up if they thought the scope and schedule were unrealistic? Or did they go silent when a cross-functional team member began sloughing off? Or even more tricky—what should they do when an executive failed to provide leadership for the effort?

 Of course, as others push back, trying to prove their points, it’s not long until we change our goal from correcting mistakes to winning.

 Crucial Conversation kr shel kän´ vr sa´ shen) n A discussion between two or more people where (1) stakes are high, (2) opinions vary, and (3) emotions run strong.

 In the worst companies, poor performers are first ignored and then transferred. In good companies, bosses eventually deal with problems. In the best companies, everyone holds everyone else accountable—

 The single biggest problem in communication is the illusion that it has taken place. —GEORGE BERNARD SHAW

 People who are skilled at dialogue do their best to make it safe for everyone to add their meaning to the shared pool—even ideas that at first glance appear controversial, wrong, or at odds with their own beliefs. Now, obviously, they don’t agree with every idea; they simply do their best to ensure that all ideas find their way into the open.

 When it comes to risky, controversial, and emotional conversations, skilled people find a way to get all relevant information (from themselves and others) out into the open.

 The best at dialogue refuse Fool’s Choices by setting up new choices. They present themselves with tougher questions—questions that turn the either/or choice into a search for the all-important and ever-elusive and.

 close to 80 percent of the projects that require cross-functional cooperation cost far more than expected, produce less than hoped for, and run significantly over budget.

 Most leaders get it wrong. They think that organizational productivity and performance are simply about policies, processes, structures, or systems. So when their software product doesn’t ship on time, they benchmark others’ development processes. Or when productivity flags, they tweak their performance management system. When teams aren’t cooperating, they restructure. Our research shows that these types of nonhuman changes fail more often than they succeed.

 practice doesn’t make perfect; perfect practice makes perfect. This means that first you have to know what to practice.

## Founders at Work: Stories of Startups' Early Days 

People like the idea of innovation in the abstract, but when you present them with any specific innovation, they tend to reject it because it doesn't fit with what they already know.

 almost all the founders I interviewed changed their ideas as they developed them. PayPal started out writing encryption software, Excite started as a database search company, and Flickr grew out of an online game.

 make sure you write a business plan because it will crystallize your thoughts to communicate your ideas with somebody else. Make sure that once you have written your business plan, you have somebody read and critique it and ask you questions.

 try to make valuable what you're good at.

 As Howard Aiken said, "Don't worry about people stealing your ideas. If your ideas are any good, you'll have to ram them down people's throats."

 determination is the single most important quality in a startup founder.

 Essentially it's a plan that says what the company is going to do, what problem it is going to solve, how big the market is, what the sources of revenue for the company are, what your exit strategy is for your investors, what amount of money is required, how you are going to market it, what kind of people you need, what the technology risks are, marketing risks, execution risks. Those are the fundamentals of what goes into a business plan, and many people have it in their heads but don't write it down.

 A business plan is nothing more than your own communication to a person not sitting in front of you—an

 We realized that the way we were attacking these things was just fundamentally flawed. So Bob and I built this system that was part visualization package, part graph balancing tool, that would try to represent large-scale travels of money in the system in a visual form. Taking that as a base, we built all these different tools that would allow computers to predict where particularly expensive losses would be and then represent the networks of losses to the investigators in such a way that they could very quickly make a decision whether or not to pursue a particular case.

 I see way too many people give up in the startup world. They just give up too easily. Recruiting is a classic example. I don't even hear the first "no" that somebody says. When they say, "No, I'm not interested," I think, "Now it's a real challenge. Now's when the tough part begins." It's hard to identify talent, but great people don't look for jobs, great people are sold on jobs. And if they're sold they're going to say no at first. You have to win them over.

 If you have a good team, you are halfway there. Even more importantly, perhaps, you have to have a really strong cofounder. Someone you can rely on in a very fundamental way.

 Starting a startup is a process of trial and error. What guided the founders through this process was their empathy for the users. They never lost sight of making things that people would want.

 I had wanted a computer my whole life. Back in high school I told my dad, "I'm going to have a computer someday." And he said that it cost as much as a house—the down payment on a house. And I said, "Well, I'll live in an apartment."

 The default of how you do these things is very powerful, if you've been in the industry for a long time. So we were sort of beneficiaries of our naïveté. We thought, "We don't know how to do this; let's just invent it."

 don't try to change user behavior dramatically. If you are expecting people to dramatically change the way they do things, it's not going to happen. Try to make it such that it's a small change, yet an important one.

 existing companies' biggest problem is legacy. Period. They can't focus on new businesses because they've got to manage their old ones.

## How Not to Be Wrong: The Power of Mathematical Thinking 

asking, “What assumptions are you making? And are they justified?”

 Here’s an old mathematician’s trick that makes the picture perfectly clear: set some variables to zero. In this case, the variable to tweak is the probability that a plane that takes a hit to the engine manages to stay in the air. Setting that probability to zero means a single shot to the engine is guaranteed to bring the plane down. What would the data look like then? You’d have planes coming back with bullet holes all over the wings, the fuselage, the nose—but none at all on the engine.

 Nonlinear thinking means which way you should go depends on where you already are.

 The military analyst has two options for explaining this: either the German bullets just happen to hit every part of the plane but one, or the engine is a point of total vulnerability. Both stories explain the data, but the latter makes a lot more sense. The armor goes where the bullet holes aren’t.

## Impact Mapping: Making a big impact with software products and projects 

A common problem with measurements is that they can change from being the means to control the success of a project to an end in itself. In Seeing like a state, James C. Scott warns about the conflict between two levels of metrics: the ones that provide understanding and control to people outside the process being measured, and the ones that are important for the people inside, affected by the process.

 In How to Measure Anything, Douglas Hubbard warns about a common psychological tendency to track what is easy to measure instead of what can inform good decisions. Hubbard says that information is valuable if it reduces uncertainty about decisions, and that the “value of measuring a variable is often inversely proportional to the attention it gets”.

 Based on a seven year long research of companies across the European Union, John McManus and Trevor Wood-Harper list the following as the top five key reasons why IT projects fail: Business reasons Business strategy superseded Business processes change (poor alignment) Poor requirements management Business benefits not clearly communicated or overstated

 By visually grouping together different deliverables that could contribute to the same impact, maps allow us to spot over-complicated solutions and prevent over-engineering. They facilitate thinking about alternatives, helping delivery teams come up with simpler, cheaper and faster alternative deliverables that achieve the desired effect. Because of this, impact maps make it is easy to argue that more complex solutions should be discarded or at least postponed until simpler suggestions are proven wrong.

 To use impact maps for roadmap management, you need: agreement that your aim is to achieve a business goal, not deliver pre-set scope frequent, iterative releases to measure progress agreement on metrics that express stakeholder expectations for the central business goal

 Once a deliverable is shipped, we can measure the actual changes in actors' behaviour and the impact on the overall objective. We can then re-evaluate our strategy and decide whether to continue working on the same part of the map or move on to something else.

 An impact map communicates scope, goals and priorities, but also assumptions on two levels. The first is that a deliverable will cause a change in behaviour of an actor, produce an impact. The second is that once the impact is achieved, the relevant actor will contribute to the overall objectives.

 Impact maps bridge the two worlds: they facilitate strategic planning and thinking to create a big-picture view focused on key business objectives, but also facilitate learning through delivery and help us manage project roadmaps. They represent and organise delivery scope in a way that is easy to evolve, reprioritise, grow and shrink as necessary to react to changed market opportunities or new knowledge.

 An impact map puts all the deliverables in the context of the impacts that they are supposed to support. This helps with breaking deliverables down into independent chunks that provide clear business value, and helps us launch something valuable sooner. A clear hierarchy allows us to group related deliverables, compare them and avoid over-investing in less important actors or impacts. It also helps us to throw out deliverables that do not really contribute to any important impact for a particular goal. Finally, by connecting deliverables to impacts and goals, a map shows the chain of reasoning that led to a feature suggestion, visualising the assumptions of stakeholders. This allows us to scrutinise those decisions better and re-evaluate them as new information becomes available through delivery.

 Once we have the first three questions answered, we can talk about scope. The third level of an impact map answers the following question: What can we do, as an organisation or a delivery team, to support the required impacts? These are the deliverables, software features and organisational activities.

 Impacts are not product features. Avoid listing software ideas here, focus on business activities.

 The second level of an impact map sets the actors in the perspective of our business goal. It answers the following questions: How should our actors' behaviour change? How can they help us to achieve the goal? How can they obstruct or prevent us from succeeding? These are the impacts that we're trying to create.

 The first level of an impact map provides answers to the following questions: Who can produce the desired effect? Who can obstruct it? Who are the consumers or users of our product? Who will be impacted by it? These are the actors who can influence the outcome.

 Goals should not be about building products or delivering project scope. They should explain why such a thing would be useful. Goals should present the problem to be solved, not the solution. Avoid design constraints in a goal definition.

 The purpose of a goal definition is to allow the delivery organisation and business sponsors to re-evaluate the plan as new information becomes available. For this reason, good goals tend to be SMART: Specific, Measurable, Action-oriented, Realistic and Timely.

 Assumptions validated by consistent data from actual experiments enable the creation of real value. An impact map connects candidate causes with desired effects. It is a map of assumptions connecting causes and effects. It helps you to find the right questions, which is much more difficult than finding good answers.

 Agile approaches use ‘working software’ as this visualization by rapidly implementing small collections of user stories which non-software disciplines can provide feedback on. However, while working software can validate choices, it does not help a lot with discovering and selecting those sets of user stories whose implementation will delight the people who will use the solution to achieve the overall purpose.

 If a product milestone or project succeeds in delivering the expected business goal, it is a success from a business perspective, even if the delivered scope ends up being different from what was originally envisaged.

 disparate perspectives and even vocabularies dominating each discipline make unambiguous communication difficult.

## Kanban: Workflow Visualized: An Expert's Guide 

Some of the things that your team should agree upon before starting will include the following: The initial limits for WIP and any policies that can be in place in order to change those limits or break them temporarily. The process for prioritizing or selecting the features that needs to be done. The policies for the way you will classify your services. This could be things like fixed delivery date, expedite, or standard. Determine if you need to provide estimates. And when the team has to choose the work they will do, how will they make this selection. How often reviews should be done to ensure the system is still working.

## Made to Stick: Why Some Ideas Survive and Others Die 

concrete details don’t just lend credibility to the authorities who provide them; they lend credibility to the idea itself.

 The homeowners who got information about cable subscribed at a rate of 20 percent, which was about the same as the rest of the neighborhood. But the homeowners who imagined themselves subscribing to cable subscribed at a rate of 47 percent. The research paper, when it was published, was subtitled “Does Imagining Make It So?” The answer was yes.

 When Boeing prepared to launch the design of the 727 passenger plane in the 1960s, its managers set a goal that was deliberately concrete: The 727 must seat 131 passengers, fly nonstop from Miami to New York City, and land on Runway 4-22 at La Guardia. (The 4-22 runway was chosen for its length—less than a mile, which was much too short for any of the existing passenger jets.) With a goal this concrete, Boeing effectively coordinated the actions of thousands of experts in various aspects of engineering or manufacturing. Imagine how much harder it would have been to build a 727 whose goal was to be “the best passenger plane in the world.”

 The choice may seem to be a difficult one: (1) accuracy first, at the expense of accessibility; or (2) accessibility first, at the expense of accuracy.

 This challenge—asking customers to test a claim for themselves—is a “testable credential.” Testable credentials can provide an enormous credibility boost, since they essentially allow your audience members to “try before they buy.”

 To make our communications more effective, we need to shift our thinking from “What information do I need to convey?” to “What questions do I want my audience to ask?”

 PUNCH LINE:When we use statistics, the less we rely on the actual numbers the better. The numbers inform us about the underlying relationship, but there are better ways to illustrate the underlying relationship than the numbers themselves. Juxtaposing the deer and the shark is similar to Ainscow’s use of BBs in a bucket.

 Curiosity, he says, happens when we feel a gap in our knowledge.

 Testable credentials are useful in many domains. For example, take the question “Are you better off now than you were four years ago?” Ronald Reagan famously posed this question to the audience during his 1980

 Schemas help us create complex messages from simple materials.

 Lee realizes that serving food is a job, but improving morale is a mission. Improving morale involves creativity and experimentation and mastery. Serving food involves a ladle.

 This is the most important thing to remember about using statistics effectively. Statistics are rarely meaningful in and of themselves. Statistics will, and should, almost always be used to illustrate a relationship. It’s more important for people to remember the relationship than the number.

 two essential emotions—surprise and interest—that are commonly provoked by naturally sticky ideas.

 A commercial claiming that a new shampoo makes your hair bouncier has less credibility than hearing your best friend rave about how a new shampoo made her own hair bouncier. Well, duh. The company wants to sell you shampoo. Your friend doesn’t, so she gets more trust points. The takeaway is that it can be the honesty and trustworthiness of our sources, not their status, that allows them to act as authorities.

 A great way to avoid useless accuracy, and to dodge the Curse of Knowledge, is to use analogies. Analogies derive their power from schemas: A pomelo is like a grapefruit. A good news story is structured like an inverted pyramid. Skin damage is like aging. Analogies make it possible to understand a compact message because they invoke concepts that you already know.

 Belief counts for a lot, but belief isn’t enough. For people to take action, they have to care.

 There is value in sequencing information—not dumping a stack of information on someone at once but dropping a clue, then another clue, then another. This method of communication resembles flirting more than lecturing.

 “I also found something I had not expected—the most successful of these pieces all began with a mystery story. The authors described a state of affairs that seemed to make no sense and then invited the reader into the material as a way of solving the mystery.”

 The availability bias is a natural tendency that causes us, when estimating the probability of a particular event, to judge the event’s probability by its availability in our memory. We intuitively think that events are more likely when they are easier to remember. But often the things we remember are not an accurate summary of the world.

 But in many circumstances this is a false choice for one compelling reason: If a message can’t be used to make predictions or decisions, it is without value, no matter how accurate or comprehensive it is.

 He says that the WIIFY—“what’s in it for you,” pronounced whiff-y—should be a central aspect of every speech.

 Why do we care that Michael Jordan likes McDonald’s? Certainly he is not a certified nutritionist or a world-class gourmet. We care because we want to be like Mike, and if Mike likes McDonald’s, so do we. If Oprah likes a book, it makes us more interested in that book. We trust the recommendations of people whom we want to be like.

 This approach is inspired by the gap theory. The goal is not to summarize; it’s to make you care about knowing something, and then to tell you what you want to know.

 beginning algebra students, who can solve complex equations but grind to a halt when they’re presented with a simple word problem that involves exactly the same math. Problem X doesn’t always identify itself as Problem X.

 The most basic way to get someone’s attention is this: Break a pattern.

 The use of schemas can sometimes involve a somewhat slower route to the “real truth.”

 distinction between gimmicky surprise, like dot-com ads, and meaningful post-dictable surprise.

 Why is this story format more interesting? Because it allows his lunch partners to play along. He’s giving them enough information so that they can mentally test out how they would have handled the situation.

 uses a simple but effective testable credential: Which problem do you think kills more people? With any luck, readers will botch at least one of the predictions, thus illustrating for themselves the reality of the availability bias.

 So where’s the emotion in “relativity” and in “unique”? Here’s the punch line: The most basic way to make people care is to form an association between something they don’t yet care about and something they do care about.

 These results are shocking. The mere act of calculation reduced people’s charity. Once we put on our analytical hat, we react to emotional appeals differently. We hinder our ability to feel.

 Making people commit to a prediction can help prevent overconfidence. Eric Mazur, a physics professor at Harvard, came up with a pedagogical innovation known as “concept testing.” Every so often in his classes, Mazur will pose a conceptual question and then ask his students to vote publicly on the answer. The simple act of committing to an answer makes the students more engaged and more curious about the outcome.

 the team members tied a sample of each material to the back bumper of their rental car, then drove around the parking lot with the materials dragging behind. They kept this up until the police came and told them to knock it off. The verdict was that the new plastic composite held up just as well as the traditional metal. Decision made.

 “First and foremost, try to get self-interest into every headline you write. Make your headline suggest to readers that here is something they want.

 The first step in motivating the hospital staff to change was to get them to realize that there was a problem and get them to care about it.

 The more that training simulates the actions we must take in the world, the more effective it will be.

 Unexpected ideas, by opening a knowledge gap, tease and flirt. They mark a big red X on something that needs to be discovered but don’t necessarily tell you how to get there.

 Why does this happen? Because concreteness is a way of mobilizing and focusing your brain. For another example of this phenomenon, consider these two statements: (1) Think of five silly things that people have done in the world in the past ten years. (2) Think about five silly things your child has done in the past ten years.

 “The most frequent reason for unsuccessful advertising is advertisers who are so full of their own accomplishments (the world’s best seed!) that they forget to tell us why we should buy (the world’s best lawn!).” An old advertising maxim says you’ve got to spell out the benefit of the benefit.

 People often trust their intuition, but our intuition is flawed by identifiable biases. Still, most people feel pretty good about their intuition, and it’s hard to convince them otherwise. This is the uphill battle faced by psychologists who study decision-making.

 The Creativity plot involves someone making a mental breakthrough, solving a long-standing puzzle, or attacking a problem in an innovative way. It’s the MacGyver plot.

 An expert on folk legends, Jan Brunvand, says that legends “acquire a good deal of their credibility and effect from their localized details.” A person’s knowledge of details is often a good proxy for her expertise.

 There are variations of the Challenge plot that we all recognize: the underdog story, the rags-to-riches story, the triumph of sheer willpower over adversity. The key element of a Challenge plot is that the obstacles seem daunting to the protagonist. Jared slimming down to 180 pounds is a Challenge plot. Jared’s 210-pound neighbor shaving an inch off his waistline is not.

 Abstraction makes it harder to understand an idea and to remember it. It also makes it harder to coordinate our activities with others, who may interpret the abstraction in very different ways. Concreteness helps us avoid these problems.

 Good teachers intuitively use lots of schemas.

 process—exploiting terms and concepts for their emotional associations—is a common characteristic of communication. People tend to overuse any idea or concept that delivers an emotional kick. The research labeled this overuse “semantic stretch.”

 perhaps the most important part of the story is this: “Group interest” is often a better predictor of political opinions than self-interest. Kinder says that in forming opinions people seem to ask not “What’s in it for me?” but, rather, “What’s in it for my group?” Our group affiliation may be based on race, class, religion, gender, region, political party, industry, or countless other dimensions of difference.

 Here is the bottom line for our everyday purposes: If you want your ideas to be stickier, you’ve got to break someone’s guessing machine and then fix it.

 So, a good process for making your ideas stickier is: (1) Identify the central message you need to communicate—find the core; (2) Figure out what is counterintuitive about the message—i.e., What are the unexpected implications of your core message? Why isn’t it already happening naturally? (3) Communicate your message in a way that breaks your audience’s guessing machines along the critical, counterintuitive dimension. Then, once their guessing machines have failed, help them refine their machines.

 Should both parties learn greater empathy for the other and, in essence, meet in the middle? Actually, no. The solution is for the engineers to change their behavior. Why? As Bechky notes, the physical machine was the most effective and relevant domain of communication. Everyone understands the machines fluently. Therefore problems should be solved at the level of the machine.

 Surprise is triggered when our schemas fail, and it prepares us to understand why the failure occurred.

 Stories are effective teaching tools. They show how context can mislead people to make the wrong decisions. Stories illustrate causal relationships that people hadn’t recognized before and highlight unexpected, resourceful ways in which people have solved problems.

 When they share their lessons—“Keep the lines of communication open”—they’re hearing a song, filled with passion and emotion, inside their heads. They’re remembering the experiences that taught them those lessons—the struggles, the political battles, the missteps, the pain. They are tapping. But they forget that the audience can’t hear the same tune they hear.

 Stories are like flight simulators for the brain.

 The third major type of inspirational story is the Creativity plot.

 Accuracy to the point of uselessness is a symptom of the Curse of Knowledge.

 The Drag Test is a Creativity plot that reinforced the team’s new culture. The Drag Test implied, “We still need to get the right data to make decisions. We just need to do it a lot quicker.”

 The first problem of communication is getting people’s attention.

 When it comes to statistics, our best advice is to use them as input, not output. Use them to make up your mind on an issue. Don’t make up your mind and then go looking for the numbers to support yourself—that

 we use two basic models to make decisions. The first model involves calculating consequences. We weigh our alternatives, assessing the value of each one, and we choose the alternative that yields us the most value.

 One important implication of the gap theory is that we need to open gaps before we close them. Our tendency is to tell people the facts. First, though, they must realize that they need these facts. The trick to convincing people that they need our message, according to Loewenstein, is to first highlight some specific knowledge that they’re missing. We can pose a question or puzzle that confronts people with a gap in their knowledge. We can point out that someone else knows something they don’t. We can present them with situations that have unknown resolutions, such as elections, sports events, or mysteries. We can challenge them to predict an outcome (which creates two knowledge gaps—What will happen? and Was I right?).

 a Connection plot is all about. It’s a story about people who develop a relationship that bridges a gap—racial, class, ethnic, religious, demographic, or otherwise.

 To use scientific language, Wendy’s made a falsifiable claim.

 The problem is that when you hit listeners between the eyes they respond by fighting back. The way you deliver a message to them is a cue to how they should react. If you make an argument, you’re implicitly asking them to evaluate your argument—judge it, debate it, criticize it—and then argue back, at least in their minds. But with a story, Denning argues, you engage the audience—you are involving people with the idea, asking them to participate with you.

 The second model is quite different. It assumes that people make decisions based on identity. They ask themselves three questions: Who am I? What kind of situation is this? And what do people like me do in this kind of situation?

 Here’s the answer: The event-simulation group—the people who simulated how the events unfolded—did better on almost every dimension. Simulating past events is much more helpful than simulating future outcomes.

 When it comes to our hearts, one individual trumps the masses.

 Concreteness makes targets transparent. Even experts need transparency.

 How do we get people to believe our ideas? We’ve got to find a source of credibility to draw on.

 Floyd Lee, the manager of the Pegasus dining hall, has it right. He could have generated motivation through a strict self-interest appeal: perhaps by offering to let his employees off ten minutes early every night if they worked hard, or by giving them the first choice of the steaks. Instead, he helped create a kind of Pegasus identity: A Pegasus chef is in charge of morale, not food. You can imagine hundreds of decisions being made by staffers in the tent who think to themselves, What should a Pegasus person do in this situation?

## Managing Humans: Biting and Humorous Tales of a Software Engineering Manager 

A manager’s job is to transform his glaring deficiency into a strength by finding the best person to fill it and trusting him to do the job.

 A manager’s job is to take what skills they have, the ones that got them promoted, and figure out how to make them scale. They do this by building a team that accentuates their strengths and, more importantly, reinforces where they are weak.

## Measure What Matters: How Google, Bono, and the Gates Foundation Rock the World with OKRs 

In moderation, cascading makes an operation more coherent. But when all objectives are cascaded, the process can degrade into a mechanical, color-by-numbers exercise, with four adverse effects: A loss of agility. Even medium-size companies can have six or seven reporting levels. As everyone waits for the waterfall to trickle down from above, and meetings and reviews sprout like weeds, each goal cycle can take weeks or even months to administer. Tightly cascading organizations tend to resist fast and frequent goal setting. Implementation is so cumbersome that quarterly OKRs may prove impractical. A lack of flexibility. Since it takes so much effort to formulate cascaded goals, people are reluctant to revise them mid-cycle. Even minor updates can burden those downstream, who are scrambling to keep their goals aligned. Over time, the system grows onerous to maintain. Marginalized contributors. Rigidly cascaded systems tend to shut out input from frontline employees. In a top-down ecosystem, contributors will hesitate to share goal-related concerns or promising ideas. One-dimensional linkages. While cascading locks in vertical alignment, it’s less effective in connecting peers horizontally, across departmental lines.

 Everything seems important; everything seems urgent. But what really needs to get done?” The answer lies in focused, transparent OKRs. They knit each individual’s work to team efforts, departmental projects, and the overall mission. As a species, we crave connection. In the workplace, we’re naturally curious about what our leaders are doing and how our work weaves into theirs. OKRs are the vehicle of choice for vertical alignment.

 Unfortunately, alignment is rare. Studies suggest that only 7 percent of employees “fully understand their company’s business strategies and what’s expected of them in order to help achieve the common goals.” A lack of alignment, according to a poll of global CEOs, is the number-one obstacle between strategy and execution.

 We created quarterly OKRs and annual OKRs, and rolled them out to everybody at Nuna from day one. We were tiny then, around twenty people—not such a big lift, you might think. But the process didn’t take. Some people never set their individual OKRs; others set them, but stuck them in a drawer. With hindsight, I would have started with our leadership team of five. For structured goal setting to prosper, as our company learned the hard way, executives need to commit to the process. It may take a quarter or two to overcome your managers’ resistance and get them acclimated to OKRs—to view them not as a necessary evil, or some perfunctory exercise, but as a practical tool to fulfill your organization’s top priorities. Until your executives are fully on board, you can’t expect contributors to follow suit—especially when a company’s OKRs are aspirational.

 Above all, top-line objectives must be significant. OKRs are neither a catchall wish list nor the sum of a team’s mundane tasks. They’re a set of stringently curated goals that merit special attention and will move people forward in the here and now. They link to the larger purpose we’re expected to deliver around.

 The one thing an [OKR] system should provide par excellence is focus. This can only happen if we keep the number of objectives small. . . . Each time you make a commitment, you forfeit your chance to commit to something else. This, of course, is an inevitable, inescapable consequence of allocating any finite resource. People who plan have to have the guts, honesty, and discipline to drop projects as well as to initiate them, to shake their heads “no” as well as to smile “yes.” . . . We must realize—and act on the realization—that if we try to focus on everything, we focus on nothing.

 In most cases, the ideal number of quarterly OKRs will range between three and five. It may be tempting to usher more objectives inside the velvet rope, but it’s generally a mistake. Too many objectives can blur our focus on what counts, or distract us into chasing the next shiny thing.

 What are our main priorities for the coming period? Where should people concentrate their efforts?

 people walk out of meetings saying, “I’m going to conquer the world” . . . and three months later, nothing has happened. You get people whipped up with enthusiasm, but they don’t know what to do with it.

 Ideas are easy. Execution is everything.

 Andy Grove’s quantum leap was to apply manufacturing production principles to the “soft professions,” the administrative, professional, and managerial ranks. He sought to “create an environment that values and emphasizes output” and to avoid what Drucker termed the “activity trap”: “[S]tressing output is the key to increasing productivity, while looking to increase activity can result in just the opposite.”

 defined OKRs: “A management methodology that helps to ensure that the company focuses efforts on the same important issues throughout the organization.” An OBJECTIVE, I explained, is simply WHAT is to be achieved, no more and no less. By definition, objectives are significant, concrete, action oriented, and (ideally) inspirational. When properly designed and deployed, they’re a vaccine against fuzzy thinking—and fuzzy execution. KEY RESULTS benchmark and monitor HOW we get to the objective. Effective KRs are specific and time-bound, aggressive yet realistic. Most of all, they are measurable and verifiable.

 At smaller start-ups, where people absolutely need to be pulling in the same direction, OKRs are a survival tool. In the tech sector, in particular, young companies must grow quickly to get funding before their capital runs dry. Structured goals give backers a yardstick for success: We’re going to build this product, and we’ve proven the market by talking to twenty-five customers, and here’s how much they’re willing to pay. At medium-size, rapidly scaling organizations, OKRs are a shared language for execution. They clarify expectations: What do we need to get done (and fast), and who’s working on it? They keep employees aligned, vertically and horizontally. In larger enterprises, OKRs are neon-lit road signs. They demolish silos and cultivate connections among far-flung contributors. By enabling frontline autonomy, they give rise to fresh solutions. And they keep even the most successful organizations stretching for more.

 OKRs surface your primary goals. They channel efforts and coordination. They link diverse operations, lending purpose and unity to the entire organization.

 For leaders, OKRs give a lot of visibility into an organization. They also provide a productive way to push back.

 “hard goals” drive performance more effectively than easy goals. Second, specific hard goals “produce a higher level of output” than vaguely worded ones.

 “Google’s objective is to be the systematic innovator of scale. Innovator means new stuff. And scale means big, systematic ways of looking at things done in a way that’s reproducible.” Together, the triumvirate brought a decisive ingredient for OKR success: conviction and buy-in at the top.

 When people help choose a course of action, they are more likely to see it through.

 Grove wrestled with two riddles: How can we define and measure output by knowledge workers? And what can be done to increase it?

 Where an objective can be long-lived, rolled over for a year or longer, key results evolve as the work progresses. Once they are all completed, the objective is necessarily achieved. (And if it isn’t, the OKR was poorly designed in the first place.)

## Peopleware: Productive Projects and Teams 

We observe that about 15 percent of all projects studied came to naught: They were canceled or aborted or “postponed” or they delivered products that were never used. For bigger projects, the odds are even worse. Fully 25 percent of projects that lasted 25 work-years or more failed to complete.

 People often use the word politics to describe any aspect of the work that is people-related, but the English language provides a much more precise term for these effects: They constitute the project’s sociology. The truly political problems are a tiny and pathological subset.

 Twentieth-century psychological theory holds that man’s character is dominated by a small number of basic instincts: survival, self-esteem, reproduction, territory, and so forth.

 The builders’ view of quality, on the other hand, is very different. Since their self-esteem is strongly tied to the quality of the product, they tend to impose quality standards of their own. The minimum that will satisfy them is more or less the best quality they have achieved in the past.

 Speaking to a group of software managers, we introduced a strategy for what we think of as iterative design. The idea is that some designs are intrinsically defect-prone; they ought to be rejected, not repaired. Such dead ends should be expected in the design activity. The lost effort of the dead end is a small price to pay for a clean, fresh start.

 Fostering an atmosphere that doesn’t allow for error simply makes people defensive. They don’t try things that may turn out badly.

 Because we go about this work in teams and projects and other tightly knit working groups, we are mostly in the human communication business. Our successes stem from good human interactions by all participants in the effort, and our failures stem from poor human interactions.

 If you are charged with getting a task done, what proportion of your time ought to be dedicated to actually doing the task? Not 100 percent. There ought to be some provision for brainstorming, investigating new methods, figuring out how to avoid doing some of the subtasks, reading, training, and just goofing off.

 We all tend to tie our self-esteem strongly to the quality of the product we produce—not the quantity of product, but the quality.

 People under time pressure don’t work better—they just work faster.

 By noting the true nature of a problem as sociological rather than political, you make it more tractable.

 By regularly putting the development process under extreme time pressure and then accepting poor-quality products, the software user community has shown its true quality standard.

 We have to assume that the people who pay for our work are of sound enough mind to make a sensible trade-off between quality and cost. The point here is that the client’s perceived needs for quality in the product are often not as great as those of the builder.

 The manager’s function is not to make people work, but to make it possible for people to work.

 The major problems of our work are not so much technological as sociological in nature.

 Northcote Parkinson introduced the notion that work expands to fill the time allocated for it, now known as Parkinson’s Law.

 There may be many and varied causes of emotional reaction in one’s personal life, but in the workplace, the major arouser of emotions is threatened self-esteem.

 Gilb’s Law: Anything you need to quantify can be measured in some way that is superior to not measuring it at all. Gilb’s Law doesn’t promise you that measurement will be free or even cheap, and it may not be perfect—just better than nothing.

 The cause of failure most frequently cited by our survey participants was “politics.”

## Presenting Data Effectively: Communicating Your Findings for Maximum Impact 

Graphic elements are useful guides, leading the reader through the organization of a report or slideshow. By identifying and consistently using symbol sets or icons in our documents, we increase the structure of the information, making it easier and quicker for readers to interact with our work.

 the more hard-and-fast our existing schemas, the more new information struggles to find a home in long-term memory.

 We gain a visual theme when we use repetition. Repetition occurs when we take a few key graphic elements that support our message and sprinkle them (or variations on them) throughout the document group.

 You should probably pick a serif font for at least the body text of a written report where we expect an audience to engage in sustained reading.

 KEY POINTS TO REMEMBER High-quality graphics increase the impact of your data presentations. •   High-quality graphics have minimal clutter. In terms of photographs, stock photo sites are one solid option for finding controlled graphics. In terms of data displays, nonessential gridlines, axis labels, and tick marks can be removed. •   Whether free or for a fee, images should be procured at the right size so they are crisp when presented. Check pixel resolution, dpi, and size. •   Simplified graphics can be altered to draw attention to key areas through the use of selective emphasis techniques. •   A strong visual theme is built when graphic elements, such as portions of the same picture, or the same color, or the same shapes, are repeated throughout the data presentation

 focus on these three attributes: 1.   Two-dimensional 2.   Free of extraneous lines 3.   Familiar to viewers

 Black text has the highest comprehension levels when positioned on a white background, followed closely by dark gray text. We discuss other color options, but keep in mind that all of them come in a distant third place.

 Effective data presentation makes use of this early attention function.

 Usually color serves one of two purposes: 1.   Decorating 2.   Spotlighting

 The pictorial superiority effect is exactly what we can use to our advantage in effective data presentation. This effect is what allows us to move information along the memory continuum to catch the reader’s eye, focus the reader’s attention, and affix in the reader’s memory.

 effective data presentation assists this process because graphics are particularly good at activating those existing schemas.

 Effective data presentation, where we use graphic visualization to emphasize information, speeds the acquisition of that information and reduces the opportunity for misinterpretation

 For effective presentation, you need to succinctly name your key messages and identify visual images or metaphors that extend and elaborate on them.

 our working memory is prone to cognitive overload and getting past that hindrance is the tricky part of teaching and presentation.

 I represented the data by a bar chart instead of a pie chart because humans are much better at roughly assessing length than they are at perceiving area. Bar charts are easier to decode. I also ordered the bars from the greatest to the least to make that decoding process even more straightforward.

 We can enhance reader interpretability by turning down what Edward Tufte (2001, p. 105) called the “noise” in the graph. By “noise,” I refer to all of the parts of this graph that don’t actually display data or assist reader cognition.

 Type refers to the shapes of the individual letters and to the stylistic variations that contribute to legibility in different contexts.

 Effective data presentation creates a shortcut to audience comprehension.

 The visual impact of your research products increases if the images are large, well blended with the background, and positioned to support the text.

 People are most comfortable reading according to this reading gravity—left to right and top to bottom. Layouts that go against this reading gravity tend to make a reader feel subtly uncomfortable,

 A common mistake that impedes comprehension is when size changes in the graph do not actually correspond to meaningful changes in the data.

 The effective application of emphasis colors absolutely hinges on two things. First, identify the key message you are trying to communicate in your diagram, graph, or slide in order to emphasize that message with color. Second, once you set up a palette of colors, use those color choices consistently to create a predictable system for your readers that speeds up their ability to understand and remember your effective data presentations.

 two basic strategies: simplification and emphasis.

 Even if the study authors had an opinion, it was left up to the viewer to interpret the data and decide what was important. The problem with presenting data in that manner is that it assumes that the average viewer takes the time to engage with the data and to pull out the most pertinent elements. That is quite a large assumption.

 Paying attention to format, color, and font choices assists readers in encoding our information and grappling with it; this is how comprehension occurs. The more engagement, the more that passes through the working memory checkpoint, the more information that stays in long-term memory.

 Effective data presentation uses design principles built around graphics, typeface, color, and arrangement to support engagement with our research products.

 Regardless of the field, position, or geographic location, we are all in the business of presentation. The way we package our words and our data is reflected in our audience’s perceptions of our quality, credibility, and trustworthiness.

 The research in this area repeatedly shows that when the viewer (young or old) is unfamiliar with the type of display, she spends cognitive energy just trying to understand the display rather than decode the data it is trying to communicate

 When we develop a visual theme, we build a system of organization throughout our presentation avenues.

 A change in font indicates a change in meaning and invites the audience to spend energy to interpret the meaning.

 using the image for the introduction and conclusion helped create a brand for me and this particular project.

 The emotional response summoned by imagery is weakened when hackneyed pictures are used.

 Choices in font category, size, and spacing affect legibility and influence the mood or environment of the reporting, as well as reflect the competence of the researcher. A hierarchy of importance, established by controlling and manipulating the font, communicates to the reader the desired focus and order for attention.

 Communication with our stakeholders is clearer and more effective when we highlight the graph’s key points. The viewer can always disagree and the remainder of the data is there with which to do so; nothing is hidden. This format just respects the time and energy of the audience and relays the data directly. In the effective example, the key message is both stated in the title and made obvious by changing the bar colors such that the less important points are a light gray and the point that illustrates my message pops out the most.

 Guiding Ideas Pictures/graphics are present Graphics direct toward text Visual theme is evident Size corresponds to changes in meaning Graphics are simple

 By expanding the image to fill the screen (bleeding it), I am tapping into the Gestalt theory of closure (see Graham, 2008 for an overview of Gestalt principles in media design). This principle says that our eyes naturally continue the picture off the edges of the screen and into the real world—a good thing when we are trying to make connections from our findings to our audience’s circumstances.

 Graphic design elements and techniques draw attention, help a viewer digest information, and boost the recall of that information later

 but the problem is that working memory is like a sieve. It is weak, can’t wrestle for long, and can’t wrestle with much. Research shows we only hold 3–5 chunks of information in working memory at any one time, and that number even varies by the environmental context

 we live in a “high concept” society; we have about 3 seconds to capture attention, which is hardly enough time to read text. So use an image to help.

 Information uptake occurs in three phases: early attention, working memory, and long-term memory.

 In fact, we are so awesome at using our eyes to take in information, our brains do not even have to be cognitively engaged for the process to work. When something just catches our eye, it is tapping into our earliest stages of attention, an activity that is so subtle that some researchers call this stage pre-attention

 Serif is a Latin word that means “little feet.” See the little feet at the bottom of the letters? Those feet help create an almost continual line along the bottom of a length of text, smoothing the reading process. Serif typefaces make reading our work more fluid

 Pairing an image with a few keywords on a slideshow, or with a few summary sentences in a report or research poster, serves to create a chunk of information mentally processed as one unit. Presenting the combined image-idea pair together replaces lengthy narrative, speeds up the pace at which people engage with our work, and generates more interest in the work.

 When moving between fonts, make them very different. If the sans serif heading looks too similar to the serif body type, it just comes off as a sloppy mistake. Be a little bold with the headings. Contrast with body text by using a different font category, size, style, and/or color.

 Bar charts work best when comparing categories. Line charts are most appropriate for looking at change over time. Scatterplots most effectively represent correlations and linear relationships.

 Default bullets are dark. The black dots contrast with the white background more than the text on the slide, and thus they pop out to the reader. The bullets are surrounded by white space, contributing to their emphasis as focal points. Our eyes are drawn to the bullets. That is a lot of power, except we tend to use them on anything that could be a list instead of reserving them for what really needs the reader’s attention.

 Generally speaking, humans are good at judging length and bad at judging area—which means bar and line charts are often good options.

 As students we are taught to summarize the main points when we read. Rather than obfuscate that attempt in our own readers, we can use graphics to help us cut to the chase.

 Selective use of color is one way the designer (you) can “prechunk” your information, easing some of the thinking and cogitating a reader normally has to do, thus increasing both their capacity of thinking and the amount of time an audience spends thinking about your data.

 Subheadings are set in the same font as the document’s headings. In keeping with a hierarchical organization, the subheadings should just be downplayed a bit: smaller in size than the headings, or a more neutral color, or italicized.

 The use of color for emphasis impedes comprehension if too many colors are used indiscriminately; readers expect that a change in color indicates a change in meaning and they spend valuable time and effort trying to understand the meaning shift

 Headings are a clue to the report’s organization. They can be distinguished from body text by their placement above the narrative and they can be further distinguished through the use of a font change.

 Some people think that there is no better way to express parts of a whole. Other people assert that pie charts are fairly useless because humans are pretty terrible at judging area.

 they lose their distinction when printed in black and white

 Moving from weak to effective data presentation involves stripping out nonessential information and then adding back in selective emphasis to bring attention to our meaning.

 However, in order to be able to recall information, it must be stored in the brain’s long-term memory, which is Stage 3. The path that moves information from Stage 1, early attention, to Stage 3, long-term memory, can be a bit tricky, but graphic design helps it get there.

 Working memory is what we use when something has caught our eye and we decide to bring it into mental focus, to contemplate it, and to engage our cognitive energy.

 techniques like color, alignment, motion, orientation, and size grab a viewer’s early attention. Visual cognition research reveals that capitalizing on the pictorial superiority effect boosts the audience’s ability to recall information.

 When we add visuals to verbal explanations, readers generate 65% more creative transfer and applications of knowledge (Mayer, 1997). That is why so many of us are better at remembering faces than names, and at navigating using landmarks rather than street names. We are visual beings.

 applying colors for decoration adds a balance and professionalism to reports that contribute to perceptions of credibility and quality.

 Greenpeace used almost full-page pictures to identify the start of a new report section. Tiny corner images were used to mark that section’s interior pages. The size of the image marks meaningful changes to the reader. Such organization speeds up the pace at which readers can navigate with our materials and more readily reveals the author’s mental structure for the report.

 Color changes denote meaning changes

 The brain actually does a better job of retaining visual information when it is also paired with verbal information. In fact, a good pairing of these two elements increases retention to 75%

 In order for new information to be encoded in the brain, it must be incorporated into existing schemas.

 avoid using color as the only distinguishing factor between the icons in your set.

 As you will learn in the chapter on color, the optimal condition for reading is when black or very dark text is placed on a white background.

 call these Judgmental Icons (clearly distinct from Emoticons) because they quickly communicate our interpretation of our research findings.

 Psychologists debate the exact details, but we know that the eye-brain connection does not work by reading through each individual letter (Pelli, Farell, & Moore, 2003). Rather, curves of letters and the composure of ascenders (think of the tall sticks on an h) and descenders (think of the stick that hangs down on a y) influence recognition of an entire word.

 For lines within a paragraph, generally choose line spacing that is 1 to 2 points larger than the body text.

 Shifts in the narrative also occur with the introduction of sidebars. Sidebars are a way to showcase a short poignant story or to describe a detail that is related but not a direct part of the narrative.

 working memory can only hold roughly four chunks of information at one time,

 Narrative text is dark gray or black Background has white or subdued color

 research on color contrast says that color text on a color background hinders reading

 If you must use bullets, decrease their size to slightly less (70–80%) than the narrative font point size.

 Research has repeatedly shown that simpler visualizations are interpreted more efficiently and lead to better recall (Tractinsky, 1997).

 Everyday objects also have a naturally implied directionality that we can use to guide attention. In turn, that direction dictates the placement of the words.

 There are five ways to use images for effective impact. Images should be: 1.   present (seems obvious, but it isn’t) 2.   emotional 3.   placed for high impact 4.   quick at communicating 5.   repeated

 A good, strong noindentation can cue a reader to a subset of information, possibly as well if not better than the dark circles.

 An effective data presentation may look pretty, but the true goal is to support audience cognition.

 It is perfectly okay to use color, just be certain to also use some other method of differentiation, such as shape.

 any flipping back and forth between pages to try to cohere the two blocks of information impairs readers’ ability to comprehend; we lose them when they have to flip. It is better to isolate one idea per page or at least to start the idea on the page where the graph is located.

 If the presentation piece at hand is intended for study and requires extensive reading of narrative prose, the color combinations should be fairly bland and nondescript. If parts of the data presentation—like a callout box of text or a key data point—need to leap out at a reader, a more colorful scheme is warranted.

 KEY POINTS TO REMEMBER

 Reference icon sets provide the reader with a mental organizational structure,

 we primarily get our information about the world through our eyes. Certainly, we have other sensory organs that feed information to our brains. But the reality is that vision dominates. Today’s researchers refer to this as the pictorial superiority effect,

 Although working memory has limits on its cognitive load, graphic elements can reduce the overload by doing some of the thinking for the reader. By visually organizing and emphasizing information, graphic design makes it more accessible for the reader, increasing the capacity to engage with the words and data.

 Do not use clip art; actual photography of real images communicates credibility and legitimacy to the viewer (Samara, 2007),

 our goal in visualizing data should be to support the audience’s attention to make meaning from our work.

 reading off the bullet points one by one. The problem with slides of this type again comes back to how our brains receive and react to data. Rates vary, but normal reading speed is two to three times faster than normal speaking speed. In other words, the audience can finish reading the entire list while I am still explaining Bullet 2, but their comprehension is impaired because their brains are trying to do too many things at once.

 “Lack of information does not appear to be the main problem. Rather the problem seems to be that the available information is not organized and communicated effectively.” They went on to say “Information did not reach the right people, or it did, but it was in a form that was difficult to digest”

 Whatever method you are using to talk about your research, people tend to only read in-depth if something has caught their eye.

## Principles: Life and Work 

1. Put our honest thoughts out on the table, 2. Have thoughtful disagreements in which people are willing to shift their opinions as they learn, and 3. Have agreed-upon ways of deciding (e.g., voting, having clear authorities) if disagreements remain so that we can move beyond them without resentments. I believe that for any organization or for any relationship to be great, these things are required. I also believe that for a group decision-making system to be effective, the people using it have to believe that it’s fair.

 Everyone agreed that most of those areas couldn’t adequately be delegated. I clearly hadn’t done a good enough job of finding and training others to whom I could delegate my responsibilities.

 Whether you own a hotel, run a technology company, or do anything else, your business produces a return stream. Having a few good uncorrelated return streams is better than having just one, and knowing how to combine return streams is even more effective than being able to choose good ones

 They recounted how we uniquely and repeatedly tried new things, failed, learned from our failures, improved, and tried again, doing that over and over in an upward spiral.

 an idea meritocracy—not an autocracy in which I lead and others follow, and not a democracy in which everyone’s vote is equal—but a meritocracy that encourages thoughtful disagreements and explores and weighs people’s opinions in proportion to their merits.

 I insisted that an issue log be adopted throughout Bridgewater. My rule was simple: If something went badly, you had to put it in the log, characterize its severity, and make clear who was responsible for it. If a mistake happened and you logged it, you were okay. If you didn’t log it, you would be in deep trouble.

 My painful mistakes shifted me from having a perspective of “I know I’m right” to having one of “How do I know I’m right?” They gave me the humility I needed to balance my audacity.

 Making a handful of good uncorrelated bets that are balanced and leveraged well is the surest way of having a lot of upside without being exposed to unacceptable downside.

 Having a process that ensures problems are brought to the surface, and their root causes diagnosed, assures that continual improvements occur.

 learned that if you work hard and creatively, you can have just about anything you want, but not everything you want. Maturity is the ability to reject good alternatives in order to pursue even better ones.

 A shaper is someone who comes up with unique and valuable visions and builds them out beautifully, typically over the doubts and opposition of others.

 what was most important wasn’t knowing the future—it was knowing how to react appropriately to the information available at each point in time.

 amount. In trading you have to be defensive and aggressive at the same time. If you are not aggressive, you are not going to make money, and if you are not defensive, you are not going to keep money.

 No matter how much effort we put into screening new hires and training them to work in our idea meritocracy, it was inevitable that many of them would fall short. My approach was to hire, train, test, and then fire or promote quickly, so that we could rapidly identify the excellent hires and get rid of the ordinary ones, repeating the process again and again until the percentage of those who were truly great was high enough to meet our needs.

 I learned subsequently how important tools are in helping to reinforce desired behaviors,

 Finding out what’s true and trying to do what’s in everyone’s best interests is rare, though most policymakers pretend that’s what they’re doing.

 To me, the greatest success you can have as the person in charge is to orchestrate others to do things well without you. A step below that is doing things well yourself,

 Seek out the smartest people who disagreed with me so I could try to understand their reasoning. 2. Know when not to have an opinion. 3. Develop, test, and systemize timeless and universal principles. 4. Balance risks in ways that keep the big upside while reducing the downside.

 I urge you to be curious enough to want to understand how the people who see things differently from you came to see them that way. You will find that interesting and invaluable, and the richer perspective you gain will help you decide what you should do.

## Product Management in Practice: A Real-World Guide to the Key Connective Role of the 21st Century 

If you are using a formal practice for writing product and feature specifications such as “user stories,” remember that a formally correct spec is not necessarily a good spec.

 Adopting Agile practices meant that those initial conversations with clients had to change pretty dramatically. Rather than haggling over how many features we could build within a client’s budget, we explained to them that we would start down a certain path, track our velocity, show them the work every two weeks, and allow them to work with us on changing, adding, or subtracting features as the product took shape. We got a lot of responses like, “Yeah, but how much does it cost and when will I get it?” At first, we struggled to answer those questions. But now that we’ve been working in Agile for a number of years, we have a much clearer sense of what can be accomplished in a given time box and we can provide some fence posts along the way. With Agile, you constantly refine and explore the delta between your estimated velocity and the reality of your work, which is actually much more powerful than trying to predict it all at the beginning

 Give your colleagues the opportunity to suggest ideas for the product roadmap, but don’t let it turn into a free-for-all. Use simple templates to structure your colleagues’ thinking around the goals of their ideas, not (just) the ideas themselves.

 four actions at the “Heart of Agile”: Collaborate Deliver Reflect Improve

 Agile is not a matter of working more or of working faster, but rather of working differently. In fact, following the core values of Agile often means slowing down, at least momentarily, to reflect on how we currently work and how we could work better.

 Make sure that everything on your roadmap is tied back to a “why” so that if that “why” changes, you can adjust the roadmap accordingly.

 Don’t spend so long on product specifications that you close off avenues for true collaboration.

 Do everything in your power to make sure that the goals against which you are prioritizing are clear, well understood and actionable. If you can, take your goals for a “test drive” with the senior leaders who are setting the company vision and strategy. See if the goals can serve as a stand-in for their vision, and change your goals if they aren’t giving you the guidance you need.

 Working in Agile our team feels more like your team. As the project goes on, it becomes clearer and clearer that our interests are truly aligned. With Agile, our profit is maximized by you being successful and continuing to develop the product, whereas the end of a Waterfall project is us trying to maintain our profitability by limiting the number of things you can squeeze in, and limiting the warranty. Though waterfall projects may provide your clients with a seductive sense of certainty at the beginning of a project, they set you down an inherently adversarial path. Working in Agile, we’ve been able to collaborate much more closely with our clients and deliver better products.

 When changing specific practices within an organization, I’ve found it very helpful to document the change being made, the goal of that change, and how we will know when it is succeeding. In Chapter 4, I provided a simple and straightforward template that can be used to bring a goals-first approach to organizational practices. You can easily customize that template for working within Agile practices and methodologies: We used this Agile practice in our last iteration of work: We implemented it because we thought it would have this effect toward achieving our North Star goals: The actual effect of this Agile practice was: So, for the next iteration of work, we are changing it in this way: We hope that making this change will have the following effect toward helping us achieve our North Star goals: We will know that this change is succeeding when:

 If you are taking time to truly reflect and improve, then wherever you start, you will wind up somewhere better.

 open the roadmap to a shared, company-wide discussion about what you are building, who you are building it for, and why. As a rule, the product roadmap should be something that encourages collaboration and focuses that collaboration around high-level goals.

 Committing at the outset to what you are going to measure and why helps you to avoid what Lean Startup author Eric Ries describes as “vanity metrics.” In short, these are whatever metrics make it look like you’re doing a good job, even if they are not tied to your underlying goals.

 We knew that we needed to validate the algorithm — the core set of rules we were working on — with the client before we actually built it. So, we put a bunch of rules down on index cards, and told them, “We’re going to play a game with you, and see if the rules of the game lead to the outcomes that you think are right.” For example, one rule might be: “Once you’ve successfully completed three sessions of one-legged squats, then you progress to one-legged squats with weights.” And as we walk through a particular scenario, the client might say, “Oh no, no, no, there’s no way this person would be ready for that yet.” So, we ask, “Okay, what should happen instead?” And then we update the rules and try it again.

 rather than attaching your value as a product manager to a number that might be outside of your control, ask for accountability in a way that makes you wholly responsible for seeking out and acting on the things you can control.

 The bottom line with prioritization is this: prioritization will be as easy or as difficult as your goals are clear, well understood, and actionable.

 In Agile parlance, a finite amount of time devoted to learning, researching, and/or experimenting (as opposed to building or coding) is often called a “spike.”

 Prioritization is where organizational goals and vision turn into actual decisions about timing and resource allocation. As such, it provides us with a critical opportunity to see how well our organizational goals and vision are actually serving our day-to-day work.

 If you are being held accountable for a specific number, but the fate of that number is ultimately outside of your control, how do you stay focused on the actions you should be taking to move that number in the right direction?

 But we were able to build a really great product for this client by walking them through real scenarios that they could imagine, and not asking them to think about things in technical terms that they didn’t understand.

 When I feel like I’m struggling to identify the assumptions at play in my work, I like to begin with the question, “what other things would need to be true in order for my interpretation to be correct?”

 think of roadmaps as a strategic communication document, not as an actual plan for what will be executed and when.

 Flip the script and ask senior leaders about users If you’re looking to encourage user centricity throughout the organization, ask your senior leaders what they know about the needs of your users. Make it clear that your goal is to help them deliver value to users and meet the goals of your business. Invite them into a conversation in which you are collaboratively exploring multiple solutions to a well-understood user need, rather than debating a single, predetermined solution.

 If you find yourself confronted with an OQP, I would suggest using the following template to assess how you might put it to use: What is this OQP attempting to represent? What raw information went into generating this OQP? How was that raw information turned into this OQP? What questions can this OQP alone not answer? How might we answer those questions? Based on the above, how might we use this OQP to meet our specific goals and needs?

 One approach I’ve found very useful is to treat product specs like conversation starters, rather than hard-and-fast plans. If a question comes up about how we will build something, I include that question in the spec itself, rather than providing the answer that I think is best.

 Although the idea of actually committing to a single success metric might seem implausible, it is incredibly valuable as a thought exercise. Do you know what the single most important metric for your product is right now? Can you clearly state why it is the most important metric? Are your company’s overall strategy and vision making it easier or more difficult for you to know what metric you should be looking at and why?

 As a product manager, it is your responsibility to make sure that technical conversations are opened up and made accessible, so that people with different types of expertise can collaborate on deciding how to address a given user need. This is true not only of working with data systems, but of working with any kind of technical system you encounter as a product manager.

 Connect user needs and business goals It is not uncommon for product managers to find themselves feeling like they are advocating for “what’s good for the user” against executive mandates to build “what’s good for the business.” But the biggest problem in this scenario is not an imbalance between user needs and business goals, but that these two things are perceived as being at odds with each other in the first place. If you feel like you are caught in a tug-of-war between business goals and user needs, the solution is not to pull harder, but to make sure that a clear and positively correlated relationship has been established between the needs of the user and the goals of the business.

 Here are some signs that you might have an OQP on your hands: OQPs purport to capture complex and widely variable trends or behaviors in a single number or score. OQPs generally disguise or omit the raw data from which they are generated, and the manner in which that data was collected. OQPs are presented as being equally applicable to all organizations regardless of those organizations’ specific goals and needs.

 Putting some time into a product spec can be critical for making sure that you understand what you’re building and why you’re building it. But putting too much time into a product spec can create a false sense of certainty that actually makes it harder for your team to successfully collaborate.

 Recognize that a data-driven approach still means that you will have to set priorities and make decisions. Avoid using the word data to generalize specific information. Say what that information is and how it was gathered. Rather than hiding or erasing the assumptions that go into working with data, document those assumptions so that you and your team can address them together. Have a clear and strong point of view about what metrics matter and why. As a thought exercise, ask yourself to decide on the “One Metric That Matters.” If you’re having trouble focusing in, go back to your high-level goals and see if you can make them more specific and actionable. Think through how you will measure a product’s success before you launch it, to avoid having to go back and add instrumentation after a product is already released. Be just as curious and active about understanding metrics moving “the right way” as you are about metrics moving “the wrong way.” Rather than being accountable for a number hitting a target, seek to be accountable for knowing why that number is moving toward or away from that target and having a plan for addressing whatever underlying issues are within your control. Resist the siren call of scores and numbers that purport to tell you “everything that you need to know” about anything. Take the time to understand how these quantitative proxies are developed, and do the work of figuring out what specific questions they can and cannot answer based on your goals and priorities. No matter how complex the data systems you’re working with, resist the pull of jargon. Keep conversations about technical decisions rooted in high-level goals that can be understood by everyone in the organization to make as much room as possible for collaboration.

 Rather than being accountable for hitting a specific metric, product managers can seek to be held accountable for the following things: Knowing which metrics matter and why Having clear targets for these metrics Knowing what is going on with these metrics right now Identifying the underlying issues that are causing these metrics to do what they are doing Determining which underlying issues can be effectively addressed by you and your team Having an action plan for addressing these issues

 Let your users make the case for you When you find yourself trying to argue for specific ideas and approaches, remember that you are ultimately building a product not for your stakeholders, but rather for your users. If you are doing the work of regularly talking with and getting feedback from your users — which you absolutely should be — you should have plenty of information at your disposal to bring your users’ needs to life as you present to senior stakeholders. If you find that you don’t have a clear sense of why your users might need the thing you are proposing to build, you probably shouldn’t be advocating for it in the first place.

 I have taken to calling these numbers and scores Obfuscating Quantitative Proxies (or OQPs) — which is to say, single-dimensional numerical answers for broader qualitative questions that obscure the complexity of the underlying issue.

 Product specifications (usually referred to as “product specs”), like roadmaps, are strategic documents that help guide and facilitate the creation of your product. But they are not your product. Working on an extensive, beautiful, comprehensive product spec can feel like a productive and valuable way to contribute to a product’s development — something you can actually do on your own time with your own hands, rather than just “facilitating” or “supporting.” But your users see no benefit from that spec — they are using the product you have actually released.

 The technical jargon around data science can be particularly intimidating, precisely because it is placed at such a high value. And for this very reason, it is even more important for you to create a strong connection between the technical concepts deployed by data scientists and the plainspoken goals of your product and organization.

 People don’t know where to give you feedback when you present everything all at once in a big meeting that way. If you go to people individually, they might say, “This is terrible — and here’s how to fix it.” But when you try to do “the big reveal,” there’s really no way forward.

 Don’t try to play both sides! This will simply not work. There are likely opportunities to level up to a more goals-oriented conversation, and it is your job as a product manager to facilitate that conversation. Best-case scenario, you will discover a solution that takes less than two weeks and incurs minimal concerns about performance and stability. Keep the conversation open and exploratory, but don’t try to score quick points by telling people what they want to hear.

 If you need something, ask for it, and be absolutely clear about why you’re asking for it.

 Make sure that business goals and user needs are not seen as at odds with each other, but are instead aligned with each other, both for specific product initiatives and within the organization’s overall vision and strategy.

 If you need feedback from somebody whose first reaction always seems to be “yes,” ask for that feedback in a way that does not allow for a yes/no answer. Accept that person’s implicit challenge to be both more precise and more open in the way that you ask for feedback, and it will likely help you gather better feedback from everybody in your organization.

 people will be able to more candidly and directly walk you through their own experiences when relaying a specific instance, as opposed to trying to synthesize a general statement about their tastes and preferences.

 When talking to your stakeholders, you want them to walk away feeling deeply invested in whatever it is you’re building. You want clear and affirmative commitment. You want to connect high-level goals with specific executional details. You want to build alignment and camaraderie.

 The second you go to your team and say something like “our boss is an idiot,” you have effectively ruined your team. They will begin to see any and all requests that come down from senior stakeholders as arbitrary and unreasonable. The time and energy they spend working on projects that align with organizational goals will feel like grudging concessions to the powers that be. And the time and energy they spend working on projects that do not align with organizational goals will feel like “sticking it to the man.” They will see your role as protecting them from senior stakeholders, rather than connecting them

 Push upward for clarity around company strategy and vision, no matter how challenging it is. In the absence of this clarity, you cannot succeed.

 Never surprise a senior stakeholder with a big idea in an important meeting. Socialize ideas slowly and deliberately in one-on-one meetings.

 your users are not aware of all the organizational intricacies, all the internal trade-offs, and all the specific downstream concerns that go into building a product. In many cases, they are not even aware of their own needs because they are so accustomed to addressing those needs with the tools that they already have.

 No! If an executive has taken the time to come to you and share their excitement about a specific feature, there is almost certainly an important reason. Even if you ultimately plan to stand firm on your team’s original priorities, take the opportunity to understand why this executive is so excited about this feature.

 Another challenge posed by distributed teams is that decisions made during informal in-person or one-on-one conversations might not find their way to your remote colleagues quickly or easily. Lucky for you, this is also a problem faced by fully colocated teams, where an idea hashed out over a coffee break can have serious ramifications for people outside of the immediate conversation. Working with a distributed team is a great opportunity for you to become more disciplined and rigorous about where and how you document your team’s work.

 a product manager cannot succeed if there is not clarity among senior leaders about a company’s strategy and vision.

 When you hear about teams performing well, trust is a huge part of that. And trust often develops through conversations outside of formal, scheduled meetings.

 when there’s a fundamental mismatch between what the business wants and what your team wants, you can’t resolve it by ignoring the business in the name of “protecting” your team.

 nothing that you are telling a senior stakeholder in a “big” meeting should ever be a surprise, ever. There are many reasons why it is always a good idea to individually walk senior stakeholders through a new idea before you present it in a group setting.

 As a product manager, you’re always being asked, “Why does this take so long?” You have to be able to unpack that question without getting defensive about it. Help senior leaders understand that the decisions they make aren’t made in isolation — help them see the “invisible” work that they don’t think about when they decide that they want a new feature. Give them options and make them aware of the trade-offs of each approach. Always make sure that the decision is in their hands, that they have ownership. That way it’s not an us-versus-them situation — it’s just us.

 Let your users lead you to what they think is important, rather than making that assumption for them with lots of detailed “zooming in” questions.

 think through the following prompt before asking a specific question (see Figure 7-2): is my intent with this question to zoom in on specific details, or to level up to overall goals and experiences?

 The word why has a particular way of putting people on the defensive. And when people are on the defensive, they are generally not inclined to share very much with you about their needs, behaviors, and rituals.

 Shake up the work that people are doing and cross-pollinate knowledge and skills to keep your team curious and actively learning.

 things that seem obvious are those that carry the most potential for disastrous miscommunication. This is in no small part because the things that seem obvious are often the ones nobody wants to address explicitly.

 Part of the challenge at a big company is that the higher-ups usually aren’t the people who understand what’s really going on. They get reports from people who do the work. But I realized that in order for me to be successful, I needed to have core partnerships with folks within editorial, design, engineering — these very established orgs within the bigger organization. They have the organizational knowledge and history that I just don’t. If you have a meeting with marketing, you need someone who can tell you, “Here’s what’s actually happening.” You need to make sure that the human connection is there, and active.

 Building that kind of trust involves using a lot of classic product manager tricks: having coffee with people, getting drinks with them, getting to know their work and their problems. Starting from a place of openness: “I’m new; I don’t know anything. Tell me your problems and we’ll figure something out.” Nothing transactional, no quid-pro-quo, no “you’ll scratch my back….” No expectations. People appreciate that kind of candor.

 Discomfort is often the manifestation of a lack of clarity. It is a valuable signpost that people might not be on the same page, or that expectations have not been clearly set.

 Instead of breaking the rules for “special cases,” reflect on why the rules cannot accommodate these cases. How might you collaboratively change those rules to better account for new situations and changing circumstances?

 Build bridges before you need something

 The guiding principle for research is, “live in your user’s reality.” Every product has a user — whether it’s a consumer, another business, or an engineer utilizing an API.

 In theory, consensus means: Everybody agrees! In practice, consensus means: Lots of people disagreed but didn’t say anything. The decision being made was so important that nobody wanted to speak up and be held accountable for it. Everybody grew tired and just wanted the meeting to be over, so they agreed to...whatever it was the meeting was about. (What was that meeting about, again?)

 commitment means that everybody in the room is explicitly taking responsibility for any decision that is made in the meeting. Prompting people to affirmatively commit to a path forward rather than letting them slink out of the meeting with no sense of accountability naturally encourages people to share dissenting and complicating information. After all, nobody wants to be held accountable for a plan that they know is going to fail.

 When something goes wrong, organization-minded product managers don’t just ask “how can I solve this problem right now?” but also “how can I make sure this doesn’t happen again?” The guiding principle for organization is “change the rules, don’t break the rules.”

 In her pioneering work on learning and success, Stanford psychology professor and author Carol Dweck posits that people operate in either a “growth” or a “fixed” mindset. When operating in a growth mindset, people see failures and setbacks as learning opportunities. When operating in a fixed mindset, people see failures and setbacks as negative reflections of their intrinsic worth.

 product managers who excel at organization see the question “what should we be working on right now?” as a sign that something is broken.

 You are in the middle

 Set clear goals, test, and learn So, what if people simply won’t commit to a path forward? This is, believe it or not, a great sign. It means that the people in the room are engaged enough that they will not commit to something that they think is wrong. One way to move this conversation forward is to establish success criteria and plan to revisit the decision at a later time, so that you can validate whether the approach you choose is working and make adjustments accordingly. For example, suppose that you are in a meeting with your engineering team, and there is a disagreement about whether your product development cycle should be two weeks or six weeks. Rather than trying to get everybody to reach consensus — which might never happen — you could say, “What if we commit to trying two-week development cycles, and touching base in a month to see whether this decision is helping us meet our team goals or whether we want to try something else?” This ensures that a decision happens, and creates a shared sense of accountability for measuring its success and adjusting course if needed.

 Product managers who lack organization skills are happy to hear questions like “what should we be working on right now?” because these questions put the product manager in the utterly indispensable role of guiding the team’s day-to-day priorities and decisions.

 as a product manager, you also sit in the middle of the people who hold these needs, perspectives, and skill sets. You must understand their communication styles, their sensitivities, and the differences between what they say and what they mean.

 Large companies have a veneer of formality that startups usually don’t, but that doesn’t mean that things are linear or predictable. Startups are often much more candid about their challenges: “This is messed up; let’s fix it.” At a large company, it can take months to get people to open up and speak candidly

 Interpret silence as disagreement

 Far too many meetings adjourn without critical conversations taking place because nobody wants to publicly offer a dissenting opinion. Thankfully, the good folks at Intel pioneered a technique called “disagree and commit” that is designed to solve for this very set of problems. The idea behind disagree and commit is simple: the goal of a meeting should not be to get consensus, but rather to get commitment.

 Best practices often focus on operational stories, not stories of user value Most stories about product management best practices end with happy and efficient product managers, designers, and developers, but not (necessarily) with happy users. This focus on the operational success of product management best practices can inadvertently shift goalposts within organizations from “Are we successfully delivering value to our users?” to “Are we successfully doing product management the same way that another company does?”

 With disagree and commit, nothing short of affirmative commitment is accepted, which means that silence amounts to disagreement. Be very clear with participants: “If you are silent, I am going to assume that you are disagreeing with me. Let’s go through and have each person share your insights and concerns.”

 It’s not about changing everything all at once, and it’s not about forcing a team to work in a certain framework or adopt a certain set of rituals. It’s about really just iterating on your process constantly. When it doesn’t work, you figure out why it doesn’t work, and you try something else.

 there are a few consistent themes that unite the work of product management across job titles, industries, business models, and company sizes: You have lots of responsibility but little authority

 Communication is your job, and you can’t expect everyone else to be good at it. My two favorite questions are: “What are your goals?” and “What are you optimizing for?”

 “I’m curious to learn more about the work that you do” is the most powerful sentence at your disposal as a product manager,

 You must lead through influence, not authority, which requires developing an entirely different set of skills and approaches.

 Templates codify organizational goals and values into an impartial set of prompts and questions, and have immense power to depersonalize emotionally charged disagreements. When used consistently and transparently, templates become an immensely useful organizational mediator.

 Pursue clarity over comfort to build your communication skills.

 Seek out opportunities to solve organizational problems on the systemic level rather than the individual level. If the rules aren’t working, change them, don’t break them.

 If curiosity is the key mindset of the product manager, research is how that curiosity is actualized and extended beyond the walls of the organization.

 For being wrong to be a gift, you need to know exactly why you’re wrong — and choose to prioritize the overall goals you are working toward above your specific plan for achieving those goals.

 When talking with users, your job is not to convince, or to impress, or to align. Your job is simply to learn as much as you can about their needs, their world, and their perspective. If you are to follow the guiding principle “live in your user’s reality,” you must understand your user’s reality in bright and vivid detail. In many cases, this means that your best approach is not to sound smart, but rather to “play dumb” and create as much space as possible for your users to communicate with you in their own words and on their own terms.

 When product managers fail to push upward for clarity, they tend to retreat into building cohesion within their own team at the expense of their team’s connection with the organization as a whole.

 When senior stakeholders ask you questions like, “Can this be done by Tuesday?” take their questions at face value. Let them participate in making tactical trade-offs, rather than rushing to make yourself the Product Martyr.

 Don’t let company politics drown out the needs of your user. Let user needs guide your decision-making, and bring the user’s perspective to life in meetings with senior leaders.

 When confronted with a swoop-and-poop, don’t try to litigate the details of past conversations. Look for opportunities to diagnose and address the underlying issues so that that the swooper/pooper does not feel out of the loop moving forward.

 Patterns and traps to avoid Yes! Immediately agreeing to a request like this not only undermines the existing processes your team uses to prioritize work, it also sets up the executive making this request for disappointment. Unless you have taken the time to fully understand why this feature is being requested, you are in no position to promise anything.

 Maybe. We’ll see how much time we have. The fundamental question here is not whether your team will have time to work on the new feature, but rather why this executive is so excited about the new feature in the first place. If you make this merely a matter of capacity, you are missing out on a critical opportunity to better understand the goals and motivations of a senior stakeholder

 If a question you are planning to ask is designed to “level up” the conversation, you are effectively asking a “why” question — even if that question begins with “tell me about the last time…” or “what was it like to…” or “how was the experience when you….” Having a clear framework for thinking about whether you are directionally moving the conversation upstream and out or downstream and in gives you a way to ask why without reflexively turning to that exact word in a way that might make your users feel defensive.

 If it needs to get done, it’s part of your job

## Radical Candor: Be a Kick-Ass Boss Without Losing Your Humanity 

The source of everything respectable in man either as an intellectual or as a moral being [is] that his errors are corrigible. He is capable of rectifying his mistakes, by discussion and experience. Not by experience alone. There must be discussion, to show how experience is to be interpreted.

 Very few people focus first on the central difficulty of management that Ryan hit on: establishing a trusting relationship with each person who reports directly to you.

 three areas of responsibility that managers do have: guidance, team-building, and results.

 for criticism to be effective, it’s crucial “to do it very clearly and to articulate why … and to get them back on track.” [My italics.] In other words, “your work is shit,” even stated less aggressively, is not enough. The boss needs to explain why; that is, be invested in helping the person improve.

 Challenging others and encouraging them to challenge you helps build trusting relationships because it shows 1) you care enough to point out both the things that aren’t going well and those that are and that 2) you are willing to admit when you’re wrong and that you are committed to fixing mistakes that you or others have made. But because challenging often involves disagreeing or saying no, this approach embraces conflict rather than avoiding it.

 When bosses are too invested in everyone getting along, they also fail to encourage the people on their team to criticize one another for fear of sowing discord. They create the kind of work environment where “being nice” is prioritized at the expense of critiquing, and therefore, improving actual performance.

 When you fail to give people the guidance they need to succeed in their work, or put people into roles they don’t want or aren’t well-suited for, or push people to achieve results they feel are unrealistic, you erode trust.

 The hardest part of building this trust is inviting people to challenge you, just as directly as you are challenging them. You have to encourage them to challenge you directly enough that you may be the one who feels upset or angry.

 Your ability to build trusting, human connections with the people who report directly to you will determine the quality of everything that follows.

 At Apple, as at Google, a boss’s ability to achieve results had a lot more to do with listening and seeking to understand than it did with telling people what to do; more to do with debating than directing; more to do with pushing people to decide than with being the decider; more to do with persuading than with giving orders; more to do with learning than with knowing.

 Relationships may not scale, but culture does.

 all teams need stability as well as growth to function properly; nothing works well if everyone is gunning for the next promotion. She called the people on her team who got exceptional results but who were on a more gradual growth trajectory “rock stars” because they were like the Rock of Gibraltar on her team. These people loved their work and were world-class at it, but they didn’t want her job or to be Steve Jobs. They were happy where they were. The people who were on a steeper growth trajectory—the ones who’d go crazy if they were still doing the same job in a year—she called “superstars.” They were the source of growth on any team. She was explicit about needing a balance of both.

 We learn more from our mistakes than our successes, more from criticism than from praise. Why, then, is it important to give more praise than criticism? Several reasons. First, it guides people in the right direction. It’s just as important to let people know what to do more of as what to do less of. Second, it encourages people to keep improving. In other words, the best praise does a lot more than just make people feel good. It can actually challenge them directly.

 By failing to confront the problem, I’d removed the incentive for him to try harder and lulled him into thinking he’d be fine.

## Sprint: How to Solve Big Problems and Test New Ideas in Just Five Days 

Get that surface right, and you can work backward to figure out the underlying systems or technology. Focusing on the surface allows you to move fast and answer big questions before you commit to execution, which is why any challenge, no matter how large, can benefit from a sprint.

 Five days provide enough urgency to sharpen focus and cut out useless debate, but enough breathing room to build and test a prototype without working to exhaustion. And because most companies use a five-day workweek, it’s feasible to slot a five-day sprint into existing schedules.

 First, the sprint forces your team to focus on the most pressing questions. Second, the sprint allows you to learn from just the surface of a finished product.

 The surface is important. It’s where your product or service meets customers.

## Startup CEO: A Field Guide to Scaling Up Your Business, + Website 

the failure of early startup initiatives is predictable, so that failure should be built into the process rather than treated as a crisis when it happens.

 What are the major problems your customers are facing today? What new products and services could you provide to address those problems? Are they looking for an upgrade to a current solution or something completely new? What would it be worth for them to solve this problem (i.e., how much would they be willing to pay to solve it)? A former mentor of mine used to say that people buy things either out of fear or out of greed and that there is a fear/greed continuum where you can actually plot out the behavior of particular buyers. Find out which button your product presses and make sure you orient your questions, development, and sales and marketing around that.

 Keep the whole story in mind: customer, problem, product, solution.

 This includes what our mission is, what our strategy is, our source of competitive advantage, and what our values are. We haven’t used a consistent framework for this

 Inventors create solutions without precedent—often to problems nobody had noticed before. The stories they tell and bring to life require an enormous imaginative leap, like the one Samuel Crompton made when he envisioned an automatic process for spinning cotton. Business builders flesh those stories out. Most often, the biggest detail they include is the main character: the customer.

 Health Trumps Everything Else in Business, and answer five simple questions for ourselves: Why do we exist? How do we behave? What do we do? How will we succeed? What is most important, right now?

 Fred Wilson is right: “setting a company’s vision” is one of the three full-time jobs every startup CEO takes on when they found a company. That vision—the new product, the disruptive service, the “Blue Ocean” monopoly—is liable to be a private moment. The first step toward making that vision a reality is to translate it into a story.

 Stories, like startups, paint a picture of what the future could be. They engage our hearts and minds. They inspire people to act—to give you money, to buy your product, to join your team. Stories have a main character (the customer or user) and a supporting cast (investors, employees, partners, competitors). They have a beginning (the problem), middle (the product), and an end (the solution). Stories take a jumble of facts (profit-and-loss statements, customer surveys, market realities) and give them meaning.

 The goal of a lean business planning process should be to produce three outputs. First is a single slide that you’ll use to define your business model and your underlying hypotheses. Second is a short presentation for partners and investors. Third is your mission, vision, and values statement.

 Either innovate in a field without much competition—like the email deliverability business Return Path started working on 10 years ago when no one was focused on that value proposition—or offer such a large improvement over the competition that it essentially changes the nature of the game.

 To put it bluntly: traditional business plans assume that their assumptions are correct, and startup business plans assume that their assumptions are probably wrong.

 Ford’s customers didn’t say that they wanted a “safer” horse or a “more comfortable” horse. They said that they wanted a faster horse. They were perfectly clear about what they wanted: speed. Jobs is right: “Our task is to read things that are not yet on the page.” Very often, those things are clearly written in between the lines. If you don’t speak with your customers, you’ll miss those subtle—but crucial—insights.

 Even if you’re a crazy micromanager, the minute you have more than a handful of people, you will be delegating a vast percentage of the company’s work and decisions. It is vitally important that your team has clear, codified guideposts for doing things that work and making those decisions.

 Innovation doesn’t have to be complex. One of my favorite examples of this is luggage: for decades, we all carried around suitcases and garment bags and totes that gave us pinched nerves and bad backs as they hung from our shoulders or strained our grips. We sprinted through airports in extreme discomfort, and we assumed that there was no better way. Then someone decided to put wheels on luggage. Wheels, for goodness’ sake. Not electric cars. Not the Human Genome Project. Not cold fusion. Wheels! Those wheels changed the luggage industry and the way we travel for the better. What’s the “wheel” that your industry needs? Don’t search for an analog analogue if there’s something simpler staring you in the face that can explode your market.

 How are you going to test your hypotheses? What would need to happen to prove them right or to disprove them? Remember: revenue is a lagging metric of success. You need to define metrics further up the sales funnel—lead generation, sign-ups, and so on—or your data will come in too late.

 A CEO does only three things. Sets the overall vision and strategy of the company and communicates it to all stakeholders. Recruits, hires, and retains the very best talent for the company. Makes sure there is always enough cash in the bank.

 Given how difficult it is to successfully run a startup, your competitors may not need a broad economic shift to bring them to the brink. If they have something you need—either technology or people—make an offer. If they don’t, prepare your sales team to poach their clients.

 The adoption of lean methodologies has been a huge advance for startups. For decades, countless startups failed after spending too much time on insular product development and too little time “in-market” discovering what their customers want and need.

 The purpose of any business plan is to find new and better ways of serving your customers. You can do that in one of two ways: 1. Come up with a new set of assumptions about what your customers need and want and test those assumptions with customers. 2. Ask your customers what they need and want.

 Here is how a major enterprise might tell the story of their upcoming product release: “Our customers, who number x, have y problem, and they will pay z dollars for our solution. This is our plan for rolling that solution out and these are our cost and revenue projections for the next 18 months.” Here, by contrast, is how a startup should tell its story: “We believe that x potential customers face y problem. Our proposed solution to y problem is solution z at a cost of q dollars—but we’re also going to test the effectiveness of solutions a, b, c. Here is our plan for testing that hypothesis.”

 In the early years of a startup, the only way to define your mission, vision, and values is by way of a top-down process. There’s a simple reason for this: at this stage, your company consists almost entirely of co-founders and executives. There is no crowd of employees to crowd-source from. Either the CEO or a few members of the senior team have to sit down and craft these basic statements, being careful to separate the what (mission and strategy) from the how (values).

 On the y-axis, list all of your ideas. On the x-axis, list the (weighted) criteria you will use to judge those ideas. These are the criteria we have used at Return Path: Customer pain (30%). Does the market need your idea? Market opportunity (10%). How many people need your idea? Today (Size)? Tomorrow (Growth)? Can we win? (20%). Are there already competitors in your chosen space (Competitive Positioning)? If so, will you beat them (Feasibility)? Strategic fit (10%). Is this a problem you can solve? Do you have the right expertise, networks, and so on? Economics (30%). Can you afford to solve this problem?

## The Manager's Path: A Guide for Tech Leaders Navigating Growth and Change 

Unfortunately, sometimes you will mis-hire a person. Having a clear set of expected goals for your new hires that you believe is achievable in the first 90 days will help you catch mis-hires quickly, and make it clear to you and to them that you need to correct the situation. Create a set of realistic milestones based on your prior hires, the current state of your technology and project, and the level of the person coming in.

 A big part of the challenge of time management emerges when you start to lose the sense of importance. Urgency is often more clearly felt than importance.

 As a manager of multiple teams, you’re responsible for balancing breadth and depth of thinking, for knowing the details of your teams today but also looking at where you need to be going in the future and what you need to get there.

 Durable teams are built on a shared purpose that comes from the company itself, and they align themselves with the company’s values (see “Applying Core Values” in Chapter 9 for more on this topic). They have a clear understanding of the company’s mission, and they see how their team fits into this mission. They can see that the mission requires many different types of teams, but all of the teams share a set of values. By creating a strong and enduring alignment between the team, its individuals, and the overall company, this purpose-based binding

 Meetings can fall into that urgent but not important category, and you may decide to simply not attend them where you’re not clearly needed. Be very careful with over-deploying this strategy at this particular level of management. The responsibility of keeping your teams successfully moving forward and happily engaged is on your shoulders. When you stop going to all of their internal meetings, you run the risk of missing out on the very clues that will help you catch problems early — a major one being the existence of too many boring meetings.

 Build Trust and Rapport One strategy is to ask a series of questions that are intended to help you get to know the aspects of the person that impact your ability to manage him well. These questions might include: How do you like to be praised, in public or in private? Some people really hate to be praised in public. You want to know this. What is your preferred method of communication for serious feedback? Do you prefer to get such feedback in writing so you have time to digest it, or are you comfortable with less formal verbal feedback? Why did you decide to work here? What are you excited about? How do I know when you’re in a bad mood or annoyed? Are there things that always put you in a bad mood that I should be aware of? Maybe a direct report fasts for religious reasons, which sometimes makes him cranky. Maybe he always gets stressed out while on-call. Maybe he hates reviews season. Are there any manager behaviors that you know you hate? If you asked me this question, my answer would be: skipping or rescheduling 1-1s, neglecting to give me feedback, and avoiding difficult conversations. Do you have any clear career goals that I should know about so I can help you achieve them? Any surprises since you’ve joined, good or bad, that I should know about? Things like: Where are my stock options? You promised me a relocation bonus and I haven’t gotten it yet. Why are we using SVN and not Git? I didn’t expect to be so productive already! For more ideas, see Lara Hogan’s excellent blog post on the topic.

 The engineering director is not generally expected to write code on a day-to-day basis. However, the engineering director is responsible for their organization’s overall technical competence, guiding and growing that competence in the whole team as necessary via training and hiring. They should have a strong technical background and spend some of their time researching new technologies and staying abreast of trends in the tech industry. They will be expected to help debug and triage critical systems, and should understand the systems they oversee well enough to perform code reviews and help research problems as needed. They should contribute to architecture and design efforts primarily by serving as the technically savvy voice that asks business and product questions of the engineers on their teams, ensuring that the code we are writing matches the product and business needs and can scale appropriately as those needs grow.

 Before you try to change everything to fit your vision, take the time to understand the company’s strengths and culture, and think about how you’re going to create a team that works well with this culture, not against it. The trick is not to focus on what’s broken, but to identify existing strengths and cultivate them.

 Real potential shows itself quickly. It shows itself as working hard to go the extra mile, offering insightful suggestions on problems, and helping the team in areas that were previously neglected. The person who has potential but isn’t yet showing equivalent performance is showing up for the team in a way that others do not, even if her work is slow-going.

 Budget 20% of time for generic sustaining engineering work across the board By “generic sustaining engineering work,” I mean testing, debugging, cleaning up legacy code, migrating language or platform versions, and doing other work that has to happen.

 Create a 30/60/90-Day Plan Another approach that many experienced managers use is to help their new reports create a 30/60/90-day plan. This can include basic goals, like getting up to speed on the code, committing a bug fix, or performing a release, and is especially valuable for new hires and people transferring from other areas of the company.

 Project management is the act of breaking a complex end goal down into smaller pieces, putting those pieces in roughly the most effective order they should be done, identifying which pieces can be done in parallel and which must be done in sequence, and attempting to tease out the unknowns of the project that may cause it to slow down or fail completely.

 Ultimately, the value of planning isn’t that you execute the plan perfectly, that you catch every detail beforehand, or that you predict the future; it’s that you enforce the self-discipline to think about the project in some depth before diving in and seeing what happens.

 delegation is not the same thing as abdication. When you’re delegating responsibility, you’re still expected to be involved as much as is necessary to help the project succeed. Sharell didn’t just abandon Beth — she helped Beth understand the responsibilities in the new role and was there as needed to support the project.

 Determine which decisions must be made by you, which decisions should be delegated to others with more expertise, and which decisions require the whole team to resolve. In all of these cases, make it clear what the matter under discussion is, and communicate the outcome.

 Jane’s and Sharell’s decisions highlight the subtle differences between the micromanager and the effective delegator. Both Jane and Sharell are attempting to delegate the management of a high-priority project in order to train a new leader on their team. However, Jane ultimately never gives up control and undermines Sanjay, while Sharell makes it clear to Beth what the goals are and what her responsibilities are, and provides support and guidance to help Beth succeed.

 You have 10 productive engineering weeks per engineer per quarter

 Saying no to your boss rarely looks like a simple “no” when you’re a manager. Instead, it looks like the “yes, and” technique of improvisational comedy. “Yes, we can do that project, and all we will need to do is delay the start of this other project that is currently on the roadmap.” Responding with positivity while still articulating the boundaries of reality will get you into the major leagues of senior leadership.

 It’s important to remember that, as a technical leader, while you may not be writing code much, you’re still responsible for the technical side of getting work done. You’re also responsible for keeping your team happy and productive, and often the solution to this is not cheerleading or paying them better or praising them more, but instead enabling them to be more productive, challenging them to go faster and do better work, and helping them find the time they need to make their work more interesting. You have to be the advocate and push for technical process improvements that can lead to increased engineer productivity, even if you’re not implementing them all yourself.

 Do set up clear processes to depersonalize decisions. When you want to allow for group decision making, the group needs to have a clear set of standards that they use to evaluate decisions. Start with a shared understanding of the goals, risks, and the questions to answer before making a decision. When you assign the ownership for making a decision to someone on the team, make it clear which members of the team should be consulted for feedback and who needs to be informed of the decision or plan.

 Don’t confuse “potential” as it might be described by a grade-school teacher with the type of potential you care about. You are not molding young minds; you’re asking employees to do work and help you grow a company. Potential, therefore, must be tied to actions and value produced, even if it’s not directly the value you expected to see produced.

 Doesn’t agile software development get rid of the need for project management? No. Agile software development is a great way to think about work because it forces you to focus on breaking tasks down into smaller chunks, planning those smaller chunks out, and delivering value incrementally instead of all at once.

 The real goal here is psychological safety — that is, a team whose members are willing to take risks and make mistakes in front of one another. This is the underpinning of a successful team. The work of gelling a team begins by creating the friendliness that leads to psychological safety. You can encourage this by taking the time to get to know people as human beings

 Trust and control are the main issues around micromanagement. If you’re micromanaging someone, chances are you’re doing it because you don’t trust that a task will be done right, or you want to very tightly control the outcome so that it meets your exact standards.

 Process czars struggle when they fail to realize that most people are not as good at following processes as they are. They tend to blame all problems on a failure to follow the best process, instead of acknowledging the need for flexibility and the inevitability of unexpected changes. They often get focused on easy-to-measure things, such as hours in the office, and miss the nuances that they fail to capture when focusing on the things that are easy to measure.

 Unfortunately, sometimes you will mishire a person. Having a clear set of expected goals for your new hires that you believe is achievable in the first 90 days will help you catch mishires quickly, and make it clear to you and to them that you need to correct the situation. Create a set of realistic milestones based on your prior hires, the current state of your technology and project, and the level of the person coming in.

 Consider this scenario: Jack is having a hard time with a project, but hasn’t been asking for help with his problems. You finally hear about his struggles. At this point, it’s appropriate to tell Jack that he needs to be more proactive in sharing his progress, even if it means admitting he’s struggling. You could have Jack give you daily updates as a way of helping, but I would only use that much structure for a brief period. The goal here isn’t to punish him with micromanagement for his failure to communicate status, because all you’re doing is punishing yourself and hindering his ability to be held accountable for his own work. Instead, your goal is to teach Jack what he needs to communicate, when, and how. A word of caution, though; if you treat a struggling engineer or project as a massive failure on the part of the individual or manager, she is going to feel that blame and criticism, and instead of giving you more information in the future, she’ll keep hiding it from you as a way of avoiding blame until it’s too late. Hiding important information intentionally is a failure, and getting stuck on a problem or making a mistake is often just an opportunity for learning.

 Do remember to be kind. It’s natural and perfectly human to want to be liked by other people. Many of us believe that the way to be liked is to be seen as nice — that niceness is itself the goal. Your goal as a manager, however, should not be to be nice, it should be to be kind. “Nice” is the language of polite society, where you’re trying to get along with strangers or acquaintances. Nice is saying “please” and “thank you” and holding doors for people struggling with bags or strollers. Nice is saying “I’m fine” when asked how you are, instead of “I’m in a really crappy mood and I wish you would leave me alone.” Nice is a good thing in casual conversation. But as a manager, you will have relationships that go deeper, and it’s more important to be kind. It’s kind to tell someone who isn’t ready for promotion that she isn’t ready, and back that up with the work she needs to do to get there. It’s unkind to lead that person on, saying “Maybe you could get promoted,” and then watch her fail. It’s kind to tell someone that his behavior in meetings is disrupting the group. It’s awkward, and uncomfortable, but it’s also part of your job as his manager to have these difficult conversations.

 Developing basic standards as a team helps everyone communicate with one another in code and design reviews, and it depersonalizes the process of providing technical feedback. For me, basic standards meant things like how much unit testing we expected to happen with each change (generally speaking, as some tests were always required), and at what point technical decisions should be reviewed by a larger group (like when someone wants to add a new language or framework to the stack). As with goal setting, putting standards in place here helps people know which details are important to think about when they’re creating the technology.

 Start mastering the “yes, and” strategy for saying no, particularly when interacting with your boss and peers, and see how it often transforms contentious disagreements into realistic negotiations for priority.

 Autonomy, the ability to have control over some part of your work, is an important element of motivation. This is why micromanagers find it so difficult to retain great teams. When you strip creative and talented people of their autonomy, they lose motivation very quickly. There’s nothing worse than feeling like you can’t make a single decision on your own, or feeling like every single piece of work you do has to be double- and triple-checked by your manager.

 Don’t rely exclusively on consensus or voting. Consensus can appear morally authoritative, but that assumes that everyone involved in the voting process is impartial, has an equal stake in the various outcomes, and has equal knowledge of the context.

 When you feel like you want to micromanage, ask the team how they’re measuring their success and ask them to make that visible to you on an ongoing basis. Then sit on your hands if you must, but wait a week or two to see what they give you. If they have nothing to share, it’s a sign that you may need to do a course correction, which probably means digging into more details.

 Teams often fail because they overworked themselves on a feature that their product manager would have been willing to compromise

 Listening is a precursor to empathy, which is one of the core skills of a quality manager.

 Your manager should be the person who shows you the larger picture of how your work fits into the team’s goals, and helps you feel a sense of purpose in the day-to-day work.

## The Phoenix Project: A Novel About IT, DevOps, and Helping Your Business Win 

Get humans out of the deployment business. Figure out how to get to ten deploys a day.”

 You need to get everything in version control. Everything. Not just the code, but everything required to build the environment. Then you need to automate the entire environment creation process. You need a deployment pipeline where you can create test and production environments, and then deploy code into them, entirely on-demand. That’s how you reduce your setup times and eliminate errors, so you can finally match whatever rate of change Development sets the tempo at.”

 until code is in production, no value is actually being generated, because it’s merely WIP stuck in the system. He kept reducing the batch size, enabling fast feature flow.

 “a ‘change’ is any activity that is physical, logical, or virtual to applications, databases, operating systems, networks, or hardware that could impact services being delivered.”

 “Properly elevating preventive work is at the heart of programs like Total Productive Maintenance, which has been embraced by the Lean Community. TPM insists that we do whatever it takes to assure machine availability by elevating maintenance.

 if a resource is ninety percent busy, the wait time is ‘ninety percent divided by ten percent’, or nine hours. In other words, our task would wait in queue nine times longer than if the resource were fifty percent idle.”

 A key causal factor for vehicle breakdowns is failure to change the oil. So, to mitigate that risk, you’d create an SLA for vehicle operations to change the oil every five thousand miles.” Obviously enjoying himself, he keeps explaining, “Our organizational key performance indicator (KPI) is on-time delivery. So to achieve it, you would create a new forward-looking KPI of, say, the percentage of vehicles that have had their required oil changes performed. “After all, if only fifty percent of our vehicles are complying with the required maintenance policies, it’s a good bet that in the near future, our on-time delivery KPIs are going to take a dive,

 “Stop focusing on the deployment target rate. Business agility is not just about raw speed. It’s about how good you are at detecting and responding to changes in the market and being able to take larger and more calculated risks. It’s about continual experimentation, like Scott Cook did at Intuit, where they did over forty experiments during the peak tax filing season to figure out how to maximize customer conversion rates. During the peak tax filing season!

 Any improvement made after the bottleneck is useless, because it will always remain starved, waiting for work from the bottleneck. And any improvements made before the bottleneck merely results in more inventory piling up at the bottleneck.”

 “What that graph says is that everyone needs idle time, or slack time. If no one has slack time, WIP gets stuck in the system. Or more specifically, stuck in queues, just waiting.”

 kanban board, among many other things, is one of the primary ways our manufacturing plants schedule and pull work through the system. It makes demand and WIP visible, and is used to signal upstream and downstream stations.

 “every work center is made up of four things: the machine, the man, the method, and the measures.

 “A great team doesn’t mean that they had the smartest people. What made those teams great is that everyone trusted one another.

 “Goldratt taught us that in most plants, there are a very small number of resources, whether it’s men, machines, or materials, that dictates the output of the entire system. We call this the constraint—or bottleneck.

 Studies have shown that practicing five minutes daily is better than practicing once a week for three hours. And if you want to create a genuine culture of improvement, you must create those habits.”

 “The First Way helps us understand how to create fast flow of work as it moves from Development into IT Operations, because that’s what’s between the business and the customer. The Second Way shows us how to shorten and amplify feedback loops, so we can fix quality at the source and avoid rework. And the Third Way shows us how to create a culture that simultaneously fosters experimentation, learning from failure, and understanding that repetition and practice are the prerequisites to mastery.”

 At this level, I care more about the integrity of the process, not so much about the actual changes.”

 “Unlike the other categories of work, unplanned work is recovery work, which almost always takes you away from your goals. That’s why it’s so important to know where your unplanned work is coming from.”

 “Remember, outcomes are what matter—not the process, not controls, or, for that matter, what work you complete.”

 “Unplanned work has another side effect. When you spend all your time firefighting, there’s little time or energy left for planning. When all you do is react, there’s not enough time to do the hard mental work of figuring out whether you can accept new work.

 You must figure out how to control the release of work into IT Operations and, more importantly, ensure that your most constrained resources are doing only the work that serves the goal of the entire system, not just one silo.

 “Metaphors like oil changes help people make that connection. Preventive oil changes and vehicle maintenance policies are like preventive vendor patches and change management policies. By showing how IT risks jeopardize business performance measures, you can start making better business decisions.

 ‘Improving daily work is even more important than doing daily work.’

 every stage of the agile development process, you not only have shippable code, but a working environment it can deploy into!”

 “It’s like the free puppy,” I continue. “It’s not the upfront capital that kills you, it’s the operations and maintenance on the back end.” Chris cracks up. “Yes, exactly! They’ll say, ‘The puppy can’t quite do everything we need. Can you train it to fly airplanes? It’s just a simple matter of coding, right?’

 Resilience engineering tells us that we should routinely inject faults into the system, doing them frequently, to make them less painful.

 “Eliyahu M. Goldratt, who created the Theory of Constraints, showed us how any improvements made anywhere besides the bottleneck are an illusion.

 ‘technical debt’ that is not being paid down. It comes from taking shortcuts, which may make sense in the short-term. But like financial debt, the compounding interest costs grow over time. If an organization doesn’t pay down its technical debt, every calorie in the organization can be spent just paying interest, in the form of unplanned work.”

 We need to create a culture that reinforces the value of taking risks and learning from failure and the need for repetition and practice to create mastery.

 some IT controls he holds near and dear aren’t needed, because other parts of the organization are adequately mitigating those risks.

 “Mike Rother says that it almost doesn’t matter what you improve, as long as you’re improving something. Why? Because if you are not improving, entropy guarantees that you are actually getting worse, which ensures that there is no path to zero errors, zero work-related accidents, and zero loss.”

## The Scientist’s Guide to Writing: How to Write More Easily and Effectively throughout Your Scientific Career 

The first element is a relentless focus on the goal of crystal-clear communication:

 If the reader pauses to question your word choice or needs to squint to distinguish between two lines on a graph, then you have joined a battle you don’t want to be in: what you’re trying to say is fighting for the reader’s attention with the way you’re saying it.

 •  A paper has a story, with “characters” and a “plot,” and it raises and answers an interesting question.

 You should be able to state question and answer in a sentence or two—perhaps not in a way useful for a reader, who would need definitions, context, and so on; but in one that defines the story for you.

 Should you write in the active voice or the passive? How many decimal places should you give for the numbers in a table? Should your data be in a table at all, or in a figure? In each case, the route to an answer is the same: the better choice is the one that lets the reader more effortlessly understand the story you have to tell.

 As a scientist, you’ll work hard to make new discoveries about the world; but only writing (and publication) makes what you’ve learned part of human knowledge.

 Component 3: Occupy the niche. The third component of the Introduction indicates to a reader how your work occupies the niche you’ve just identified.

 Having established context, your Introduction begins to narrow the hourglass by identifying your more specific research territory, along with its relationship and importance to the broader field.

 Finally, your Introduction will state, clearly and specifically, your central research question

 My realization that most writers, including scientific writers, worked hard at their craft, rather than being natural geniuses, was transformative for me. It led me to think of hard work at the craft of writing as a normal part of my job.

 Outlining the approach doesn’t mean presenting detailed methods, of course. It means indicating your basic approach (the kind of experiments, observations, and/or theory you executed), the general form of your data (what important quantities you measured, and roughly how), and how analyses of those data can answer your central research question.

 Concept maps. A concept map (Figure 7.2) is a tool for exploring relationships among concepts (Novak and Cañas 2008). It consists of a set of nodes connected by lines. Each node is a concept: a word or phrase denoting an idea, a thing, or a property of one of these. Each line connects two nodes and is labelled to indicate the relationship between those concepts. Typically, most nodes will be nouns or adjectives, while most line labels will be verbs.

 Wordstacks. A wordstack (Figure 7.1) is an unsorted list of points you think might be useful ingredients in your manuscript. Each point can be a single word or short phrase indicating a relevant fact, idea, or topic, or can be a roughly sketched graphic. Your wordstack might have some hierarchical structure (some points having subpoints) if this is immediately obvious, but don’t force it.

 Component 1: Define a research territory.

 Very good: If massive stars form with gravitational assists from their neighbors, then massive protostars should always appear among other protostars. However, solitary massive protostars are common in ALMA images of the Orion, Eagle, and Carina nebulae. This mini-summary has a clear central question (do massive protostars form via combined gravity of neighbors?), and offers an answer (no). The question drives the function of each part of the manuscript: the Introduction will set up the cluster-gravity hypothesis and specify what’s needed to test it; the Methods will explain how we can measure protostar masses and distinguish between solitary protostars and sets of neighbors; the Results will tabulate frequencies of solitary and neighbored protostars; and the Discussion will interpret the Results as a test of the cluster-assist hypothesis.

 Second, saying that your paper is about your results places the focus on the writer (“your results”), which is not where it should be. Good writing is oriented to the needs of the reader. You should ask not “what should I write about?” but instead “what does my reader need to hear about?

 a concrete and narrow open problem within the research territory.

 •  “There’s a controversy in the literature over issue X, and I present the kind of data needed to resolve it.” •  “The fact that we don’t know X hinders our efforts to understand issue Y, which is central to a developing subdiscipline.” •  “Our lack of understanding of thing X impedes our efforts to solve economic problem Y.” •  “We need to know more about thing X because it’s a model system widely used to investigate problems in field Y.”

 This might mean pointing out a gap in our knowledge of some topic. It might mean noting an apparent contradiction in the literature or a published claim that’s vulnerable to new information. It might mean identifying rival theoretical models that can be distinguished by new data. It might even mean suggesting an entirely novel way of thinking about a research area.

 Whenever you are not sure whether a dataset, analysis, figure, table, or anything else belongs in the manuscript, referring to this two-sentence mini-summary should give you the answer: would including it help tell the story or distract from it?

 •  Telling your story isn’t enough; you must sell it, too. This means showing how your work solves a problem, or answers a question, that matters to readers.

 I could set out deliberately to learn and to practice the elements of the craft, rather than sitting at my keyboard hoping for genius to strike.

 Leaving things out is critical to finding and telling your story. However, it’s very important to think carefully about what it means to present “only those results necessary to support your conclusion.” This does not mean omitting results that conflict with your conclusion, which, of course, is unethical. It does mean omitting results that are not relevant to your conclusion, or are redundant with others that suffice to support it.

 Setting context for the work is now the most important work of the Introduction.

 This part of the Introduction normally includes some literature review to establish the state of the art in the research territory.

 Component 2: Establish a niche within the research territory.

 •  A well-organized paper will have an “hourglass” structure, with focus broad at the beginning, narrowing through the Introduction, and widening again through the Discussion.

 While my suggestions about the components of an Introduction should so far be uncontroversial, there is considerable disagreement over how best to end one. Some writing guides recommend ending the Introduction with the statement of your central question and approach (e.g., Davis 2005, Katz 2006). Others suggest continuing with a brief summary of your results (e.g., Montgomery 2003, Day and Gastel 2006). My own advice is to include the main result, because doing so shows your reader where you are going and helps signpost their progress through your paper.

## The User's Journey: Storymapping Products That People Love 

As such, an origin story acts as a bridge between your concept story and your usage story—bridging the gap between the concept of a product or service and the actual usage of it. It’s where and when potential customers not only see what they can do with a product, but also how they can take an action with it.

 Apple solved a problem that people didn’t know they had. As such, the 2007 keynote, as well as the device itself, not only had to tell the world what their problem was, but also show what the problem was and highlight how the solution could look and function.

 In Badass: Making Users Awesome, Kathy Sierra argues that creating successful products is not about what features you build—it’s about how badass you make your user on the other end feel. It’s not about what your product can do, but instead about what your users can do if they use your product.

