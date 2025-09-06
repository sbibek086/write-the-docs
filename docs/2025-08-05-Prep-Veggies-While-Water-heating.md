---
layout: default
title: PrepCut Veggies meanwhile water is heating
category: Programming
tags: [Programming]

---

There are two aspects of time that are important to us: concurrency(things happening at the same time) and ordering (the relative positions of things in time).

Tarkari ko laagi pyaaj furirahada tarkari katdai garda ni vayo ni ta. That’s DE-temporal coupling, by which we can improve speed in workﬂow analysis, architecture, design, and deployment.  aws asynchronicity n projManagement's oneSmartness is about this 

how it applies in Architecture: 

We wrote On-Line Transaction Processing (OLTP) system a few years ago. At its simplest, all the system had to do was read a request n process transaction against Db. 

But we wrote a three-tier, multiprocessing distributed application: each component was independent entity that ran concurrently with all other components.

While this sounds like more work, it wasn’t: taking advantage of temporal decoupling made it easier to write. Let’s take a closer look at this project in figure: 

The design addresses the following constraints as below figure: 
<img width="774" height="449" alt="image" src="https://github.com/user-attachments/assets/b149ff15-0db0-472e-bad4-5da0cead9d61" />


**DESIGN FOR CONCURRENCY:** The rising acceptance of Java as a platform has exposed more developers to multithreaded programming. But programming with threads
imposes some design constraints—and that’s a good thing. Those constraints are actually so helpful that we want to abide by them whenever we program. It will help us decouple our code.

With linear code, it’s easy to make assumptions that lead to sloppy programming. But concurrency forces you to think through things a bit more carefully—you’re not alone at the party anymore. Because things can now happen at the “same time,” you may suddenly see some time-based dependencies.

To begin with, any global or static variables must be protected from concurrent access. Now may be a good time to ask yourself WHY U NEED A GLOBAL VARIABLE in the ﬁrst place. In addition, you need to make sure that you present consistent state information, regardless of order of calls. 
For eg, when is it valid to query the state of your object? If your object is in an invalid state between certain calls, you may be relying on a coincidence that no one can call your object at that point in time.

esto concurrent aka asynchronous sys banaudaa Objects must always be in a valid state when called, n they can be called at the most awkward times. You must ensure that an object is in a valid state any time it could possibly be called. Often this problem shows up with classes that deﬁne separate constructor and initialization routines (where the constructor doesn’t leave the object in an initialized state). 
Using class invariants, discussed in **DESIGN BY CONTRACT(look at bottom of this post here)** will help you avoid this trap.

**CLEANER INTERFACES:** Thinking about concurrency and time-ordered dependencies can lead you to design cleaner interfaces as well.

<img width="950" height="464" alt="image" src="https://github.com/user-attachments/assets/00083d38-1cca-4c85-a25b-c2e1efff43c0" />

**DEPLOYMENT:** Once you’ve designed an architecture with an element of concurrency, it becomes easier to think about handling many concurrent services:
the model becomes pervasive.

Now you can be ﬂexible as to how the application is deployed: stand-alone, client-server, or n-tier. By architecting your system as independent services, you can make the conﬁguration dynamic as well.

By planning for concurrency, and decoupling operations in time, you have all these options—including the stand-alone option, where you can choose not to be concurrent.
Going the other way (trying to add concurrency to a nonconcurrent application) is much harder. If we design to allow for concurrency, we can more easily meet scalability or performance requirements when time comes—and if the time never comes, we still have the beneﬁt of a cleaner design.

---
DESIGN BY CONTRACT:   Ideally as according to Design by Contract (n it is best practice), below should be obeyed while writing function or method: 

a)Preconditions. What must be true in order for the routine to be called; the routine’s requirements. A routine should never get called when its preconditions would be violated. It is the caller’s responsibility to pass good data (see the box on page 115). 

b)Postconditions. What the routine is guaranteed to do; the state of the world when the routine is done. The fact that the routine has a postcondition implies that it will conclude: inﬁnite loops aren’t allowed.

c)Class invariants. A class ensures that this condition is always true from the perspective of a caller. During internal processing of a routine, the invariant may not hold, but by the time the routine exits and control returns to the caller, the invariant must be true.
(Note that a class cannot give unrestricted write-access to any data member that participates in the invariant.)

Let’s look at the contract for a routine that inserts a data value into a unique, ordered list. In iContract, a preprocessor for Java available, you’d specify it as

<img width="394" height="192" alt="image" src="https://github.com/user-attachments/assets/6317f93b-26ed-4dde-8ab1-977737c8edf8" />

Here we are saying that nodes in this list must always be in increasing order. When you insert a new node, it can’t exist already, and we guarantee that the node will be found after you have inserted it. 

You write these preconditions, postconditions, and invariants in the target programming language, perhaps with some extensions. For eg, iContract provides predicate logic operators—forall, exists, and implies—in addition to normal Java constructs. Your assertions can query the state of any object that the method can access, but be sure that the query is free from any side effects

The contract between a routine and any potential caller can thus be read as -> If all the routine’s preconditions are met by the caller, the routine shall
guarantee that all postconditions and invariants will be true when it completes.

If either party fails to live up to the terms of the contract, then a remedy (which was previously agreed to) is invoked—an exception is raised, or the program terminates, for instance. Whatever happens, make no mistake that failure to live up to the contract is a bug. It is not something that should ever happen, which is why preconditions should not be used to perform things such as user-input validation.

In Orthogonality, we recommended writing “shy” code. Here, the emphasis is on “lazy” code: be strict in what you will accept before you begin, and promise as little as possible in return. Remember, if your contract indicates that you’ll accept anything and promise the world in return, then you’ve got a lot of code to write!

Inheritance and polymorphism are the cornerstones of object-oriented languages and an area where contracts can really shine. 

Suppose you are using inheritance to create an “is-a-kind-of” relationship, where one class “is-a-kind-of” another class. You probably want to adhere to the
Liskov Substitution Principle:

Other Uses of Invariants:  So far we have discussed pre- and postconditions that apply to individual methods and invariants that apply to all methods within a class,
but there are other useful ways to use invariants.

c i)Loop Invariants: Getting the boundary conditions right on a nontrivial loop can be problematic. Loops are subject to the banana problem (I know how to spell
“banana,” but I don’t know when to stop), fencepost errors (not knowing whether to count the fenceposts or the spaces between them), and the ubiquitous “off by one” error.
Invariants can help in these situations: a loop invariant is a statement of the eventual goal of a loop, but is generalized so that it is also valid before the loop executes and on each iteration through the loop. You can think of it as a kind of miniature contract. 

The classic example is a routine that ﬁnds the maximum value in an array.

<img width="386" height="108" alt="image" src="https://github.com/user-attachments/assets/e5ce9484-c5ed-4cb2-a52f-f751f8d5dc4d" />

(arr[m:n] is a notational convenience meaning a slice of the array from index m to n.) The invariant must be true before the loop runs, and the body of the loop must ensure that it remains true as the loop executes. 
In this way we know that the invariant also holds when the loop terminates, and therefore that our result is valid. Loop invariants can be coded explicitly as assertions, but they are also useful as design and documentation tools.

c ii)Semantic Invariants: You can use semantic invariants to express inviolate requirements, a kind of “philosophical contract.”

We once wrote a debit card transaction switch. A major requirement was that the user of a debit card should never have the same transaction applied to their account twice. In other words, no matter what sort of failure mode might happen, the error should be on the side of not processing a transaction rather than processing a duplicate transaction.

This simple law, driven directly from the requirements, proved to be very helpful in sorting out complex error recovery scenarios, and guided
the detailed design and implementation in many areas.

Be sure not to confuse requirements that are ﬁxed, inviolate laws with those that are merely policies that might change with a new management regime. That’s why we use the term semantic invariants—it must be central to the very meaning of a thing, and not subject to the whims of policy (which is what more dynamic business rules are for).

When you ﬁnd a requirement that qualiﬁes, make sure it becomes a well-known part of whatever documentation you are producing- whether it is a bulleted list in the requirements document that gets signed in triplicate or just a big note on the common whiteboard that everyone sees. Try to state it clearly and unambiguously. 

For eg, in the debit card example, we might write ERR IN FAVOR OF THE CONSUMER .
This is a clear, concise, unambiguous statement that’s applicable in many different areas of the system. It is our contract with all users of
the system, our guarantee of behavior. 

c iii) Dynamic Contracts and Agents:  Until now, we have talked about contracts as ﬁxed, immutable speciﬁcations. But in the landscape of autonomous agents, this doesn’t need to be the case. By the deﬁnition of “autonomous,” agents are free to reject requests that they do not want to honor. They are free to renego-
tiate the contract—“I can’t provide that, but if you give me this, then I might provide something else.”

Certainly any system that relies on agent technology has a critical dependence on contractual arrangements—even if they are dynamically generated.

Imagine: with enough components and agents that can negotiate their own contracts among themselves to achieve a goal, we might just solve the software productivity crisis by letting software solve it for us. 

But if we can’t use contracts by hand, we won’t be able to use them automatically. So next time you design a piece of software, design its contract as well.
