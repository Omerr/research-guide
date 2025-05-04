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
4. Gradually replace manual steps with automated ones, while carefully prioritizing.
5. Get feedback on the end result as much as possible.

Let me explain each of these principles in more detail. To do so, I'll use the example I shared in [chapter 5]{#drawing-backwards} about extracting business rules from COBOL code. Since this book is not about extracting business rules from COBOL code, I'll provide short and somewhat simplified explanations, as the focus is on the principles and methodology.

### 1. Draw the end-to-end process

To be more accurate, draw the hypothesized end-to-end process. You can't know for sure what the process will be until you've tested it with users.

Essentially, drawing the end-to-end process is hypothesizing about drawing backwards all the way to the start. When working on extracting business rules from COBOL code, we started by considering the end result - a document with business rules. We then asked ourselves - how can we get to this document? Assume our document includes one section per business rule, with a hierarchical structure according to the business rules' dependencies. A possible end-to-end process could be:

1. Start with a COBOL program.
2. Parse the COBOL program into an Abstract Syntax Tree (AST).
3. Traverse the AST to find conditions.
4. Filter out business-related conditions.
5. For every rule - areate a document section about the condition.
6. Sort the document sections according to the business rules' dependencies.

This might indeed be our first draft.

You can start by drawing a few boxes on a whiteboard.

### 2. Get to end-to-end with by simplifying the process and taking shortcuts

 everything manual unless something is already automated.

### 3. Ship it as fast as you can

### 4. Gradually replace manual steps with automated ones, while carefully prioritizing

### 5. Get feedback on the end result as much as possible