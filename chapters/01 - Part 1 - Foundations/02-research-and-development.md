\newpage

## Chapter 2 - Research and Development {#research-and-development}

Most R&D departments have plenty of Development work. Everyone agrees on what Development is. But Research? That's murkier.

Some claim every development task involves "research" - you have to test your code, try different things, read documentation. Is this Research?

Let's be precise.

### Using Schoenfeld's Framework to Distinguish

Schoenfeld defined problem solving as "applying knowledge to overcome obstacles and reach a goal **where a direct solution path is not immediately obvious to the solver.**"

Applying this to software:

**Research** involves fundamental uncertainty:

- You don't know if a solution is even possible.
- Multiple approaches exist, but you don't know which will work for your specific problem.
- You may need to invent entirely new techniques.
- Success means establishing new capabilities, not implementing specific features.

**Development** involves:

- Applying established techniques to build products.
- Following known approaches, even if complex to implement.
- Success tied directly to working software with specific capabilities.

### A Quick Test

You're asked to reverse-engineer a specific compiled function - disassemble it and provide the C equivalent. You know assembly, you know C, you have a disassembler. Is this Research?

**No.** You know how to proceed. It might take three days of careful work, especially if the function is complex, but it's not Research. You're applying known techniques.

But if you need to understand how an entire program operates, and one *possible* approach is reverse engineering its compiled form, and you're not sure if that approach is even feasible time-wise or whether it will yield the insights you need? **That's Research.**

### Key Indicators You're Doing Research

**1. Fundamental Uncertainty About Solution Viability**

You're asking "Can this even be done?" rather than "How should we do this?" This isn't about implementation details. Rather, it's about whether the approach itself is viable.

**2. Multiple Competing Approaches Without Clear Superiority**

Research often means exploring several paths simultaneously, knowing many will fail, to discover which approach (if any) can solve the problem.

**3. Need for New Fundamental Techniques**

You may need to invent new methods rather than adapting existing ones. Note: Not all Research creates new techniques, but the possibility exists.

### Common Misconceptions

**Misconception 1: Technical Complexity = Research**

Many challenging Development tasks involve sophisticated algorithms, large-scale systems, or cutting-edge technologies without requiring Research approaches.

Building a distributed system with complex consensus algorithms? Challenging Development. Figuring out whether a distributed system *can* meet your latency requirements given your unusual constraints? Might be Research.

**Misconception 2: Using Advanced Algorithms = Research**

Implementing machine learning pipelines with random forests or neural networks isn't Research - even though the underlying algorithms are sophisticated. The Research happened when those algorithms were first developed.

**Misconception 3: Research Can Be Managed Like Development**

Perhaps the most damaging misconception. This leads to:

- Demanding precise time estimates for uncertain work.
- Expecting steady, measurable progress on fixed schedules.
- Evaluating Research with Development metrics.

Research requires different approaches. This is exactly what the rest of this book addresses.

**Misconception 4: Research Cannot Be Managed**

The opposite extreme: treating Research as mystical work by brilliant people. The best a manager can do is not interrupt.

I've had the pleasure and privilege to work with many extremely skilled researchers. I can confidently say that this is simply not the case, as even the most talented researcher can benefit from skillful guidance.

Specifically, even the most talented researcher benefits from:

- Clear connections between their work and product goals.
- Structured approaches to exploring alternatives.
- Regular checkpoints to assess direction.
- Team collaboration and brainstorming.

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

The rest of this book provides concrete tools for both responsibilities.
