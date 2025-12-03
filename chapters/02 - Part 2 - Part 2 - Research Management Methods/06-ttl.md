\newpage

## Chapter 5 - Time-Boxing Research Explorations {#time-boxing}

In the previous chapter, you learned about the Research Tree, a powerful tool for visualizing and managing Research efforts. The tree helps you systematically explore different solution paths and keep track of open questions. It also helps you decide which path to try first.

But once you've chosen a branch - how long should you pursue it before stepping back to reconsider?

### The Problem: Research Without Time Limits

A researcher investigates whether a machine learning model can predict code complexity. Day one goes well. Day two, they need more features. Day three, a different architecture might work better. They switch. Day four, the new architecture needs different preprocessing.

Two weeks later, they're still on this path. When you ask about trying alternatives, they say "I'm close. Just need a few more days."

Three weeks in, they admit this approach isn't viable. Meanwhile, a simpler approach sat unexplored on the Research Tree.

Without a defined checkpoint, there's no natural moment to ask: "Given what I've learned, is this still the best path?" The sunk cost fallacy (continuing an approach because you've already invested time, rather than because it's still the best option) takes over. This is extremely common by Researchers, who tend to be dedicated, brilliant people who get fixated by problems they try to solve.

### Time-Boxing: Creating Decision Points

Let's face it: it's hard, even impossible, to estimate how long a Research task will take. But you should still provide time limits - based on how long you're willing to invest before reconsidering.

**Time-boxing provides mandatory decision points.**

Note that we are not talking about deadlines, but decision points. These are moments where you stop and evaluate: What did I learn? Is this still the most promising path?

As a rule, for every task longer than a day, define a time limit. For example: "I'll spend three days investigating whether we can cluster files into logical folders based on their I/O operations."

Three things can happen:

**Early success:** The researcher figures it out in a few hours. Done early, move to the next question.

**Early blocker:** After one hour, they discover they don't have access to filenames. They can immediately reconsider: "Without filenames, is this viable?"

**Time box expires:** Three days pass with partial progress. Now comes the mandatory decision point.

![For every task that is longer than a day, define a time limit](images/chapter05/time_limit.png)

### The Decision Point

When your time box expires, stop. Pull out your Research Tree (yes, you already love that Tree). Ask three questions:

**1. What was your goal in pursuing this direction?**

Which question were you trying to answer? Why did you choose this approach over alternatives?

**2. What did you learn?**

Document your discoveries, even if incomplete:

- "The approach works but needs more sophisticated algorithms than we thought."
- "We need data we don't currently have."
- "This is harder than expected - would take at least 2 more weeks."
- "We're 70% there - just need to handle edge cases."

**3. Given what you learned, is this still the most promising path?**

Look at your Research Tree. You have other branches. Given what you now know, is continuing the best use of time?

![When the limit expires, stop to reconsider your next steps](images/chapter05/limit_expired.png)

You have three options:

**Continue with a new time box:** "I've solved the core challenge. One more day for edge cases." Define the new time box. The key: you consciously decided to continue based on what you learned, not enertia.

**Pivot:** "This would take two more weeks, and I'm not confident it'll work. There's a simpler approach on my tree." Mark this branch Red. Move to a different branch.

**Reconsider the question:** "Files in this codebase don't have clear I/O patterns. Maybe I should try clustering by function dependencies instead." Go back to your tree and identify a different question.

### Example: Detecting God Objects

You're detecting God Objects (classes that do too much) using static analysis. Your Research Tree shows three approaches: complexity metrics, method naming patterns, or machine learning on AST features.

You choose complexity metrics (fastest feedback, lowest cost) and set a 2-day time box.

**Day 1-2:** You implement [cyclomatic complexity](https://en.wikipedia.org/wiki/Cyclomatic_complexity) and [SLOC](https://en.wikipedia.org/wiki/Source_lines_of_code) metrics. Results: 65% accuracy, but 40% false positives.

**Decision point:** You stop. Looking at your tree, method naming patterns might provide complementary information. You decide to spend 1 day exploring whether combining both approaches improves accuracy.

**Day 3:** Combined approach: 78% accuracy, 25% false positives. Promising.

**New decision:** Time-box 3 more days to refine and test on larger codebases.

Notice what happened: The 2-day time box forced assessment before perfecting the first approach. You learned combining approaches was better. Without time-boxing, you might have spent a week perfecting complexity metrics alone.

### How to Set Time Boxes

When choosing a branch on your Research Tree, ask: Is this shorter than a day? A few days? Longer than a week?

**Shorter than a day:** Just do it. Don't overthink time-boxing for tasks this short.

**A few days (2-7 days):** Time-box for 2-5 days. I usually time-box for slightly less than my estimate - if I think 4 days, I set 3 days. This forces reflection based on learning, not arbitrary completion.

**Longer than a week:** Time-box for one week maximum. Even if you're making progress, a week is long enough that stepping back is valuable.

![Time box based on your initial estimate](images/chapter05/estimate_to_time_box.png)

Don't overthink the exact duration. The goal is creating natural stopping points. The specific number matters less than having some checkpoint.

**Critical:** Time-boxing is not about pressure. You're not failing if the time box expires without solving the problem. That's expected in Research. What time-boxing does is force moments of reflection that prevent weeks spent on directions you'd have abandoned if you'd stopped to reconsider.

### Using Time-Boxing with Your Team

When managing researchers, set time boxes together during planning. Make sure they understand it's a decision point, not a deadline. Schedule the review explicitly.

At the review, look at the Research Tree together. Ask the three questions. Make the decision collaboratively. This prevents researchers from getting stuck without asking for help, and makes pivoting feel like a positive decision rather than failure.

### Integration with the Research Tree

Time-boxing combines naturally with the Research Tree ([chapter 4](#the-research-tree)): each branch gets a time box, and when it expires, the tree shows your alternatives.

Time-boxing creates moments to ask "given what I've learned, what should I do next?" The Research Tree helps you answer that question.

### Recap

For tasks longer than a day, set a time limit (2-5 days for medium tasks, max 1 week). When time expires, stop and evaluate using your Research Tree: What was my goal? What did I learn? Is this still the best path?

Time boxes acknowledge that research estimation is hard. They prevent sunk cost fallacy and endless exploration. They're not about pressure or finishing "on time" - they're about forcing reflection instead of momentum-driven continuation.

Combined with the Research Tree, time-boxing gives you control over research execution while respecting its inherent uncertainty.
