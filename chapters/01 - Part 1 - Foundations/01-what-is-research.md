\newpage

# Part 1 - Foundations

## Chapter 1 - What is Research? {#what-is-research}

To manage research effectively, you first need to understand what research is, and what it is not.

From now on, I will use *Research* (capital R) when refering to our specific concept of research in this book, to distinguish it from general uses of the word.

Consider this scenario: Your team needs to optimize a critical API endpoint. It's slow, users complain, and you know exactly what to do: profile the code, identify bottlenecks, apply standard optimization techniques. This is challenging work, but it's not Research.

Now consider this: Your team needs to automatically extract business rules from 40-year-old COBOL codebases, consisting of millions of lines of code where the original developers are long retired. You're not even sure if extracting these rules automatically is possible. Multiple approaches might work. Or none might. This is Research.

### The Difference

The distinction isn't about difficulty or technical sophistication. It's about **uncertainty of approach**.

**Research** confronts problems where:

- You don't know if a solution exists.
- Multiple approaches might work, but you don't know which.
- The path to success is not immediately clear.
- You may need to invent new techniques.

**Development** involves:

- Applying known techniques to build specific features.
- Following established approaches, even if complex.
- Clear success criteria tied to working software.

I've found Alan Schoenfeld's model of problem solving [1] to be a useful framework for defining and analyzing research. Schoenfeld, studying how people solve mathematical problems, identified four** components that determine success when facing genuinely uncertain problems. His framework applies directly to software Research:

### Schoenfeld's Framework for Problem Solving

**1. Knowledge Base** — What you know

Are you familiar with relevant tools, algorithms, and techniques?

For COBOL business rule extraction: Do you understand COBOL syntax? Static analysis? Program comprehension techniques?

Without the right knowledge, you will have to spend time acquiring it before making progress, and might miss options that could be obvious to someone with more background.

**2. Heuristics** — Strategies for approaching problems

We will cover heuristics in much more detail later. For now, here are some examples of effective heuristics:

- "Work backwards from the desired output".
- "Break the problem into smaller pieces".
- "Try a simpler version first".
- "List all assumptions and test each one".

For COBOL: "Start by manually extracting rules from one small program to understand what 'success' looks like"

**3. Control** — Monitoring and adjusting your approach

Recognizing when your current strategy isn't working. Deciding when to pivot to a different approach. Managing your time and resources effectively.

This is what separates experienced researchers from novices - it's not just what you know, but when and how you use it.

**4. Beliefs and Attitudes** — Your mindset toward the problem

Schoenfeld found that successful problem solvers held certain beliefs that helped them persist through challenges. Examples include:

- "I can figure this out" vs. "I'm not good at this kind of thing".
- "Problems have multiple solutions" vs. "There's one right answer".
- "I should write things down and work systematically" vs. "I should solve this in my head".

These beliefs profoundly affect your ability to persist and succeed.

### Why This Matters for R&D Leaders

You've likely seen this: A capable engineer spends three weeks on a Research task, trying approach after approach, until the original problem is no longer relevant. Or they declare after two days "it's impossible" and give up, though it turns out later that the problem was actually solvable.

The issue isn't (necessarily) capability. It's that Research requires different management, and different skills, than Development:

- **Knowledge base**: Did they have the right background, or access to people who did?
- **Heuristics**: Were they using effective problem-solving strategies, or just "trying things"?
- **Control**: Did they know when to pivot? When to ask for help? When to break the problem down differently?
- **Beliefs**: Did they believe the problem was solvable? That systematic approaches work better than random attempts?

**The good news**: All four components can be improved. People get better at Research through practice, exposure to effective heuristics, and environments that support good Control and healthy Beliefs.

The rest of this book provides concrete tools, like using a Research Tree, structured brainstorming, and time-boxing methods, that put Schoenfeld's framework into action in a Product-led environment. These tools help you and your team apply better heuristics, maintain effective control, and build the beliefs that sustain successful Research.

But first, let's make sure we're clear on when you actually need these tools. [The next chapter](#Research-and-development) dives deeper into distinguishing Research from Development work.

### Notes
** Actually, Schoenfeld (1992) described five components (which he terms "categories"), but I focused on four of them.

### References

[1] Schoenfeld, A. H. (1992). Learning to think mathematically: Problem solving,
metacognition, and sense-making in mathematics. In D. Grouws (Ed.), Handbook for
Research on Mathematics Teaching and Learning (pp. 334-370). New York: MacMillan.
