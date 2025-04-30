\newpage

## Chapter 5 - Drawing Backwards {#drawing-backwards}

// In chapter 4...

Remember the spiral game introduced in [chapter 1]({#problem-solving})? As a reminder - the game looked like this:

![https://photos.google.com/search/atlanta/photo/AF1QipPIoGfmBHOSGdzd1MtAeSiGF-Wgs2AlHIR8-DAa](Spiral game)

In the image above - the duck is on spot number `41`. Each player, at their turn, moves the duck between 1 to 6 spots. So if the duck is on spot `41`, the player can move it to any spot between `40` and `35`. The player who moves the duck to spot `1` wins the game.

The key to solving this game was to start from the *end* and draw backwards. By working systematically from the end, you were able to:
1. Know what you were doing. Instead of just "trying out" things - you had a "system" - you worked your way systmetatically from spot `1` to `2` and then to `3` and so on.
2. Rely on the previous step. For example, you already knew that if you had the option and the duck were on spot `2`, `3`, `4`, `5`, `6` or `7` - you'd want to be first. You can thus easily deduce that if the duck were on spot `8`, you would want to be second.

Let us consider a different game.

// C:\Users\omerr\OneDrive\Documents\Lectures\Problem Solving Workshop - NIM1

If you are interested in trying out more similar games, I provided a few more in [Appendix A](#appendix-a).

In these games, the key was starting from the end of the game - either the duck being on spot `1`, or the state of both towers having `0` bricks, and drawing backwards systematically.

The same principle applies to making sure your Research efforts really make the desired impact.

Why is that?

Most importantly - because the "end state" is that where you reached your desired product impact, which is - as I stated before, your most important role.

Consider this example. At Swimm, we wanted to automatically generate documents from COBOL codebases that included all the extracted business rules. For those of you who aren't familiar with business rules, let me provide a short explanation just so you get a sense of the challenge at hand.

Business rules are the rules that govern the operation of a business.

In essence, business rules are the specific constraints, conditions, and actions embedded within a software system that reflect the policies and procedures of an organization. Legacy systems contain strategic business rules that govern the business processes, whether these rules are explicit or implicit.

For example, within the process of transferring money between bank accounts, business rules would include constraints like:

* A customer cannot transfer more money than is available in their account (overdraft limits notwithstanding)  
* Certain high-value transfers may require additional verification steps  
* Transfers between accounts in different currencies must apply the current exchange rate

Some sources define Business Rules as consisting of three basic elements – Event, Condition and Action. The standard rule pattern is:

ON \<Event\>

IF \<(Condition)\>

THEN \<Action\>

ELSE \<Action\>

Our goal was to extract all business rules within a COBOL codebase. To focus on a smaller case, to extract all business rules relating to a certain flow. While the problem of extracting business rules is challenging in any codebase, the problem is way more acute in legacy codebases in general, and COBOL codebases in particular. If you are interested to learn more about this specific challenge, you can read my post about it (//Add link). For the scope of this book, it is suffice to say that many research attempts were conducted over the last few decades, trying different approaches to face this challenge.

### Drawing Backwards to Extract Business Rules

If you are faced with this problem of extracting business rules from code - where should you even start? You may want to build a callgraph of all functions, which means you'd need to parse COBOL code. So maybe you should start by creating a COBOL parser? You may want to read academic papers and learn about directions pursued by others (which would be a good practice during the research initiative choosing phase, detailed in [chapter 4]({#how-to-choose-research-initiatives})). Perhaps you should be able to track a COBOL variable along the codebase. Perhaps you should distinguish conditions that are related to the business (for example, "if the requested amount of money to transfer is greater than the current available amount - deny the transfer") from technical conditions ("if the variable is not initiailized, show an error"). Each one of those steps may require some small research (and I intentionally use a lowercase "r" in "research" here), but where should you start?

Drawing backwards make us ask this question:

"If the Research succeeds, what would the result look like?"

When we first asked ourselves that question, we weren't really sure. We knew for sure from our clients that they want the extracted business rules, but we couldn't know for certain what would be the "ideal" output.

We therefore decided, before approaching any of the sub-tasks I listed above, to manually create documents that show extracted business rules from some sample programs. We did it completely manually, without solving any technological challenge (rather than understanding COBOL code on our own, which you might claim deserves to be called a challenge 😇). We did that for various types of applications from various codebases, and learned that the output structure may indeed differ from one program to another. We also learned that there is no one way to construct such a document.

By creating these documents manually, we formed a hypothesis - this is what the output should look like, which actually means - this output would make the biggest impact on the product. This is our north star. But is it? At this stage, this is just a hypothesis.

Once we wrote the documents manually, it was time to verify this hypothesis. With a concrete (manual) output at hand, we could hold more concrete discussions. We could discuss this output internally within the team and ask other team members what they tought of this output, and after some internal discussion - we reached out to our clients, showed them the outputs, and asked for their feedback.

We deliberately refrained from solving hard technological research challenges before making sure we knew where we were shooting for.

Another thing we got from this "exercise", was to have a concrete example where we could ask ourselves - what would be the way to get to this document?

For example, we saw that we listed many conditions. That made us realize we would need to:
1. Find conditions
2. Filter out business-related conditions
3. Explain the condition in a document.

Since we are drawing backwards here, we would tackle (3) before we tackle (2), and we would tackle (2) before tackling (1). Why is that? Because we have to solve (3) in order to get to our goal - a document with the biggest possible impact.

This means that we need to mock the first two steps - assume we already found a way to find conditions, and assume we already filtered out business-related conditions. So we already have a list of the conditions we want to describe, and now the challenge is, for each such condition - explain it in the output document.

This prevents us from spending time on task that may turn out to be futile as they can't really serve our end goal.

// TODO: Edit this sentence
While it is true that in order to reach (3) we would need to solve (2) and (1), but if we fail to accomplish (3) assuming that (1) and (2) were accomplished, it might not be worth pursuing (2) and (1) at all, and we would need to consider an alternative approach.


## Why Drawing Backwards is so Powerful

We can see the advantages of drawing backwards:
1. It forces you to connect to the business impact.
2. It provides a mechanism to progress when the Research seems like a huge, daunting task with endless options.
3. It makes us validate that we are solving a sub-task that would get us closer to the goal.

// Summary