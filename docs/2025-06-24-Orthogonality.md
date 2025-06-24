---
layout: page
title: Orthogonality in code (even in SysDesign or gui) + MetaProgramg
category: Programming
tags: [Programming]

---
pragmatic programming book: 

{pg59-69 Orthogonality chapter noNeedToLook now} - orthogonality aka modularity aka Decoupled code (make variables in system such that x changes '0' impacts y) (orthogonal code follow DoNotRepeatYourself): 

A. for orthogonality in coding, in addition to DRY n class s'ud have atmost nothing to do w another class input output relation, Avoid global data at most possible. 

Every time your code references global data, it ties itself into other components that share that data. Even globals that you intend only to read can lead to trouble (for eg, if you suddenly need to change your code to be multithreaded).

In general, your code is easier to understand and maintain if u explicitly pass any required context into your modules. 

In object-oriented applications, context is often passed as parameters to objects’ constructors. In other code, you can create structures con-
taining the context and pass around references to them. 

The Singleton pattern in Design Patterns is way of ensuring that there is only one instance of an object of a particular
class. Many people use these singleton objects as a kind of global variable (particularly in languages, such as Java, that otherwise do
not support the concept of globals). However, be careful with singletons— this can also need to unnecessary linkages.

B. testing (Here, context is: testing code workability in code itself, n NOT about QA who tests GUI)
![image](https://github.com/user-attachments/assets/90de2e54-99cb-42e4-a418-88874f50cb3b)

So, w orthogonal code, testing doesnt become headache integration testing (testing how if A is changed, does it messes up B classes n hence end output) but becomes Unit testing (testing individual class behaviour ie. input to class vs its desired output) is enof. 

So,"Bug ﬁxing is also a good time to assess orthogonality of system as whole. When you come across a problem, assess how localized the ﬁx is. Do you change just one module, or are the changes scattered throughout the entire system? 

When you make a change, does it ﬁx everything, or do other problems mysteriously arise? This is a good opportunity to bring automation to bear."

**every module should have its own unit test built into its code, n these tests be performed auto as part of regular build process.** - relates to this weblog's Perfect GitCommit post

C.Properly assemble toolkits n libraries such that they are atmost orthogonals:

_(This is synonymously talked by boringprinciple dot com n aws-sw-architecture book). I'm compiling so that different sources might be talking differently but they might be same essence so that I wont end up w flood of redundant concepts. garna aunu paryo at end of day, sakyo kura_

"So, We once worked on prj which required that certain body of Java code run both locally on server machine n remotely on client machine. 

Alternatives for distributing classes this way were RMI, COBRA. 

If class were made remotely accessible using RMI, every call to remote method in that class c'ud potentially overthrow exception, which means that naive implementation w'ud require us to handle exceptioon whenever our remote classes were used. Using RMI hence w'ud be no orthogonal: code calling our remote classes s'ud have to be aware of their locations. 

Alternatives (using COBRA) didnt impose restrictions: we c'ud write code that was unaware of our classes location.    

**When u bring in toolkit (or even library from other members of ur team), ask urself whether it implies certain changes on ur code that s'udnt be there.** If object persistence scheme is transparent, then its orthogonal. If it requires u to create or access objects in special way, then its not. 

Keeping such details isolated from ur code has added benefit of making it easaier to change vendors in future.    

Eg: Enterprise Java Beans EJB is eg of ortho. 

In most transaction oriented sys, application code has to delineate black-box aka compartmentalise start n end of tx. With EJB, info is expressed ***declaratively** AS METADATA, outside any code. Same application code can run in different EJB tx environment with no change. This is what s'ud be as for many future environment design.  

![image](https://github.com/user-attachments/assets/79847b15-9bf7-4fbe-828b-115c7da0d3f6)

---
Metaprogramming {=programming using METADATA at most possible} (aka DYNAMIC, CONFIGURABLE programming)

_(pg169-174 thisChapter noNeedToLook now)_

A. metadata (data about data) isnt just about using data about database, like no. of row cols etc. which we aka schema. 

We'd want to use it in applications also in form of metadata driven applications. 
**We want to configure n drive application via metadata as much as possible** so that core logic is modularized somewhere else n its subtle variations are stored seperately- again orthogonality logic, huh. We do this by:

_so, .env we have been using, again is concept of metadata._

Extending this concept, our goal is to think DECLARATIVELY n create highly dynamic adaptable pgm such that HOWs rest modularized seperately -- imagine having to search whole code to rewrite some lines while u want to change some business logic or some middleware logic like api linking with A server instead of B. aka these items should be implemented as configuration options, n not thru integration. 

**THUMB-RULE: program for general case but specifics somewhere else ie outside compiled code base such that they are taken care by pgm execution at runtime, without having to go such option thru recompilation in each iterative adjustment.**

Live case: "your purchasing application may include various corporate policies. Maybe you pay small suppliers in 45 days and large ones in 90 days. Make the deﬁnitions of the supplier types, as well as the time periods themselves, conﬁgurable. Take the opportunity to generalize.

Maybe you are writing a system with horrendous workﬂow requirements. Actions start and stop according to complex (n changing) business rules. Consider encoding them in some kind of rule-based (or expert) system, embedded within your application. That way, you’ll conﬁgure it by writing rules, not cutting code.
Less complex logic can be expressed using a mini-language, removing need to recompile n redeploy when the environment changes."

![image](https://github.com/user-attachments/assets/847e8874-32e4-4250-a1dd-6926c8c383b9)

B. Cooperative Conﬁguration: We’ve talked about users and developers conﬁguring dynamic applications. 

But what happens if you let applications conﬁgure each other— software that adapts itself to its environment? Unplanned, spur-of-the-
moment conﬁguration of existing software is a powerful concept.

OS already conﬁgure themselves to hardware as they boot, and Web browsers update themselves with new components automatically.

Your larger applications probably already have issues with handling different versions of data and different releases of libraries and operating systems. Perhaps a more dynamic approach of co-operative configuration will help.
