\newpage

## Chapter 7 - Drawing Backwards {#drawing-backwards}

So you've chosen a research initiative, and done so correctly (following [chapter 6](#how-to-choose-research-initiatives)). Now, how do you start working on it?

Most teams start by diving into technical challenges: parsing COBOL, building callgraphs, implementing algorithms. But there's a more powerful approach that ensures your Research actually impacts the product: **start from the end and work backwards**.

This heuristic - working backwards from your goal - is one of the most valuable problem-solving strategies you can use. Let me show you why with a simple game.

### The Spiral Game

Consider this game:

![https://photos.google.com/search/atlanta/photo/AF1QipPIoGfmBHOSGdzd1MtAeSiGF-Wgs2AlHIR8-DAa](IMAGE: A spiral board numbered from 1 to 41, with a duck token on spot 41)

The rules are simple:
- The duck starts on spot 41.
- On each turn, a player moves the duck backward between 1 to 6 spots. That is, if the duck is on spot 41, you can move it to any spot from 35 to 40.
- The player who moves the duck to spot 1 wins.

Take a moment: If you go first, how would you play to guarantee a win?

Most people start thinking from the current position (spot 41) and try to calculate forward: "If I move 3 spaces, they can move 2, then I can move 4..." This quickly becomes overwhelming - too many possible moves to track.

But if you **work backwards**, the solution becomes clear:

**Starting from the end (spot 1):**
- To win, you need the duck on spot 1 on your turn.
- Your opponent just moved, so the duck could be on spots 2-7 (since they moved 1-6 backward from wherever it was).
- For any spot from 2-7, you can move directly to spot 1.
- **Conclusion**: If the duck is on spots 2-7 at the start of your turn, you win.

**Continue working backwards (from spots 2-7):**
- You want your opponent to *not* be able to land on spots 2-7.
- From spot 8, no matter what they do (move 1-6), they land on spots 2-7.
- **Conclusion**: If you get the duck to spot 8, you guarantee a win.

**Continue working backwards from spot 8:**
- Spots 9-14 all allow moving to spot 8.
- So if your opponent starts their turn with duck on 9-14, you can force it to 8.

**The pattern emerges:**
- Safe spots for you: 1, 8, 15, 22, 29, 36
- From any of these, your opponent cannot avoid giving you another safe spot
- These are all numbers of the form: `1 + 7n`

**The winning strategy:**
- From spot 41, move 5 spots backward to reach spot 36 (a "safe spot").
- No matter what your opponent does, you can always move to the next "safe spot".
- Eventually, you reach spot 1 and win.

Notice what happened: By working backwards from the goal, you discovered the systematic solution. Working forward from the start position would have been much, much harder.

### How to Apply Drawing Backwards to Research

Let's connect this to Product-led Research. When you face a complex Research challenge, the question isn't "What technical problem should I solve first?" but rather:

**"If the Research succeeds, what would the result look like?"**

This forces you to:
1. **Connect to product impact** - You must envision the end state that creates value.
2. **Work systematically** - Like the spiral game, you identify the chain of dependencies backward.
3. **Validate assumptions** - Before solving sub-problems, ensure they lead to your goal.

Let me show you how this worked in practice at Swimm.

### Case Study: Extracting Business Rules from COBOL

At Swimm, we wanted to automatically generate documents from COBOL codebases that included all the extracted business rules.

**Quick context on business rules:** Business rules are the constraints, conditions, and actions embedded within software that reflect organizational policies. For example, in money transfer logic:
- A customer cannot transfer more than their available balance (overdraft limits notwithstanding).
- High-value transfers require additional verification.
- Cross-currency transfers must apply current exchange rates.

Some sources define business rules with three elements: Event, Condition, Action:

```
ON <Event>
IF <Condition>
THEN <Action>
ELSE <Action>
```

Our goal was to extract all business rules from a COBOL codebase. While challenging in any codebase, it's particularly acute in legacy COBOL code. (If you're interested in the technical details, see [this post](https://swimm.io/blog/blackbox-to-blueprint-extracting-business-logic-from-cobol-applications).) For this book, it's sufficient to know that many research attempts over the last few decades have tried different approaches to face this challenge.

#### Where Do You Even Start?

Faced with this problem, you might think:
- "Should I build a callgraph of all functions? That means I need to parse COBOL code..."
- "Should I create a COBOL parser first?"
- "Maybe I should read academic papers about program comprehension?" (Good practice during the pre-Research checks phase from [chapter 6](#how-to-choose-research-initiatives))
- "Perhaps I should track COBOL variables through the codebase?"
- "Should I distinguish business conditions ('if requested transfer amount > available balance') from technical conditions ('if variable not initialized, show error')?"

Each of these might require its own research effort. Where do you start?

#### Drawing Backwards: Start with the End Result

Drawing backwards made us ask:

**"If the Research succeeds, what would the result look like?"**

When we first asked ourselves this question, we weren't sure. We knew from our clients that they wanted extracted business rules, but we couldn't know what the "ideal" output would look like.

So we decided, **before tackling any technical challenges**, to manually create documents showing extracted business rules from sample programs. We did this completely manually - no parsing, no algorithms, just understanding COBOL code ourselves and writing documentation.

We did this for various types of applications from different codebases, and learned:
- There's no single "right" way to construct such a document.
- The output structure differs from one program to another.
- Certain patterns appear consistently across business logic.

By creating these documents manually, we formed a hypothesis: **"This is what the output should look like, which means this output would make the biggest impact on the product. This is our north star."**

But was it actually the north star?

#### Validating the Hypothesis

Once we manually wrote the documents, it was time to verify our hypothesis. With concrete output in hand, we could:
1. Discuss internally within the team - get feedback from engineers who understand both COBOL and our product.
2. Reach out to clients - show them the actual output and ask: "Does this solve your problem?"

We deliberately **refrained from solving hard technological challenges** before knowing where we were aiming.

#### Working Backwards Through Sub-Problems

The manual documents also gave us something crucial: a concrete example to analyze backwards.

For instance, we saw that our documents listed many conditions. This made us realize we would (most probably) need to:

1. **Find conditions** in the code.
2. **Filter out business-related conditions** (vs. technical conditions).
3. **Explain the condition** in the document.

**Here's where drawing backwards becomes powerful:** We tackled (3) before (2), and (2) before (1).

Why? Because we needed to solve (3) to reach our goal - creating impactful documents.

This means we **mocked the first two steps** - we assumed we already had a way to find conditions and filter business-related ones. So we already had our list of business conditions, and now the challenge was: for each condition, explain it clearly in the output document.

This approach prevented us from spending weeks on tasks (1) and (2), only to discover that our explanation approach (3) didn't actually work. If we can't accomplish (3) assuming (1) and (2) are solved, then perhaps this entire approach isn't viable, and we need to reconsider alternatives.

The logic is clear: While solving (3) ultimately requires solving (1) and (2), if we fail at (3) even with (1) and (2) accomplished, then pursuing (1) and (2) might not be worth the effort at all.

### Why Drawing Backwards Is So Powerful

The advantages of drawing backwards become clear from both the game examples and the COBOL case study:

**1. Forces Connection to Product Impact**

Like working backwards from spot 1 in the spiral game, starting with "what does successful output look like?" forces you to think about end-user value. You can't start drawing backwards without a clear goal. This prevents the common failure mode of technically interesting Research that doesn't impact the product.

**2. Provides a System for Progressing**

When Research seems like a huge, daunting task with endless options, working backwards gives you a systematic approach. Just as the spiral game became trivial once you worked backwards to identify the safe spots (1, 8, 15, 22...), Research becomes more manageable when you work backwards from the desired output to identify the dependencies.

**3. Validates Each Step Before Investment**

Working backwards lets you validate that each sub-problem actually contributes to your goal before you invest significant effort. In the COBOL example, we could verify that our explanation approach (step 3) worked before spending weeks on finding and filtering conditions (steps 1 and 2).

### Practical Application: Your Research Tree

Drawing backwards integrates naturally with the Research Tree from [chapter 4](#the-research-tree). When you create your tree:

**Start with the end:**
- Root of tree: "Generate impactful business rule documentation".
- First question: "What should successful output look like?"
- Approach: Create manual examples.

**Then work backwards:**
- Once you have output, ask: "What do we need to produce this?".
- This reveals the actual sub-questions and their dependencies.
- Each branch represents a prerequisite you need to solve.

**Validate before going deeper:**
- Before pursuing any branch deeply, ask: "If I solve this, does it actually get me closer to the goal?"
- Mock out dependencies to test approaches cheaply.
- Use time-boxing (from [chapter 5](#time-boxing)) to limit exploration of any branch.

### Summary: Drawing Backwards

**Drawing backwards** is the heuristic of starting from your desired end state and working systematically toward your current position.

**In Product-led Research**, drawing backwards means:
1. Start by defining what successful output looks like (often manually or semi-manually).
2. Validate the output with stakeholders before technical work.
3. Work backwards through dependencies, solving them in reverse order.
4. Validate that each step contributes to the goal before major investment.

This heuristic ensures that Research connects to product impact, since you start with the product goal. It provides systematic progress even when problems seem overwhelming, and makes you validate each step before you invest heavily.

**Integration with other tools:**
- Use with Research Tree ([chapter 4](#the-research-tree)) to map backwards dependencies.
- Apply time-boxing ([chapter 5](#time-boxing)) to limit exploration of each branch.
- Combine with pre-Research checks ([chapter 6](#how-to-choose-research-initiatives)) to validate product impact.

In the next chapter, you will learn about two limitations of drawing backwards and how to address them with continuous end-to-end iterations.
