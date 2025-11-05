\newpage

## Chapter 2 - Research and Development {#research-and-development}

Most R&D departments have plenty of Development work. Everyone agrees on what Development is. But Research? That's murkier.

Some claim every development task involves "research" - you have to test your code, try different things, read documentation. Is this Research?

Let's be precise.

### Defining Research vs. Development
As a reminder from [chapter 1](#what-is-research),

**Research** involves fundamental uncertainty:

- You don't know if a solution is even possible.
- Multiple approaches exist, but you don't know which will work for your specific problem.
- You may need to invent entirely new techniques.
- Success means establishing new capabilities, not implementing specific features.

**Development** involves:

- Applying established techniques to build products.
- Following known approaches, even if complex to implement.
- Success tied directly to working software with specific capabilities.

![Research vs Development](images/chapter01/research_vs_development.png)

### A Quick Test

You're asked to reverse-engineer a specific compiled function - disassemble it and provide the equivalent code in C language. You know assembly, you know C, you have a disassembler. Is this Research?

**No.** You know how to proceed. It might take three days of careful work, especially if the function is complex, but it's not Research. You're applying known techniques, and know how to progress to a solution.

But if you need to understand how an entire program operates, and one *possible* approach is reverse engineering its compiled form, and you're not sure if that approach is even feasible time-wise or whether it will yield the insights you need? **That's Research.**

### Key Indicators You're Doing Research

**1. Fundamental Uncertainty About Solution Viability**

You're asking "Can this even be done?" rather than "How should we do this?" This isn't about implementation details – rather, it's about whether the approach itself is viable.

**2. Multiple Competing Approaches Without Clear Superiority**

Research often means exploring several paths simultaneously, knowing that many will fail, to discover which approach (if any) can solve the problem.

**3. Need for New Fundamental Techniques**

You may need to invent new methods rather than adapting existing ones. Note: Not all Research creates new techniques, but the possibility exists.

![Research definition](images/chapter01/research_definition.png)

### Common Misconceptions

**Misconception 1: Technical Complexity = Research**

Many challenging Development tasks involve sophisticated algorithms, large-scale systems, or cutting-edge technologies without requiring Research approaches.

Building a distributed system with complex consensus algorithms? Challenging Development. Figuring out whether a distributed system *can* meet your latency requirements given your unusual constraints? Might be Research.

Technical complexity is not the same as Research.

![Technical complexity is not the same as Research](images/chapter02/technical_complexity_neq_research.png)

**Misconception 2: Using Advanced Algorithms = Research**

Implementing machine learning pipelines with random forests or neural networks isn't Research - even though the underlying algorithms are sophisticated. The Research happened when those algorithms were first developed. However, if you are using those algorithms when trying to solve a problem where it's unclear if they will work at all, that could be Research.

![Using Advanced Algorithms is not the same as Research](images/chapter02/advanced_algorithms_neq_research.png)

**Misconception 3: Research Can Be Managed Like Development**

Perhaps the most damaging misconception. This leads to:

- Demanding precise time estimates for uncertain work.
- Expecting steady, measurable progress on fixed schedules.
- Evaluating Research with Development metrics.

Research requires different approaches. This is exactly what the rest of this book addresses.

![Managing Research is different from Managing Development](images/chapter02/managing_dev_neq_managing_research.png)

**Misconception 4: Research Cannot Be Managed**

The opposite extreme: treating Research as mystical work by brilliant people. The best a manager can do is not interrupt.

I've had the pleasure and privilege to work with many extremely skilled researchers. I can confidently say that this is simply not the case, as even the most talented researcher can benefit from skillful guidance.

Specifically, even the most talented researcher benefits from:

- Clear connections between their work and product goals.
- Structured approaches to exploring alternatives.
- Regular checkpoints to assess direction.
- Team collaboration and brainstorming.

Research is not magic, it *can* be managed effectively.

![Research is not magic, and it can be managed](images/chapter02/research_neq_magic.png)

### Your Role as Research Leader

When leading Product-led Research, your job has two parts:

**1. Ensure the Research makes the biggest possible impact on the product**

This is your most important responsibility. "Successful" Research that doesn't impact the product is a failed project. Your job is to maintain the connection between Research work and product value - not just at the start, but continuously.

This means:

- Starting with clear product needs, not interesting technical questions.
- Regularly validating that the Research still serves the product goal.
- Making trade-offs between thorough exploration and shipping impact.

(We'll cover this in detail in [Part 3](#part3-ensuring-product-impact).)

**2. Ensure the Research is done in the most effective manner**

Even brilliant researchers benefit from structured approaches. Your role is to help the team work systematically rather than randomly.

This means:

- Helping identify which questions are worth answering.
- Introducing better heuristics when the team is stuck ("Let's work backwards," "Let's time-box this investigation").
- Preventing common failure modes like endless exploration or premature commitment.

(We'll cover this in detail in [Part 2](#part2-research-management-methods).)

Responsibility (1) is defining the right goals.
Responsibility (2) is reaching these goals effectively.

The rest of this book provides concrete tools for both responsibilities.

![](images/chapter02/lead_goals.png)
