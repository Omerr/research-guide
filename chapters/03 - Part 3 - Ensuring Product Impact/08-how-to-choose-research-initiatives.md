\newpage

# Part 3 - Ensuring Product Impact {#part3-ensuring-product-impact}

In [chapter 2](#research-and-development), I argued that your role as a Research leader is to:
1. Ensure Research connects to product impact.
2. Ensure Research is done effectively.

Part 2 addressed (2) above - ensuring Research is done effectively - with tools that work in ANY research context. This part provides the complete answer to (1) - ensuring Research connects to product impact:
- First, choose research that matters ([chapter 6](#how-to-choose-research-initiatives)).
- Then, work backwards from product value ([chapter 7](#drawing-backwards)).
- Continuously validate with end-to-end iterations ([chapter 8](#end-to-end)).
- Finally, see how everything integrates ([chapter 9](#integration)).

## Chapter 6 - How to Choose Research Initiatives {#how-to-choose-research-initiatives}

The very first step in making sure your Research impacts the product is choosing the right thing to research, and, just as important - avoiding research that won't impact the product.

Research initiatives can start from two different places:

1. From a problem the product is facing.
2. From a technological opportunity.

### 1. Starting From a Concrete Problem

The most promising way to find research initiatives that will have a big impact on the product is to start from an acute problem that the product is facing. 

At [Swimm](https://swimm.io), we allowed users to write documents about their code, but inevitably, the code changed, and the documentation became outdated. This made writing documentation not worth the effort in the first place. We needed to find a way to make sure the documentation stayed up to date automatically, with a good user experience. This was a clear problem we faced, and we didn't know if it was even possible to solve.

Consider a different example - a medical company that wants to diagnose a disease based on a few blood samples. Currently, they have an algorithm in place, but it's not very accurate. Specifically, it yields too many false positives. They need to find a way to improve their prediction accuracy. This is a clear problem the product is facing, and it doesn't have a clear technological solution.

In both cases, the problem is clear, and its impact on the product or company is clear. At the same time, the solution is not clear, and it's not certain that a solution will be technologically feasible.

### 2. Starting From a Technological Opportunity

When generative AI became popular, many companies started exploring how to leverage it to improve their products. This is an example of an emerging technology that can enable new product features. 

The same can happen with smaller, more specific technologies, and not necessarily new technologies - sometimes technologies that the relevant teams just familiarized themselves with. For example, if a researcher reads a paper about a new way to parse source code, that researcher might have an idea for a new product feature that can leverage this technology.

While many good ideas come from technological opportunities, it's important to remember that the real impact of research is determined by the product, not the technology. It's far more risky to pursue a technological opportunity than a concrete problem. In that case, your responsibility is to make sure that the technological opportunity, if pursued successfully, will indeed have a big impact on the product.

### Problem-Driven vs. Opportunity-Driven: A Comparison

| Aspect | Problem-Driven Research | Opportunity-Driven Research |
|--------|------------------------|----------------------------|
| **Starting Point** | Customer pain point or product limitation | New technology or technique becomes available |
| **Product Impact Clarity** | High - you know exactly what problem you're solving | Low to Medium - you're searching for problems this technology can solve |
| **Risk Level** | Lower - you know there's demand if you succeed | Higher - solution might not match any important problem |
| **Validation** | Problem already validated through user feedback | Needs validation that the solution matters to users |
| **Examples** | Swimm's auto-updating docs; Reducing false positives in medical diagnosis | "How can we use LLMs in our product?"; "This new parsing technique could enable..." |
| **Success Criteria** | Did we solve the problem? | Did we find a valuable use case AND solve it? |

Problem-driven research starts with validated demand. Opportunity-driven research starts with a hammer looking for nails. Sometimes you find valuable nails, but it's riskier.

### Should You Pursue a Research Initiative?

Say you have a research initiative - an idea you'd like to research. To know whether you should pursue it, you should be able to answer a simple set of questions:

**1. Product Impact - If the Research succeeds, how big will the impact be?**

This is the most crucial question. 

For problem-driven research, this is usually straightforward: "If we solve automatic doc updates, we'll retain 40% more customers who currently churn due to outdated docs."

For opportunity-driven research, you need to work harder: "If we use LLMs for code analysis, we could enable X feature, which would help Y users save Z hours per week, translating to $W in additional revenue."

If you're not convinced a successful Research result would make a huge impact on the product, it's probably not worth pursuing at the moment (until you *are* convinced). "Huge impact" means:
- Solving a top-3 customer pain point, OR
- Enabling a new product capability that significantly expands your market, OR
- Reducing a major cost or risk factor

Anything less, and your resources are better spent on Development work with clearer ROI.

**2. Time to Impact - How long until we see product value?**

Time estimation is always hard in software. This is true for Development tasks, and even more so for Research. You learned ways to manage this uncertainty *during* Research in [chapter 5](#time-boxing), but even at this early pre-Research stage, you should consider the timeline.

Ask yourself two related questions:

- **How long for the Research itself?** (days? weeks? months?)
- **How long from successful Research to product impact?** (immediate integration? requires significant Development? needs market validation?)

The total timeline matters because:
- Research that takes 6 months but delivers immediate product value might be worthwhile.
- Research that takes 2 months but requires 8 more months of Development might not be worth it if your product roadmap can't accommodate that.
- Research that takes 1 year with uncertain outcomes probably isn't worth pursuing unless the potential impact is transformational.

Of course, the actual timespans vary greatly by context (and specifically by the company you work for).

Consider also whether you can achieve **incremental value**. Can you get *some* product impact in 3 months even if the full solution takes 9 months? This significantly de-risks longer Research initiatives.

**3. Resources - Do you have what you need?**

Research requires specific resources beyond just "engineering time":

**Knowledge**: Do you have team members familiar with the relevant:
- Technical domain (e.g., NLP, compiler design, distributed systems)?
- Business domain (e.g., medical diagnostics, financial regulations)?
- Similar problems solved elsewhere?

If not, can you acquire this knowledge in reasonable time? (Reading papers for a week: reasonable. Earning a PhD: not reasonable.)

**Capacity**: Can you dedicate someone (or multiple people) for the expected duration? Research requires sustained focus - splitting someone 10% on Research and 90% on urgent product work rarely succeeds.

**Dependencies**: Do you need:
- Access to specific data or systems?
- Collaboration from other teams?
- External expertise or consulting?
- Budget for tools, cloud resources, or datasets?

If critical resources are unavailable or expensive to obtain, the initiative may not be viable.

### Pre-Research Checks

You might not have clear answers to all three questions above. In that case, it makes sense to spend time answering them *before* actually pursuing the Research. This phase should be limited in time - ideally a few days, at most a week or two.

In this stage you might:

1. **Interview customers and business stakeholders** to understand the real impact of solving the problem.
2. **Read about the technological aspects** and previous research done in this field to assess feasibility and timeline.
3. **Consult with people** who have faced similar challenges (internal experts, academic contacts, or practitioners in your network).
4. **Run quick feasibility tests** - not full Research, but simple checks like "Can we even access the data we'd need?" or "Does this library exist in our language?"

After pre-research checks, you should have a clear answer: "Yes, we should pursue this because the impact is X, the timeline is roughly Y, and we have (or can get) the resources we need."

If you're not confident about substantial product impact, *don't start the Research*. This might sound harsh, but it's crucial: unfocused Research that doesn't connect to product needs wastes your most valuable resource - talented engineers' time and attention. One way to enhance your certainty about product impact is described in [chapter 7](#drawing-backwards).

The next chapters assume you understand the product impact of successful Research outcomes, and will help you ensure you actually achieve this impact as quickly as possible.

### How to Choose Research Initiatives - Summary

**Research initiatives** start from either:
- **Problem-driven**: A clear product need (strongly preferred)
- **Opportunity-driven**: A new technology (higher risk)

**Before pursuing Research**, answer three questions:
1. **Product Impact**: Will success create huge value?
2. **Time to Impact**: How long until we see product results?
3. **Resources**: Do we have the knowledge, capacity, and dependencies?

**Run pre-research checks** (days, not weeks) to answer these questions if unclear.

**Only pursue Research** when you're confident about substantial product impact.

The next chapter shows how to maintain that product connection throughout the Research process.