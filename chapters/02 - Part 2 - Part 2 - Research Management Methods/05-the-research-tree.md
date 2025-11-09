\newpage

## Chapter 4 - The Research Tree {#the-research-tree}

You've probably seen this: An engineer/researcher starts down one path, hits an obstacle, tries something else, hits another obstacle, then tries a third approach. Three weeks later, they're still stuck - or worse, they've built something that technically works but doesn't solve the actual problem.

The issue isn't persistence. It's that they never mapped out the solution space. They never visualized **which** approaches might work, **which questions** need answering, and **how** everything relates to each other.

**The Research Tree solves this problem.**

It is a way to visualize and manage the **Control** component of Schoenfeld's framework from [chapter 1](#what-is-research) - monitoring and adjusting your approach. This is where most Research efforts struggle.

![Reminder: Schoenfeld's Framework](images/chapter01/components_of_problem_solving.png)

### What Is a Research Tree?

A Research Tree is a living visual representation of your Research journey. It captures three things:

1. **Possible solution paths** - different approaches you might take.
2. **Open questions** - what you need to learn.
3. **Closed questions** - what you've already discovered.

Unlike a static plan, the Research Tree grows and changes as you learn (which is one reason I like the name "tree" 😇). You start with what you know, then update it continuously as you investigate. Dead ends get marked. New branches appear. Questions get answered and new questions emerge.

Think of it like this: You're exploring a cave system. You don't have a map - you're *creating* the map as you explore. You mark passages you've tried. You note which ones are dead ends. You write down questions: "Does this passage connect to the main chamber?" "Is there water down this route?" As you explore, you answer some questions and discover new ones you hadn't considered. You write down the answers you found, and the experiments you conducted to find them ("I tried going left, hit a wall after 50 feet").

Research works the same way. The Research Tree is both your map and your log.

### Your First Research Tree

Let's build one together. Consider a common engineering challenge:

**Goal: Reduce API response time from 800ms to under 100ms**

You start with a fundamental question that needs answering. What's the first thing you need to know?

Take a moment to think about this before reading on.

The first question is usually: **Where is the bottleneck?**

Until you answer this, you don't know which approaches make sense. Let's draw this:

![Initial Research Tree](images/chapter04/research_tree_1.png)

You can use a simple pen and paper, a whiteboard, or a digital tool to draw this out. When creating your very first tree, I highly recommend doing it by hand - the physical act of drawing will help you feel comfortable with the process.

Now, how can you answer this question? What approaches might tell you where the bottleneck is?

You might identify:
- Profile the application with a performance monitoring tool.
- Add detailed logging to measure each operation.
- Use database query analysis tools.

Let's add these as branches:

![Research Tree with a few directions](images/chapter04/research_tree_2.png)

(Note: the Brown status means "uncertain, needs investigation" - more on this later.)

Each approach is an investigation you could run to answer the question.

### The Power of Stopping to Think

Before we go further, notice what just happened. **You stopped.**

Instead of immediately jumping into "Let's add more logging!" or "I bet it's the database, let's check queries," you identified multiple possible approaches. You're looking at three different ways to answer the same question.

This is already valuable. Most engineers would have jumped straight into whichever approach came to mind first. Maybe you've done this yourself - spent two days adding detailed logging, only to discover later that a profiler would have given you the answer in 30 minutes.

By creating this tree, you've avoided that trap. You can see all the approaches before committing to any of them. It doesn't guarantee you will choose the "right" path - you can't always do that in advance – but it will minimize the chances of you omitting it completely.

Remember the reverse engineering students from [chapter 3](#why-methodology-matters)? They never created this tree. They jumped straight to the first approach they knew: disassemblers and debuggers. They didn't stop to think: "What are all the ways we could understand this game's rules?" If they had, they would have listed approaches like: reverse engineer the binary, check the Help menu, just play the game, examine config files, watch network traffic. And if they'd evaluated those approaches using the framework you're about to learn, "check the Help menu" would have scored perfectly: fastest feedback (30 seconds), lowest cost (zero), best coverage (complete rules). Instead, they spent hours on complex reverse engineering when a simple menu click would have worked. Don't be those students.

![A simple tree for the game makes it clear starting with reversing is the wrong option](images/chapter04/research_tree_3.png)

**Now comes the critical question: Which branch do you try first?**

Consider our tree again:

![Research Tree with a few directions](images/chapter04/research_tree_2.png)

### Choosing Your First Path

You're looking at three approaches: Profile, Logging, DB Analysis. Each is a **heuristic** (in Schoenfeld's terms, as presented in [chapter 1](#what-is-research)) - a problem-solving strategy that might work. How do you decide which one to try?

Sometimes, the answer is obvious (I wouldn't really use a framework to check if there's a "Help" menu). Let me show you the framework I use when it's not so clear which path to choose. Ask yourself these questions:

**1. Which gives the fastest feedback?**

How long until you get an answer?

- Profile: Can run in 10 minutes. Setup is probably 5 minutes.
- Logging: Need to add logging code, deploy, wait for traffic - maybe 4 hours.
- DB Analysis: Need to enable slow query log, wait for data - maybe 2 hours.

**Fastest feedback wins.** You want to learn quickly.

**2. Which has the lowest cost?**

What do you need to set up or change?

- Profile: Just attach a profiler - no code changes.
- Logging: Need to modify code, test, deploy.
- DB Analysis: Need database permissions, might need config changes.

**Lower cost wins.** Why spend hours adding logging if you can get the answer without changing any code?

(In your environment, it may be different. Perhaps logging is really easy, while profiling is super hard to set up. I am not claiming that profiling is a better heuristic than logging - it depends on your circumstances.)

**3. Which answers the most questions?**

Some approaches answer not just your immediate question, but related questions, too.

- Profile: Shows you CPU, memory, database, network - a complete picture.
- Logging: Only shows what you logged.
- DB Analysis: Only shows database queries.

**Broader coverage wins.** A profiler might show you that 70% of time is database queries *and* that 20% is network latency - information you wouldn't get from narrow approaches.

![Prioritizing heuristics framework](images/chapter04/path_priorities.png)

So this is an easy one. **Profiling wins on all three criteria.** That's your first approach to try.

Update your tree:

![Start with profiling](images/chapter04/research_tree_4.png)

This doesn't mean the other approaches are bad, or that this one will necessarily turn out to be the best. It means that profiling is the best *starting point* given what you know right now.

### What If Your First Choice Doesn't Work?

Let's say you try profiling and hit a problem: Your profiler can't attach to the production environment due to security restrictions.

**This is valuable information.** Mark Profile as Red and move to your next best option:

![Profiling failed, pivot to logging](images/chapter04/research_tree_5.png)

Now you try Logging. But notice: You didn't waste days trying Profile in production. You tried it, hit a blocker, immediately pivoted to Logging. The tree helped you move quickly.

### Choosing When Everything Seems Equal

Sometimes multiple approaches look equally good. Profile and DB Analysis might both be fast, low-cost, and have decent coverage. How do you choose?

**Pick one and move on.** Don't spend an hour analyzing which approach to try for 30 minutes. The meta-work (deciding) shouldn't take longer than the actual work (trying it).

When approaches seem equal, ask: "Which one am I more familiar with?" or "Which one does the team have experience with?" Use your judgment, make a choice, and start learning.

The worst decision is no decision.

In general, this approach might feel like over-kill. Should you really sketch out trees and compare branches before actually doing something?

The surprising answer is that while almost always it feels like over-kill - almost every single time, it turns out to be worth it. Try it a few times and you will see for yourself.

### Heuristics Can Be Combined

Sometimes you don't have to choose just one. You might run Profile *and* enable DB Analysis simultaneously. If they don't conflict and you have the time, parallel investigations can be powerful.

But be careful: Don't try to do everything at once. Start with your best option. If that doesn't fully answer your question, then add another approach.

### How Answers Lead to New Questions

Let's say you choose "Profile" and run it for a day. You discover: **70% of response time is database queries**.

![Database is the bottleneck](images/chapter04/research_tree_6.png)

This answer eliminates the need for other approaches (you don't need logging now - you found the answer). But more importantly, it reveals new questions:

![New questions emerge](images/chapter04/research_tree_7.png)

See how the tree grows? One answered question spawns two new questions. Each of these new questions will have its own approaches for answering them.

And you'll apply the same framework to choose which question to answer first: Which gives fastest feedback? Which has lowest cost? Which answers the most questions?

Let's expand "Which queries are slowest?":

![Research tree expanding](images/chapter04/research_tree_8.png)

Again, you'd evaluate: Which approach gives fastest feedback? Enabling slow query log is probably fastest - you just flip a config flag and wait a few minutes.

You decide to enable the slow query log. After investigating, you discover: **User profile queries are slowest - they make 15 separate database calls (N+1 problem)**.

(What is the N+1 problem in this context? It means that when fetching user profiles, the code first queries for a list of users (1 query), then for each user, it makes an additional query to fetch related data (N queries). If there are 15 users, that's 16 queries total. This is inefficient and slows down response time.)

This answer leads to a new question:

![New question about fixing N+1](images/chapter04/research_tree_9.png)

Now you have three solution approaches. Again, evaluate them:
- Rewrite queries with JOINs: Fast to implement, proven pattern.
- Add Eager Loading: Depends on your ORM, might be quick.
- DataLoader Pattern: Requires learning new pattern, takes longer.

Rewrite queries with JOINs probably gives the fastest feedback if your team knows SQL well.

### The Complete Picture

Let's see how the full tree looks after a few days of investigation:

![Completed research tree example](images/chapter04/research_tree_complete.png)

(Note: for the "How many queries per request?" node - I skipped the approaches for brevity.)

**Reading this tree:**

1. We started with "Where is the bottleneck?" and chose profiling (fastest feedback).
2. That answer led to two new questions about specific queries.
3. For "Which queries are slowest?", we chose slow query log (fastest to enable).
4. Answering it led to another question about fixing the N+1 problem.
5. For "How can we fix N+1?", we evaluated the approaches and chose "Rewrite queries with JOINs" (team knows SQL, fastest to implement).
6. Meanwhile, "Can we reduce query count?" is still open and has its own approaches to investigate.

### Color-Coding Status

When you're creating your Research Tree, you'll mark both questions and approaches with a particular status. Of course, the following specific colors are just suggestions - the important thing is to keep something consistently so you can quickly see the status at a glance.

**For Questions:**
- **Open**: Not yet answered.
- **Closed**: Answered (show the answer).
- **Blocking**: Must answer before proceeding with an approach.

**For Approaches:**
- **Green**: Viable, worth pursuing.
- **Brown**: Uncertain, needs investigation.
- **Red**: Dead end or not viable.

In our example above:
- "Rewrite with Joins" is Green because we've identified that it addresses the specific N+1 problem and that the team is confident in implementing it.
- "Redesign API" is Red because it would take too long for this project.
- Other approaches are Brown because we haven't investigated them yet.

### The Research Tree Prevents Common Pitfalls

The Research Tree with this decision-making framework addresses five critical failure modes:

**1. Jumping on First Idea**
Without a tree, people implement the first approach they think of. The tree forces you to identify alternatives and evaluate them systematically before starting.

**2. Tunnel Vision**
People lock onto one approach without considering alternatives. The tree makes alternatives visible and helps you choose the best starting point.

**3. Inefficient Learning**
Teams might try expensive, slow approaches first when faster, cheaper ones exist. The decision framework helps you learn quickly.

**4. Answering Questions You Don't Need To**
Teams waste time investigating interesting but irrelevant questions. The tree shows how questions connect - you only need to answer questions that lead to your goal.

**5. Lost Context**
When you hit a roadblock, you need to know which question you were trying to answer and what other approaches exist. The tree provides that context.

### Time to Practice

Open your favorite drawing tool - or just grab a piece of paper. Think of a Research problem you're currently facing or recently faced.

Now answer these questions:

1. What's your goal? Write it at the top.
2. What's the first question you need to answer? Write it below the goal.
3. What are 2-4 approaches to answer that question? Draw them as branches.
4. For each approach, evaluate:
   - How fast is the feedback?
   - What's the cost?
   - How much does it answer?
5. Which approach scores best? Mark it "TRY FIRST".

Actually do this. Don't just read and think "I understand." Drawing the tree and evaluating approaches forces you to be explicit, and you'll immediately see gaps in your thinking.

I'll wait.

...

Don't worry about me, I'm enjoying some really great coffee in the meanwhile.

...

Done? Good. You now have your first Research Tree with a clear starting point.

### Using the Tree with Your Team

Research Trees become even more powerful when shared with a team. It actually provides you, the Lead, with a way to see what directions the team is executing upon, and why. Your job here is to make sure the framework is used. Help your team stop and ask: are we asking the right questions? Are there approaches that we missed? Are we choosing the right approach?

**During Planning:**
- Draw the tree together as a group.
- Brainstorm questions and approaches.
- Evaluate approaches using the framework (fastest feedback, lowest cost, best coverage).
- Everyone sees *why* you're trying a particular approach first.

**During Execution:**
- Update the tree as you learn.
- When stuck, revisit the tree to identify alternative approaches.
- Make sure you consider whether you are asking all of the important questions, and whether you are considering all relevant approaches.
- Conduct regular tree reviews (weekly or bi-weekly).

Note that the Research Tree is also useful for one on one sessions - you can review the tree with individual team members to understand their progress and help them choose next steps. It actually makes the Control component of Schoenfeld's framework much easier to manage - as you see the variolus questions and approaches laid out visually.

### Tools

- Pen and paper (seriously, this works great).
- Whiteboard (for team sessions).
- Miro, Mural, or similar digital whiteboards.
- Mind mapping software (XMind, MindNode, and so on).
- Even a simple text file with indentation.

The tool doesn't matter. What matters is that the tree exists, is visible, and gets updated.

### Pro Tips

**Start with the most important question**

Don't try to list all possible questions upfront. Start with the one question that, if answered, would most clarify your path forward. Answer it, then see what new questions emerge. More on finding the questions to start from in [chapter 7](#drawing-backwards).

**Show how answers lead to new questions**

When you close a question, immediately ask: "What new questions does this answer reveal?" Draw those as branches from the answer.

**Update questions weekly**

In your weekly check-ins, explicitly review: Which questions did we close? What did we learn? Which new questions emerged? Which questions are blocking progress?

**Re-evaluate when context changes**

If you learn something new that changes the evaluation (maybe a tool you thought was fast turns out to be slow), re-evaluate your approaches. The tree is living - update it.

### Recap - The Research Tree

The Research Tree is a living visual framework that:

- Shows questions you need to answer to reach your goal.
- Maps approaches for answering each question.
- Helps you choose the best starting point for each question.
- Prevents jumping on the first idea without considering alternatives.
- Captures how answers lead to new questions.
- Tracks status of questions (open/closed/blocking) and approaches (green/brown/red).
- Documents the investigation path so the team understands why decisions were made.
- Evolves as you learn - questions get answered, new questions emerge.

**Key structure:**
- Goal → Question → Approaches to answer it → Answer → New questions

**Decision framework for choosing approaches:**
1. Which gives fastest feedback?
2. Which has lowest cost?
3. Which answers the most questions?

In the next chapter, you'll learn how to manage execution using time-boxing and decision points to keep your Research moving forward without getting stuck.

