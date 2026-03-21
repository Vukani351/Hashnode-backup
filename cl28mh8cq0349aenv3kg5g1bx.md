---
title: "Tips that grow your debugging skills"
seoTitle: "debugging | less bugs | documentation"
seoDescription: "how to write less buggy code | how to debug code"
datePublished: 2022-04-21T06:28:15.607Z
cuid: cl28mh8cq0349aenv3kg5g1bx
slug: tips-that-grow-your-debugging-skills
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1650522394246/y93OjiIVz.png
tags: documentation, debugging, clean-code

---

Creating quality code is an amazing process, and seeing your product run beautifully without crashing is another heavenly feeling, but bug-free code is highly unrealistic. Therefore let's go through some bug-crushing ideas to help us get that intoxicating feeling while writing fewer bugs.

## Using documentation to write cleaner code:

![https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.toptal.com%2Ffreelance%2Fwhy-design-documents-matter&psig=AOvVaw3lOzV-eGKEtpwsPZj6QA5y&ust=1647547005203000&source=images&cd=vfe&ved=0CAsQjRxqFwoTCICylKutzPYCFQAAAAAdAAAAABAD](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/niqb1l5xrbfqis7h4qqx.png)

- One of the things I learned painfully was that trying to **re-invent the coding was working against me**, so a major part of me creating fewer bugs actually came from sticking to the standard, by writing code using the docs as a reference. So I have to emphasize that learning to use documentation, and learning it correctly will greatly reduce the number of bugs you create.

- Using the docs also makes the types of bugs you meet predictable, we might not avoid them totally, but usually following standards creates a possibility that the issues you face were surely faced by other developers, and the solution is shared online your job is to find it. 

- Understanding documentation also gives you the power to copying and paste a bug fix with confidence to even modify it. It allows you to **understand the solution** and be able to replicate or create a solution for a similar problem in that same domain.

- Another benefit of sticking to the docs is that if you fail to debug, whomever you ask for help will in fact get to the source of the bug quicker and solve it easier, this is **because you wrote code in a way it is generally used** or with general behavior. 

## Your first priority is understanding your error message.

![https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.istockphoto.com%2Fillustrations%2Fhigh-priority&psig=AOvVaw3dFcjBejqCArpxt5J7COAf&ust=1647547418746000&source=images&cd=vfe&ved=0CAsQjRxqFwoTCICj0-iuzPYCFQAAAAAdAAAAABAD](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/67gop50ni7r71t2dqgey.jpg)

- A sad reality is that we juniors actually get so stressed with error messages we prioritize removing the message not truly fixing the bug that causes it, that’s why some bug fixes produce more bugs but we can change that.

- **Read your stack trace carefully**, follow the error messages to find where the exception was thrown, some times the debugger will show you where the bug is, it goes as far as showing the files affected 'as a hierarchy' therefore the one on top is likely the file with a problem, and next to the file name is a line number representing where the error is.

- If the bug keywords are foreign to you please don’t spend too much time on it, simply **search the bug on google** and look for a solution you can understand and modify, solutions that correspond with docs.

- My most important point here is that do not try to fix a bug before you fully understand it and what it means and only then do you start implementing chosen fixes.

## Remove confusion:

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/xv9w9nn311x5xbbs5wj1.jpg)

- One thing that my senior tend to always require from me was clarity because without it you will definitely face logic errors.

- One trick is to write **single-purpose code** because this will allow you to re-use your code and not repeat yourself, but again this means when there is a bug you will narrow it down easily because only one module/function does this functionality.

- Apply that KISS rule “keep it simple and stupid”, when you have to write complex logic, simply separate it into small simple pieces initially, then when it's working then remove any redundancies or any useless things that might make the code look longer and with millions of references.

- Another thing my senior pressed onto me was reusing code. I later realized that this makes me efficient and allows me to write code on a standard I can't produce and good quality code is less buggy code, but obviously, this **causes bugs also if not clear** about how a module or function you want to use works.

- Clarity also allows us to see the possible errors that might happen, so we can use try-catch clauses but with the intent of keeping them on the minimum.

## Check your tools and configs:

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/f0oyefeek3a6piejx7v5.jpg)

- Your tools will also cause you success or failure in a project so it's recommended that we first update our tools, and make sure everything is working correctly.

- Make sure your **framework's dependencies are not clashing** and that they are updated, or just re-install them, this sometimes causes bugs with building the project or running the project.

- On a more personal note, learn how to use your dev tool and you debugging tools, for web developers using Chrome debug tools is the go to, but others are out there. UI designers use Adobe XD or Figma, but to be great at your work mastering the tool is key.

- IDE have built-in debuggers for the languages they use and frameworks have those for the languages they accommodate, so once again that learning the debugger for that is useful for fixing bugs efficiently and effectively. 

- Sometimes while writing code, the error or output tab will show you warnings, with VS you even see them before you compile the code. Don't work against yourself by ignoring these when you polishing the code, look through them and fix those also to avoid bugs creeping up on you later.

## Use the conventions
- The [conventions](https://en.wikipedia.org/wiki/Coding_conventions) will save you a 
lot of issues across the board, they allow us to write code in a clean way and much readable and understandable.
- Using their naming conventions allows us to understand easily differentiate from names alone functions, variables, constants, and so on. 

- Using **comments correctly and on the minimum** will allow you to keep track of your thoughts when you made a decision but if you write simple code it means its self explaining code.

- you don't need to go deep into this but, at least applying the basics is enough for you to write cleaner code and be able to even understand why something is written in a certain format and why you could use it for yourself.

## Rest is one of the best debuggers

- It's true, working on a bug for too long is a thing, and if you don't rest so it won't too.
- A useful process in developing and debugging is taking time off the screen. This is why sometimes fresh eyes can see simple errors you couldn't.
- So an easy fix sometimes will be to fully consume the issue of the bug and then leave it to fix when you come back. The process of rest will allow your mind to see things differently, the feeling of being refreshed and calm is good for you to analyze and get deep easy with. 

A last important point to raise is being TDD “Test-Driven 
Development” is one important practice because you don’t need to get too far in maintaining code then you realize you have bugs in runtime, “assuming these are not syntax but logical errors”.

Bugs are a tricky hurdle, how do you deal with your bugs?

 