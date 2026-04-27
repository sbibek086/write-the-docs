---
layout: default
title: ~
category: Programming
tags: [Programming]

---

# Using pi - creating skills in it

🐧2 - (_read 🐧post if u only feel like before this 2_)
<img width="894" height="669" alt="image" src="https://github.com/user-attachments/assets/bc12b1e3-5b16-4336-a797-c83954bb783c" />
<img width="1275" height="571" alt="image" src="https://github.com/user-attachments/assets/6021a0cc-ceeb-4131-b802-52ff6a2c372a" />

BUT here, I want to focus more on building skills for .pi
<img width="918" height="526" alt="image" src="https://github.com/user-attachments/assets/aaf063e3-a846-41ff-b4b1-f8cc32561ea6" />

now, trying to use gdcli led me to more Eureka!-rabbitHole moment:
<img width="459" height="623" alt="image" src="https://github.com/user-attachments/assets/1e4e1701-9a6f-4a72-8f59-2a6df75fcc60" />

Eureka moment of whole console.google.com (- Google's aws equivalent) DISCOVERY
<img width="1291" height="573" alt="image" src="https://github.com/user-attachments/assets/2cbe1e36-d5e4-4ed7-9506-9ad7546c39c2" />

<img width="1254" height="249" alt="image" src="https://github.com/user-attachments/assets/612f1249-e432-4a48-9b72-92c76697b65f" />

----
<img width="1227" height="583" alt="image" src="https://github.com/user-attachments/assets/21ad9dc5-1be4-4012-9d28-c184f3f4c22c" />


---
---
CLAUDE AGENTIC CO-ORDINATION PROBLEM CLEVER SOLN- yo maile aafu le garya haina, jus copy pasting one post- SO DONT WORRY ABOUT IT!

<img width="458" height="184" alt="image" src="https://github.com/user-attachments/assets/18f8e5b0-b6d1-4d77-9c45-de19e75b289e"/>

*ding*

You hear a notification sound from a Claude Code workflow finishing. Which terminal tab was it?

Hop around terminal windows and tabs for a bit, finally find it. It was Project B. Okay, now which browser was that in...

Oh, it got assigned localhost:3001, now my auth redirects are broken. Which terminal tab is using :3000 right now?

Okay, it was Project A, just killed it. Where's the tab for Project B's dev server?

*ding*
Another workflow has finished. It briefly grabs your attention - just long enough to lose track of what you were doing.

I want to make something clear before we go further: This is not your fault

**Claude's tools were not built for how we work today.**

Back in my day (read: 2 months ago), we worked on one thing at a time. Our work was split between 3 apps, the terminal, IDE and browser. Let's say we were working on Project A. It looked something like this:

<img width="458" height="499" alt="image" src="https://github.com/user-attachments/assets/41778f23-797a-44a3-bb84-431a93e374e4" />

The split didn't matter because it was all grouped together in your head. Project A was split between apps, but we think of it differently. We used all of these apps WITHIN Project A.

But I'm not just working on Project A anymore.

---
**The PROBLEM**

<img width="458" height="356" alt="image" src="https://github.com/user-attachments/assets/0e6673ff-8c2f-418b-8748-ab1c20ec1d1c" />

Oh...oh no...

When you have more than one project going, the mental model collapses.

<img width="458" height="207" alt="image" src="https://github.com/user-attachments/assets/362d2f69-a44a-4ab6-a2ca-67856bcbcad3" />

Our projects are split BETWEEN apps, windows and tabs. There's no natural grouping! If I see some work finish in Claude Code for Project A, I have to go hunt for the right Chrome window/tab to see the results. If I want to check the code, I have to hop between multiple IDE windows trying to find it. When it's time to file a PR, good luck finding the right github tab!

The issues with this workflow go way deeper. Death by thousands of papercuts (in parallel!)

Do you split terminal between tabs or windows?

Tmux?

How do you know which terminal window you are in?

What about your browser? How will you split your work up?

How do you handle collisions when everything uses :3000? Can your auth redirects handle it?

One fights these issues every single day. Pity is: I spend more time switching between apps than I spend building.

----
**The SOLUTION**

I'll be honest, I don't have one. Here are some things I can confidently say are NOT a solution

tmux (Great for splitting terminals, does not help with mental overhead)

Agent orchestration GUIs (Roughly same as above)

IDE w/ built-in browser (Cool, what about github? Auth?)

Docker (lmao)

Background agents (Make agent management easier at the cost of everything else)

I am not writing this post to announce something or to sound smart. I really, really just want this fixed. I almost started to build an OS to do it.

I need to be realistic. I can't do this one. I don't have the skill, time or mental bandwidth to figure this one out.

I wrote this in hopes I can inspire others to solve this problem. There is no single "correct" solution to this. We need lots of them.

Experiment. It's never been easier to test out theories. Build new workflows. Feel this pain deeply. Try to fix it. Fail. Try again. Keep trying. We need to figure this out.

We need to change how we use computers.

quoted
