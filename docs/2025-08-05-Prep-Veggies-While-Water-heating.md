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

Suppose you have a windowing subsystem where the widgets are ﬁrst created and then shown on the display in two separate steps. You aren’t allowed to set state in the widget until it is shown. Depending on how the code is set up, you may be relying on the fact that no other object can use the created widget until you’ve shown it on the screen. 

But this may not be true in a concurrent system. Objects must always be in a valid state when called, and they can be called at the most awkward times. You must ensure that an object is in a valid state any time it could possibly be called. Often this problem shows up with classes that deﬁne separate constructor and initialization routines (where the constructor doesn’t leave the object in an initialized state). 
**Using class invariants, discussed in DESIGN BY CONTRACT** will help you avoid this trap.

**CLEANER INTERFACES:** Thinking about concurrency and time-ordered dependencies can lead you to design cleaner interfaces as well.

<img width="950" height="464" alt="image" src="https://github.com/user-attachments/assets/00083d38-1cca-4c85-a25b-c2e1efff43c0" />

**DEPLOYMENT:** Once you’ve designed an architecture with an element of concurrency, it becomes easier to think about handling many concurrent services:
the model becomes pervasive.

Now you can be ﬂexible as to how the application is deployed: stand-alone, client-server, or n-tier. By architecting your system as independent services, you can make the conﬁguration dynamic as well.

By planning for concurrency, and decoupling operations in time, you have all these options—including the stand-alone option, where you can choose not to be concurrent.
Going the other way (trying to add concurrency to a nonconcurrent application) is much harder. If we design to allow for concurrency, we can more easily meet scalability or performance requirements when time comes—and if the time never comes, we still have the beneﬁt of a cleaner design.
