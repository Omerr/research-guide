\newpage

# Part 1 - What is Research?

## Chapter 1 - Problem Solving as the Foundation of Research {#problem-solving}

To help us manage research effectively, we first need to understand what research is, and what it is not. Specifically for R&D teams, we need to separate research from development. In this chapter, you will get to know Schoenfeld's model of problem solving, as I will rely on it to define research. In the next chapter, you will use this model to distinguish research from development.

To define research, I've found Alan Schoenfeld's model of problem solving to be a useful framework. To introduce you to the model, I'd like to share a true story.

### A true story

It was a hot summer day in Atlanta, Georgia. I had flown there to represent my company, Swimm, in a booth at a conference. To draw the attention of the conference's attendees, I wanted our booth to include something special, enticing. I decided to pose a problem, wrapped as a game, with a prize. Anyone could aim to solve this problem and win the game, and if they did - they'd get a cool Swimm Rubber Duck.

You can see the game from the original booth here:

https://photos.google.com/search/atlanta/photo/AF1QipPIoGfmBHOSGdzd1MtAeSiGF-Wgs2AlHIR8-DAa

In the image above - the duck is on spot number `41`. Each player, at their turn, moves the duck between 1 to 6 spots. So if the duck is on spot `41`, the player can move it to any spot between `40` and `35`. The player who moves the duck to spot `1` wins the game.

Each person who walked up to the booth could play the game - then, they could decide whether they wanted to play first or second. They got as much time to think as they wanted. I would play against them, and if they won - they'd get the duck.

Not one of the people who tried to play against me won the first time they did. Many tried multiple times and failed to win. At that point, they did not know what to do. It wasn't obvious for them that there *is* a solution (until I told them so), or how to approach the problem.

In a sense, this is a small Research task (you will see how it relates to the definition of research later).

Some people got back, after a few attempts, and solved this correctly. Most people didn't. They just gave up. It is hard to know if it was because they weren't motivated enough to succeed, or didn't believe they would. And still - many questions arise here. What separated those who succeded from those who didn't? And, more importantly, is this just a born gift or could people improve their Research skills?

As I mentioned, most people faced with this challenge did not know how to approach this problem, and eventually gave up. You may ask, what does this game have to do with Research? It is a simple game, after all. It is not a Research task, right?

In the next section, I will describe a framework for Problem Solving, which I believe can be applied to Research tasks. We will analyze the Spiral game above with it, and then see how it can be applied to other, more complex problems.

But let's solve the puzzle. If you're up for it, feel free to try it for youself - can you make sure you always win?

⭐ Try to solve the problem yourself before reading on. This is not mandatory, but I believe it will help you understand the framework better. Besides, it is fun.

## The Spiral Game - Solution
Think about this methodically.

It would be much easier to start from the end.

Say the duck is on spot `2`. You would want to be first, move exactly `1` step and get to `1`. That's clear.

What about `3`? You'd want to be first and take `2` steps - to get to `1`. That's clear too.

You can keep going like that until you get to `7`, where you need to take `6` steps to get to `1`.

Next, if the duck is on spot `8`, what can you do?

If you take `1` step, your opponent will have the duck on spot `7`, and you know that if the duck is on spot `7`, the other player can win. For every possible turn, you can see that if the duck is on spot `8`, the player who moves first will move to duck to a position between `2` and `7`, where the other player can win.

Since there is no "good" move for the player who moves first when the duck is on spot `8`, you would want to be the second player in that case.

Now, you can view this as a new game - the player who reaches `8` wins. If you move the duck to spot `8`, then it's the other player's turn, and you know you can win for certain. You should thus focus "only" on reaching spot number `8`.

// Image

Keep going. If the duck is on spot `9` - you can take `1` step and get to `8`, so you wish to be first. If the duck is on spot `10` - you can take `2` steps and get to `8`. And so on.. Until you get to `14`, where you need to take `6` steps to get to `8`.

// Image

At `15`, any move you make would make you get to a spot between `14` and `9`, where you already know you want to be first... So you would want to be the second player when the duck is on spot `15`.

// Image

And now you can, again, consider this a new game - trying to reach `15` to win.

`8` and `15` are exactly `7` spots apart. This is no coincidence. It is the same difference between `1` and `8`, and we win when we get to `1`. When a player has to play on spot `8`, they can move at max `6` steps which is not enough to reach `1`, and then the other player can make the move to reach `1`.

In general, if we keep the following rule, we always win:

After each turn we make, the duck will be on a spot of the form `7k+1` (where `k` is a non-negative integer). So `1`, `8`, `15`, `22`, `29` and so on - are all spots where we want to be second.

### Schoenfeld's Problem Solving Model - A Framework for Problem Solving

I would like to adopt a framework for Problem Solving by Alan H. Schoenfeld (1992, see references). While this framework was first devised to describe how people solve math problems, I believe it can be applied to Research tasks in general.

In general, Schoenfeld describes four components of Problem Solving**:

1. "The knowledge base" - basically, what you *know*. For example, if you are faced with an optimization problem - are you familiar with profiling tools? Are you familiar with optimization algorithms? Do you know how to use them? 

2. "Heuristics" - these are strategies you can use to solve problems. For example, if you are faced with an optimization problem, you can first try to profile your code, and see where the bottlenecks are. You can also debug a specific case, or draw a diagram of the problem. If the problem you are solving is writing a compelling article, heurstics can be creating an outline before starting to write, using a specific structure, or writing the conclusion first.

3. "Control" - this is the ability to monitor your progress, and adjust your strategy if needed. For example, if you are trying to solve a problem and you see that your current strategy is not working, you can try a different one. This greatly distinguishes experienced researchers from novices - what matters is not just what you know, but how and when you use what you know.

4. "Beliefs and attitudes" - these are your beliefs about your ability to solve the problem, and your attitude towards the problem. For example, if you believe that you are not good at solving optimization problems, you may not even try to solve the problem. Schoenfeld describes a few typical student beliefs about mathematics problems, such as "I'm not good at math", "Math is a matter of memorization", "There is one right answer", and so on. These beliefs can greatly affect your ability to solve problems.

Let's analyze the Spiral Game and our solution with this framework.

## How could you apply the framework to the Spiral Game?

1. **The knowledge base**. To solve this problem, you need to understand simple arithmetic (how to add and subtract numbers). To actually prove that you always win, you need to understand the concept of "modulus" - that is, the remainder of a division. 

2. **Heuristics**. We mainly used two heuristics to solve this problem. First, we tried to solve the problem by starting from the end and drawing back. Second, we considered cases systematically and listed them. Third, we generalized the solution to all cases. 

3. **Control**. I showed you a clear solution to the problem, but for most people who address it - they first try different "guesses". Maybe I just need to be first on odd spots. When they try it, a Control would be to refute their hypothesis - try to find a counterexample. Understanding that you should start from the end and draw backward, and work systematically - that is, using the heuristics described before, is a form of Control.

4. **Beliefs and attitudes**. If you believe that you can solve this problem, you are more likely to try to solve it. Many of the people who tried to solve this problem simply gave up after two minutes, with a shrug and a short saying like "I am not good with this kind of things". Another belief is that you should solve this problem in your head, rather than using a pen and paper. To systematically consider different spots, it is actually very helpful to write them down.

### Research as Problem Solving - Reflection

So, again, what does the Spiral Game have to do with Research?

The same **Heuristics** and **Control** we used to solve the Spiral Game can be used to solve more complex Research tasks. The **Knowledge base** would probably be different. By solving this task, and then discussing the process of solving it and learning from it, the solver can improve their Research skills. This does not happen with a single task, but with many tasks. I have seen people get better at solving tasks by practicing on small tasks, and then gradually moving to more complex ones. Schoenfeld's research has shown that students can learn to use effective heuristics for solving problems, and that they can learn to monitor their progress and adjust their strategies (Control). As leaders of Research teams, you can help your team improve their Research skills and perform Research tasks more effectively. I wlil dive into that in future chapters.

In this chapter, you got to know Schoenfeld's model of problem solving, and how it can be applied to Research tasks. In the next chapter, we will use this model to distinguish Research from Development.


### Notes
** Actually, Schoenfeld (1992) described five components (which he terms "categories"), but I focused on four of them.

### References

Schoenfeld, A. H. (1992). Learning to think mathematically: Problem solving,
metacognition, and sense-making in mathematics. In D. Grouws (Ed.), Handbook for
Research on Mathematics Teaching and Learning (pp. 334-370). New York: MacMillan.
