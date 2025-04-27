\newpage

## Chapter 2 - Research and Development {#Research-and-development}

In most organizations, there is a department called R&D. In software organizations, these usually consist of developers, or engineers. R&D stands for Research and Development. In most R&D departments, the D(evelopment) is clear - the teams have clear goals to accomplish, usually represented by tickets in a task management system. The developers write code, test it, ship it.

But what about the R(esearch) part of R&D? There seems to be some confusion there. Some would claim that every development task involves some "Research" - you have to test your code and perhaps try differnet things.

Is this Research?

I am not as concerned with semantics here, but most people can also differntiate the process of a Development task (which consists of trial-and-error, reading others' code and so on), from "deep" Research - where the problem the person is facing does not have a clear answer.

All software organizations have Development tasks. All of them. With R(esearch), this is different. Some organizations have a lot of Research tasks, some have none. In some organizations there are even Research teams, and in some - only few people get assigned those mystical tasks.

So what is really Research in R&D organizations? And how is it different from Development? Does this distinction matter?

In [chapter 1](#problem-solving), you got to know Schoenfeld's model of problem solving, and how it can be applied to Research tasks. In this chapter, we will use this model to distinguish Research from Development.

Schoenfeld defines problem solving as "the process of applying knowledge to overcome obstacles and reach a goal where a direct solution path is not immediately obvious to the solver." 

If we apply Schoenfeld's definition to distinguish Research from development in software, things become clearer:

**Research** in software involves confronting problems where:
- You don't know if a solution is even possible
- Multiple approaches might exist, but you do not know which approach will prove effective for your specific problem
- You may need to invent entirely new algorithms, methods, or techniques
- Success often means establishing new capabilities rather than implementing specific features

Throughout this book, I will relate to such tasks, and the R in R&D in general, as "Research" (with a capital R).

**Development**, by contrast, involves:
- Applying established techniques to build specific products or features
- Following known approaches, even if they're complex to implement
- Focusing on efficient implementation rather than proving fundamental concepts
- Success criteria tied directly to working software with specific capabilities

This distinction isn't always clear-cut, but it helps us differentiate Research from Development in most cases. For example - consider I gave you a task of reverse engineering a specific function. The function is implemented in Assembly, and you need to provide the C language equivalent. You know how to use a disassembler to read the Assembly code, and you know both Assembly and C. Is this Research?

According to the proposed definition - no. You know how to proceed. It might be a difficult task, especially if this function is long and convoluted, but it's still not Research. If you were to understand something about how a program operates, and one of the approaches was reversing its compiled form, and you weren't sure whether reversing it would work (or is feasible time-wise), that would be Research.

Note that I do not claim that Research is more important than Development. I do not claim that Development is more important than Research. I claim that Research and Development are different, and that they need different approaches.

## Distinguishing Research from Advanced Development

Is your team engaged in genuine Research, or just tackling complex Development work? This distinction isn't merely semantic. This distinction matters because Research and Development need different:
- Timeframes and milestone structures
- Success metrics and evaluation methods
- Team compositions and skill sets
- Management approaches

In this section, I'll help you discern the difference and address common misconceptions.

Building on Schoenfeld's problem-solving model, you can identify several key indicators that an activity genuinely requires a Research approach:

### 1. Fundamental Uncertainty About Solution Viability

The most reliable indicator of Research is fundamental uncertainty about whether a solution is possible at all. When your team is asking "Can this even be done?" rather than "How should we do this?" you're likely in Research territory.

This uncertainty isn't about implementation details or technical complexity—it's about the fundamental feasibility of an approach.

If you consider the spiral game from [chapter 1](#problem-solving), in case you encounter this problem and do not know whether you can find a solution where you *guarantee* that you win every time, then this is a Research problem.

### 2. Multiple Competing Approaches Without Clear Superiority

Another indicator is the presence of multiple potential approaches with no clear evidence about which will succeed. Research often involves exploring several paths simultaneously, knowing that many will fail, to discover which approach (if any) can solve the problem.

In Development work, you typically know which approach to take from the outset, even if multiple options exist. In Research, you're genuinely exploring different approaches because the current state of knowledge doesn't provide clear guidance.

### 3. Need for New Fundamental Techniques or Algorithms

Research often requires inventing entirely new techniques, algorithms, or methods rather than adapting existing ones. The key question is whether you need to create fundamentally new approaches or can accomplish your goals by applying and adapting known solutions. Note that not all Research tasks would inlvolve new fundamental techniques, but it is hard to tell whether they will.

## Common Misconceptions About Research in Software Companies

Several misconceptions about Research persist in software companies, leading to misaligned expectations and inappropriate management approaches:

### Misconception 1: Technical Complexity Equals Research

Perhaps the most common misconception is equating technical complexity with Research. Many challenging Development tasks involve sophisticated algorithms, large-scale systems, or cutting-edge technologies without requiring Research approaches.

### Misconception 2: Using Advanced Algorithms Is Research

Another misconception is that implementing sophisticated algorithms constitutes Research. While the original development of these algorithms was Research, applying them—even with modifications for your specific context—is typically development work.

For instance, implementing a machine learning pipeline using established methods like random forests or neural networks isn't Research, even though the underlying algorithms are sophisticated. The Research happened when these algorithms were first developed and their properties established.


### Misconception 3: Research Can Be Managed Like Development

Perhaps the most damaging misconception, as it has direct practical implications, is that Research can be managed using the same processes and timelines as Development work. This leads to inappropriate expectations and frustration for both Researchers and business stakeholders.

Research requires different approaches as I'll explore in later chapters.

### Misconception 4: Research Cannot Be Managed

Another claim I encountered is that Research cannot be managed at all. It is a mystical task performed by extremely talented people. The best a manager can do is not interrupt.

I had the pleasure and privilege to work with many extremely skilled researchers. I can confidently say that this is simply not the case, as even the most talented researcher can benefit from skillful guidance.

## Summary

In this chapter, TBD
In the next chapter, TBD