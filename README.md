##Understanding Recursion in JavaScript
> In my attempt to understand recursion I found many of the explanations somewhat complex at times, when at its core, recursion
>is a rather simple concept once you understand the basics.

What is Recursion?
---

Simply put - Recursion is a technique in which a function calls itself.

**But** if you're like me, this is simply not enough to understand how it works and why use it!

Why use Recursion?
---

- Allows for the writing of neater and more elegant code by dividing big and sometime complex complex problems into smaller and simpler problems. (http://en.wikipedia.org/wiki/Recursion#Functional_recursion)
- Recursion allows us to create the functionality of a loop without actually using a loop.
- Recursion also allows us to write a series of asynchronous calls without nesting them. (https://medium.com/functional-javascript/recursion-282a6abbf3c5)

Caveat
---
When using recursion beware of overloading the call stack or creating an infinite loop by not setting a base case or termination case.

>In JavaScript every function call will add a call frame to the call stack. The frame is popped off the call stack when the call returns. However a recursive function does not return immediately. It will make a recursive call before it returns. This will add to the call stack every time. Recursively calling from the tail position sufficently deep, will cause the call stack to run out of space, throwing a RangeError.

https://medium.com/functional-javascript/recursion-282a6abbf3c5

How to write a recursive function and its parts.
---

Let's take the most common example - a factorial - and break out recursion into its fundamental parts.

```javascript
function factorial (n) {

  //This is our Termination Condition
  if(n < 0) {
    return;
  }

  //This section is our Base Case - when n = 0, we stop the recursion
  if(n === 0) {
    return 1;
  }

  //This is our Recursive Case
  //It will run for all the other conditions except when n is equal to 0
  return n * factorial (n - 1);
};
```

There are a few key features to recursion that must be included in order for it to work properly.

1. The Termination Condition to cancel the recursion in case of an error or bad input. This is a specific statement that will stop the recursion.
2. The Base Case - this is a statement usually within a conditional clause like "if" that stops the recursion from going into an infinite loop.
3. The Recursive Case - this is the statement where recursion actually happens; where the recursive function is called on itself.


>When building a Recursive Case (the code that will be repeated), one rule of thumb is to ensure that the arguments you use for the recursion will lead to your Base Case.

>When writing a recursive function, ask yourself - Does the recursive case modify the arguments in such a way that each recursion brings it one step closer to the Base Case?
