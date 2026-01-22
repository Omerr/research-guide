\newpage

## Chapter 8 - End-to-End Iterations {#end-to-end}

Your most important role is ensuring that Research impacts the product. One major risk: spending weeks on research questions that seem vital, only to discover they don't actually impact the product.

In [chapter 7](#drawing-backwards), I advocated for drawing backwards - starting from product impact and working your way back to research questions. This is indeed powerful, especially because it forces you to focus on the end result and validate it with users.

But drawing backwards alone has limitations. Two risks emerge:

**Risk 1: Infeasibility in practice**
Your manually-created "ideal output" might be technically infeasible or impossibly expensive to generate. You won't discover this until you try to build it.

**Risk 2: Lack of real-world validation**
Since you haven't completed an end-to-end process, you probably haven't run your solution on clients' actual data (assuming you can't access it during the manual phase). Continuing our COBOL example from the previous chapter, what works on carefully-chosen examples might fail on real codebases.

These two risks are why I advocate for **continuous end-to-end iterations**.

\newpage

### Drawing Backwards + End-to-End: A Combined Approach

These aren't competing approaches - they're complementary:

| Heuristic | Purpose | What It Gives You | Strength | Limitation |
|----------|---------|-------------------|----------|------------|
| **Drawing Backwards** ([chapter 7](#drawing-backwards)) | Define target and path | 1. Target output\ 2. Hypothesized chain of steps to get there\ 3. Order of dependencies | Ensures product focus; reveals what you need to build | Hypotheses may be wrong; doesn't validate feasibility on real data   |
| **End-to-End Iterations** (this chapter) | Validate and build incrementally | 1. Proof the chain works\ 2. Learning from real data\ 3. Prioritized improvements | Validates feasibility; discovers what actually works | Can lose direction without clear target and chain |

![These are complementary heuristics](images/chapter08/heurstics_comparison.png)

\newpage

**The recommended flow:**

1. Use drawing backwards to:
   - Define your target output (manually create examples, validate with users).
   - Identify the chain of intermediary steps needed to produce that output.
   - Understand the order of dependencies.
2. Switch to end-to-end iterations to:
   - Test whether your hypothesized chain actually works.
   - Validate on real data (not just your manual examples).
   - Incrementally build toward the target.
3. Throughout iterations, keep both the target AND the chain from step 1 as your guide.

Drawing backwards already outlines your end-to-end process (Principle 1 below). End-to-end iterations validate and build that process incrementally, learning what works and what doesn't.

### The Five Principles of End-to-End Iterations

The end-to-end approach relies on five principles:

1. Outline the end-to-end process.
2. Get to end-to-end by simplifying.
3. Ship it as fast as you can.
4. Gradually replace steps.
5. Get frequent feedback on results.

Let me explain each principle using the COBOL business rules example from [chapter 7](#drawing-backwards). Since this book isn't about COBOL, I'll keep explanations short while focusing on the methodology.

![The five principles of end-to-end iterations](images/chapter08/e2e_principles.png)

### Principle 1: Outline the End-to-End Process

Start by outlining the entire process from input to output. More accurately, outline the *hypothesized* end-to-end process - you can't know for certain until you test with users.

**If you followed drawing backwards from [chapter 7](#drawing-backwards), you already have this.** Drawing backwards naturally produces this chain: you started with the target output, asked "what do I need to produce this?", then "what do I need for that?", working your way back to the starting input. That chain IS your end-to-end process outline.

For the COBOL business rules example: We used drawing backwards to identify that our document needed business rule sections, which meant we needed to explain conditions, which meant we needed to filter business conditions, which meant we needed to find conditions, which meant we needed to parse COBOL. Working backwards gave us this chain:

1. Start with a COBOL program.
2. Parse the COBOL program into an Abstract Syntax Tree (AST).
3. Traverse the AST to find conditions.
4. Filter out business-related conditions (vs. technical conditions).
5. For every business rule, create a document section explaining the condition.
6. Sort document sections according to business rule dependencies.

This is your first draft: the hypothesized process that drawing backwards revealed.

![First end-to-end process draft](images/chapter08/cobol_steps.png)

**How to outline:**

- Draw boxes on a whiteboard.
- Use a flowchart if the process isn't linear.
- Keep it visible throughout the research.
- Update it as you learn.

The outline serves as your map - it shows you where you are and what you're building toward.

### Principle 2: Get to End-to-End by Simplifying

Your goal: make the process work end-to-end. Start with input (a COBOL program), reach the output (a document with business rules), while passing through the intermediate stages.

This sounds like too much. Don't you need to complete the whole research to achieve this?

**Definitely not.** The trick is to find the easiest way to get end-to-end by taking shortcuts and making assumptions that are definitely too generous for production. You should fight your inner engineer who wants to "do it right" from the start. Your goal is to get an end-to-end process working, as this heuristic is far more valuable than perfecting one step.

This means that some of the steps can be completed manually, or with very simple implementations that you know won't work in production. Remember it is an intermediate milestone, not the final product.

For our COBOL example:

- Start with a single, known COBOL program.
- **Skip parsing** - just manually write a list of conditions for the next stage.
- The filtering function returns `true` if business-related, `false` otherwise.
  - First implementation: a simple mapping between input conditions (that you know of) and whether to return `true` or `false`.
  - Alternative: always return `true` - yes, you'll get non-relevant rules, but that's a problem for *later*.
- The document generation might also be manual for the first pass.

![With shortcuts, we get to an end-to-end process quickly](images/chapter08/cobol_steps_shortcuts.png)

**End result:** A rough-looking document, generated by a combination of manual work and code that works solely on a single program. This is far from shippable, but it's an extremely important milestone for ensuring research impacts the product.

You might argue that it's overkill, and why waste this time on manual steps when you'll need to automate them eventually? Even if you don't, I promise from experience that many researchers and engineers feel that way. 

From my own experience, I learned (the hard way) that this pays off. Getting to a working end-to-end makes sure you:

- Validate that the entire flow works.
- Identify bottlenecks and blockers early.
- Have something concrete to show and get feedback on.
- Prevent spending months on one component that turns out to be unnecessary.

### Principle 3: Ship It as Fast as You Can

By the end of Principle 2, you have a working end-to-end process for a single case. You definitely can't ship it yet - it only works on one specific program, certainly not the client's program.

**Next milestone: make it shippable.**

Does "shippable" mean it works on *any* program? That's too hard and takes too long. **You need shortcuts.**

This is where creativity matters. For our COBOL example:

**Information gathering:**

- If running on a client's program, get as much information as possible.
- Perhaps assume it's less than 1,000 lines of code.
- Perhaps you know which COBOL dialect the client uses, so you don't need to support others (fun fact: [COBOL has more than 300 dialects](https://www.cs.vu.nl/grammarware/500/500.pdf). Well, it's fun for you, not for those who need to support them). 

**Algorithmic shortcuts:**

- Use regular expressions to find conditions instead of a full parser.
- Yes, you'll miss some conditions - that's a problem for *later*.

**UX shortcuts:**

- Skip the document generation. Just print rules to the console.
- Run from the command line without a GUI.
- Manual configuration file instead of user interface.

**Your goal is clear: ship it.**

It doesn't need to be perfect. It needs to be enough to learn from this iteration. If you don't ship, you can only learn from your intuition - a very bad idea.

Unlike in Principle 2, note that here you don't generate an output (partially) manually - you need a working software that can run on real data.

**What "shippable" means:**

- Works on the client's actual data (even if imperfectly).
- Produces output you can get real feedback on.
- Doesn't require your manual intervention for each run.

**What "shippable" doesn't mean:**

- Perfect accuracy.
- Handles all edge cases.
- Production-quality code.
- Beautiful user interface.

You can't ship just *anything*, though. In our example, if you only have a solution that works on one specific test program you created, generating an irrelevant document for the client wastes time and teaches you nothing.

You can't learn from iteration without shipping. And you can't ship without a working end-to-end process. I know it sounds obvious, but many teams miss this in practice as they get into the rabbit hole of solving one step "the right way" before validating the entire flow.

### Principle 4: Gradually Replace Steps, While Carefully Prioritizing

Now you have a working end-to-end process. You can start replacing various steps' implementations with better ones:

- Replace manual steps with automated ones.
- Remove shortcuts and add more robust implementations.
- Improve accuracy and coverage

After shipping, you'll have many things you think you *must* replace immediately. But remember: the goal is making research impact the product. To do that, you need careful prioritization.

**The Prioritization Framework**

Prioritize changes based on three criteria:

**1. Learned Necessity**
Did you learn that something doesn't work in the current implementation and **must** be fixed for the product to be viable?

*Example: "Regular expressions miss nested conditions, and 60% of the client's business rules are in nested conditions. We must use a real parser."*

**2. Learning Potential**
Will changing this implementation help you learn more about product impact in the next iteration?

*Example: "If we improve the filtering accuracy from 40% to 80%, we'll learn whether the document format is actually useful when it contains mostly-correct content."*

**3. Effort Estimation**
How much time will this change take?

*Example: "Building a full parser: 3 weeks. Improving regex to handle nested conditions: 2 days. The latter gives us 80% of the value for 10% of the effort."*

Continuing with our COBOL example, you may consider and prioritize these changes following the first iteration:

```
Changes after first iteration:

- Fix parser to handle nested conditions [Learned: Critical, 2 days] → DO FIRST
- Add GUI for document generation [Nice-to-have, 1 week] → DEFER
- Improve filtering accuracy [Learning: Critical, 3 days] → DO SECOND  
- Support additional COBOL dialects [No evidence needed, very long time...] → DEFER
- Better document formatting [Client mentioned it, 1 week] → DEFER (validate content first)
```

Iterate fast: change something, ship again, get feedback. Don't solve every issue you find, even issues clients mention. Ask: "What's the most important thing to change to learn something in the very next iteration?"

### Principle 5: Get Frequent Feedback on Results

The trick is to be obsessed with getting as much feedback as you can, on each and every iteration.

**On each iteration:**

1. **Get feedback on the end result**
   - Show the actual output to users.
   - When applicable, don't just ask "does this work?" - also watch them try to use it.
   - Identify what works, what doesn't, what's missing.

2. **Understand the next questions to answer**
   - What did you learn about product impact?
   - What assumptions were validated or invalidated?
   - What new questions emerged?

3. **Plan the next iteration accordingly**
   - Use the prioritization framework above.
   - Focus on learning, not building.

4. **Implement minimal changes to answer questions**
   - Don't fix everything.
   - Make the smallest changes that will answer your next most important question.
   - Keep the cycle fast (days to weeks, not months).

**Example iteration cycle:**

```
Iteration 1:
- Shipped: Regex-based condition finder, always-true filter, console output.
- Learned: Document structure works, but too many false positives (noise).
- Question: Is filtering accuracy the blocker to usefulness?
- Next: Improve filtering to 80% accuracy, ship again.

Iteration 2:
- Shipped: Same regex finder, smarter filtering (80% accurate), console output.
- Learned: With better filtering, users found the output useful!
- Question: Do we need a parser, or is regex sufficient?
- Next: Test on larger programs to see where regex breaks down.

Iteration 3:
- Shipped: Same pipeline, tested on 10 real programs.
- Learned: Regex fails on 4/10 programs (nested conditions).
- Question: Parser worth the investment now?
- Next: Build parser for nested conditions, ship again.
```

Notice: Each cycle is fast, focused on one question, and based on real learning.

In real life, you may want to tackle a few questions per iteration. If two things are clear, fix them before shipping again so you can actually gain valuable feedback rather than hearing the same complaints.

Also, when working with real clients, they might not be as receptive to trying things so many times - so you'll need to consider that aspect as well. Regardless, the key remains the same: keep cycles short and focused on learning.

\newpage

### Integration with Other Tools

End-to-end iterations work best when combined with other research management tools:

**Research Tree ([chapter 4](#the-research-tree)):**

- The outlined process becomes a branch in your tree.
- Each iteration tests different approaches on branches.
- Failed iterations mark branches red, successful ones mark green.

**Time-boxing ([chapter 5](#time-boxing)):**

- Time-box each iteration.
- If you can't ship in the time box, you're building too much.

**Drawing Backwards ([chapter 7](#drawing-backwards)):**

- Drawing backwards ([chapter 7](#drawing-backwards)) defines both:
  - The target output.
  - The hypothesized chain of intermediary steps to reach it.
- End-to-end iterations test whether that chain actually works on real data.
- The target from drawing backwards acts as your north star throughout iterations.
- Each iteration validates or refines the steps that drawing backwards identified.
- Use both: drawing backwards reveals what to build, while end-to-end iterations prove it works and let you test it incrementally.

### Summary: End-to-End Iterations

**End-to-end iterations** ensure Research impacts the product by continuously validating feasibility and learning from real data.

**The five principles:**

1. **Outline the process**: Draw backwards already gives you this: the chain from input to output.
2. **Simplify to get end-to-end**: Use shortcuts and manual steps to make the whole chain work.
3. **Ship fast**: Real data teaches what theory can't.
4. **Prioritize carefully**: Use the three-criteria framework:
   - Learned necessity (is it broken?)
   - Learning potential (what will you learn?)
   - Effort estimation (how long will it take?)
5. **Get frequent feedback**: Fast cycles (days to weeks) focused on learning.
