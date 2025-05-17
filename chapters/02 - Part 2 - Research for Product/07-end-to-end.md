\newpage

## Chapter 6 - End-to-end {#end-to-end}

// In chapter 5...

Again, your most important role is to make sure that your research impacts the product. One possible risk is spending a lot of time on a research question, or part of the research that seems vital, only to find out that it doesn't impact the product.

In [chapter 5]{#drawing-backwards}, I advocated for drawing backwards - starting from the product impact, and working your way backwards to the research questions. This is indeed a powerful approach, especially as it forces you to focus on the end result, and hopefully test it with users. There are two risks with this approach:

1. You might have created an end result that is not feasible.
2. Since you didn't complete an end-to-end process, you probably didn't run your solution on clients' data (assuming you can't access it offline).

These two risks are why I advocate for a continuous end-to-end process.

The end-to-end approach relies on the following principles:

1. Draw the end-to-end process. Always have it at hand.
2. Get to end-to-end with by simplifying the process and taking shortcuts
3. Ship it as fast as you can.
4. Gradually replace steps, while carefully prioritizing.
5. Get feedback on the end result as frequently as possible.

Let me explain each of these principles in more detail. To do so, I'll use the example I shared in [chapter 5]{#drawing-backwards} about extracting business rules from COBOL code. Since this book is *not* about extracting business rules from COBOL code, I'll provide short and somewhat simplified explanations, while focusing on the principles and methodology.

### 1. Outline the end-to-end process

You will start by outlining the entire process, end-to-end. To be more accurate, outline the *hypothesized* end-to-end process. You can't know for sure what the process will be until you've tested it with users.

Essentially, outlining the end-to-end process is hypothesizing about drawing backwards all the way to the start. When working on extracting business rules from COBOL code, we started by considering the end result - a document with business rules. We then asked ourselves - how can we get to this document? Assume our document includes one section per business rule, with a hierarchical structure according to the business rules' dependencies. A possible end-to-end process could be:

1. Start with a COBOL program.
2. Parse the COBOL program into an Abstract Syntax Tree (AST).
3. Traverse the AST to find conditions.
4. Filter out business-related conditions.
5. For every rule - create a document section about the condition.
6. Sort the document sections according to the business rules' dependencies.

This might indeed be our first draft.

You can outline this process by drawing a few boxes on a whiteboard. Sometimes, the process is not linear, so it would look more like a flowchart.

### 2. Get to end-to-end with by simplifying the process and taking shortcuts

Your goal at this stage is to make the process work end to end - start with the input (in our example, a COBOL program), and you need to reach the output (a document with business rules), awhile passing through the intermediate changes.

But that's a *lot* to solve! Don't you need to complete the whole research in order to achieve this stage?

Definitely not. The trick here is that you find the easiest way to get to end-to-end, by taking shortcuts and making assumption sthat are definitely too generous for a production-ready solution.

Unless something is already automated, complete the entire process manually. That is, start with a single, known COBOL program. Skip parsing it, just write a list of conditions for the next stage. The next phase is a filtering function that returns `true` if the condition is business-related and `false` otherwise. Its first implementation will be a simple mapping between the input conditions (that you know of) and whether it should return `true` or `false`. An alternative is that it will always return `true` - so you inevitably will get non-relevant rules in your document, but that is a problem for *later*.

The end result is a pretty bad-looking document (unless you manually wrote the sections too), that works solely on a single program. This is far from a solution you can ship, but I argue it is an extremely important milestone if you strive to make sure the research actually impacts the product.

### 3. Ship it as fast as you can

By the end of the previous stage, you have a working end-to-end process that works on a single case, but you definitely can't ship it. In our example, the solution works on a single program, definitely not the client's program.

The next milestone is to make a solution that we can ship. What does that mean? It could mean, a solution that works on *any* program. That seems too hard, and it will take us too much time. We need to take shortcuts. This is where we need to get creative. For example, if we are running on a client's program, we need to get as much information as possible about the program. Perhaps we can assume it's less than 1000 lines of code. Perhaps we can know which COBOL dialect the client uses (yes, COBOL has dialects, you learn new things every day), so you don't need to support others. Perhaps, for this first shippable version, we can use regular expressions to find conditions, rather than a full-fledged parser. It will mean we will miss some conditions, sure, but again - that is a problem for *later*.

Your goal here is clear: ship it. It doesn't need to be perfect. It needs to be enough for you to learn from this iteration. If you don't ship it, you can only learn from your own intuition, and that is a very bad idea.

You can't ship anything, however. In our example, on the previous stage, you only have a solution that works on a specific program. Generating a document that is not relevant for the client will be a waste of time, as it will teach you nothing.

Shortcuts can be made in many ways. I noted "algorithmic" shortcuts, such as using regular expressions instead of a full-fledged parser. Other shortcuts can be made in terms of the user experience. For example, you can skip the document generation step, and just print the rules in the console. The whole tool can be run from the command line, without a GUI, as a first step.

The point is that you can't ship anything if you don't have a working end-to-end process. And you can't learn from this iteration if you don't ship it.

### 4. Gradually replace steps, while carefully prioritizing

Now that you have a working end-to-end process, you can start to replace various steps' implementations with better ones. This can mean replacing manual steps with automated ones, and taking out some of the shortcuts you made in the previous stage with more robust implementations.

Now, the goal is careful prioritization. You will definitely have many things you think you *must* replace as soon as you shipped the previous iteration, but again - the goal is to make your research impact the product. To do that, you need to carefully prioritize. Prioritization should be based on three things:

1. If you learned that something doesn't work in the current implementation, and must be fixed for the product to be viable.
2. If by changing the implementation, you will learn more about the product's impact on the next iteration.
3. Effort estimation for the specific change.

You want to iterate fast - which means, changing something, and shipping again to get feedback. Be careful not to solve every issue you find with the current implementation, even issues that the clients mention. What is the most important thing to change for you to be able to learn something on the very next iteration?

### 5. Get feedback on the end result as frequently as possible

The last step is to get feedback on the end result as frequently as possible. On each iteration, you should:
1. Get feedback on the end result.
2. Understand the next questions to answer.
3. Plan the next iteration accordingly.
4. Implement the minimal changes to be able to answer questions, at least some of them, within the next iteration.

### End-to-end process - Summary


