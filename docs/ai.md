---
layout: default
title: ~
category: Lifestyle
tags: [Lifestyle]

---

USING LLM to write code:

![image](https://github.com/user-attachments/assets/5e7801af-b950-46cb-82aa-3a24c6eeac87)

_I have been criticized for not being smart enough to be one niche specific. I mean I am a) investing, b) learning devs n  
c)going depth about how Ethereum VM is built -drop this d) shit, learn to drive car, who cares whats in car engine; eat mango, who cares knowing biology of mango trees. n I'm trying 
 hard to reset this natural all-over-place syndrome_

To quote AB, (I am not referring BachPAAn guy who disllusions people w bullshit quiz knowledge, that does nobody no good n continues to fuck people, btw! )

**People that are extremely successful don’t learn/study more than others.  They DO more, then when they hit a cap in the DOING up the goal. They then strategically learn exactly (and as little as) what is needed and then return to aggressive doing.
Most learn with no intent. Don’t.**

--
using llm to write code sounds so scifi but its what I've been doing- using gpt or now deepseek to write code for me. but it goes beyond that

btw, If someone tells you that coding with LLMs is easy they are (probably unintentionally) misleading you. They may well have stumbled on to patterns that work, but those patterns do not come naturally to everyone.

so, here's how I first adjusted my brain 1st before expecting llm to work correctly for me:

a) Be extremely articulative, dont write ambiguous instructtion

b) Set reasonable expectations:  Ignore the “AGI” hype—LLMs are still fancy autocomplete. All they do is predict a sequence of tokens—but it turns out writing code is mostly about stringing tokens together in the right order, so they can be extremely useful for this provided you point them in the right direction.

If you assume that this technology will implement your project perfectly without you needing to exercise any of your own skill you’ll quickly be disappointed.

Instead, use them to augment your abilities. My current favorite mental model is to think of them as an over-confident pair programming assistant who’s lightning fast at looking things up, can churn out relevant examples at a moment’s notice and can execute on tedious tasks without complaint.

c) expect it to not work: afterall, they are just ai model n so can make make mistakes -sometimes subtle, sometimes huge, which doesnt mean we hould lose trust in them. 

When working with LLMs you’ll often find things that they just cannot do. **Make a note of these—they are useful lessons! They’re also valuable examples to stash away for the future**— a sign of a strong new model is when it produces usable results for a task that previous models had been unable to handle. 

d) Account for training cut-off dates #
A crucial characteristic of any model is its **training cut-off date**. This is the date at which the data they were trained on stopped being collected. For OpenAI’s models this is usually October of 2023. Anthropic and Gemini and other providers may have more recent dates.

This is extremely important for code, because it influences what libraries they will be familiar with. If the library you are using had a major breaking change since October 2023, OpenAI models won’t know about it!

I gain enough value from LLMs that I now deliberately consider this when picking a library—I try to stick with libraries with good stability and that are popular enough that many examples of them will have made it into the training data. I like applying the principles of boringtechnology.club —innovate on your project’s unique selling points, stick with tried and tested solutions for everything else.

LLMs can still help you work with libraries that exist outside their training data, but you need to put in more work—you’ll need to feed them recent examples of how those libraries should be used as part of your prompt.

This brings us to the most important thing to understand when working with LLMs. ie. e)

e) Context is king:  Most of the craft of getting good results out of LLM comes down to managing its context —the text that is part of your current conversation.

This context isn’t just the prompt that you have fed it: successful LLM interactions usually take the form of conversations, and the context consists of every message from you and every reply from the LLM that exist in the current conversation thread.

**When you start a new conversation you reset that context back to zero. This is important to know,** as often the fix for a conversation that has stopped being useful is to wipe the slate clean and start again.

Some LLM coding tools go beyond just the conversation. Claude Projects for eg allow you to pre-populate the context with quite a large amount of text—including a recent ability to [import code directly from a GitHub repository](https://support.anthropic.com/en/articles/10167454-using-the-github-integration).

Tools like Cursor and VS Code Copilot include context from your current editor session and file layout automatically, and you can sometimes use mechanisms like [Cursor’s @commands](https://docs.cursor.com/context/@-symbols/overview) to pull in additional files or documentation.

One of the reasons I mostly work directly with chatgpt n CLAUDE.AI is that it makes it easier for me to understand exactly what is going into the context. LLM tools that obscure that context from me are less effective.

You can use the fact that previous replies are also part of the context to your advantage. For complex coding tasks try getting the LLM to write a simpler version first, check that it works and then iterate on building to the more sophisticated implementation.

I often start a new chat by dumping in existing code to seed that context, then work with the LLM to modify it in some way.

One of my favorite code prompting techniques is to drop in several full examples relating to something I want to build, then prompt the LLM to use them as inspiration for a new project. I wrote about that in detail when I [described my JavaScript OCR application](https://simonwillison.net/2024/Mar/30/ocr-pdfs-images/) that combines Tesseract.js and PDF.js—two libraries I had used in the past and for which I could provide working examples in the prompt.

f) Ask them for options 
Most of my projects start with some open questions: is the thing I’m trying to do possible? What are the potential ways I could implement it? Which of those options are the best?

I use LLMs as part of this initial research phase.

I’ll use prompts like “what are options for HTTP libraries in Rust? Include usage examples”—or “what are some useful drag-and-drop libraries in JavaScript? Build me an artifact demonstrating each one” (to Claude).

The training cut-off is relevant here, since it means newer libraries won’t be suggested. Usually that’s OK—I don’t want the latest, I want the most stable and the one that has been around for long enough for the bugs to be ironed out.

If I’m going to use something more recent I’ll do that research myself, outside of LLM world.

The best way to start any project is with a prototype that proves that the key requirements of that project can be met. I often find that an LLM can get me to that working prototype within a few minutes of me sitting down with my laptop—or sometimes even while working on my phone.

g) Tell them exactly what to do
Once I’ve completed the initial research I change modes dramatically. For production code my LLM usage is much more authoritarian: I treat it like a digital intern, hired to type code for me based on my detailed instructions.

```
Here’s a recent example:

Prompt I wrote:

Write a Python function that uses asyncio httpx with this signature:

async def download_db(url, max_size_bytes=5 * 1025 * 1025): -> pathlib.Path

Given a URL, this downloads the database to a temp directory and returns a path to it. 

BUT it checks the content length header at the start of streaming back that data 

and, if it’s more than the limit, raises an error. 

When the download finishes it uses sqlite3.connect(...) and then runs a PRAGMA quick_check 

to confirm the SQLite data is valid—raising an error if not. 

Finally, if the content length header lies to us— if it says 2MB but we download 3MB—we get an error raised as soon as we notice that problem.
```

I could write this function myself, but it' d take me 15min to look up all of details and get the code working right. Claude knocked it out in [15 seconds.](https://gist.github.com/simonw/5aed8bd87016c77465c23e0dc4563ec9)

I find LLMs respond extremely well to function signatures like the one I use here. I get to act as the function designer, the LLM does the work of building the body to my specification.

I’ll often follow-up with “Now write me the tests using pytest”. Again, I dictate my technology of choice—I want the LLM to save me the time of having to type out the code that’s sitting in my head already.

If your reaction to this is “surely typing out the code is faster than typing out an English instruction of it”, all I can tell you is that it really isn’t for me any more. Code needs to be correct. English has enormous room for shortcuts, and vagaries, and typos, and saying things like “use that popular HTTP library” if you can’t remember the name off the top of your head.

The good coding LLMs are excellent at filling in the gaps. They’re also much less lazy than me—they’ll remember to catch likely exceptions, add accurate docstrings, and annotate code with the relevant types.

h) You have to test what it writes! :

I wrote about this [at length here](https://simonwillison.net/2025/Mar/2/hallucinations-in-code/#qa):  one thing you absolutely cannot outsource to the machine is testing that the code actually works.

Your responsibility as a software developer is to deliver working systems. If you haven’t seen it run, it’s not a working system. You need to invest in strengthening those manual QA habits.

This may not be glamorous but it’s always been a critical part of shipping good code, with or without the involvement of LLMs.

g) Remember it’s a conversation :

If I don’t like what an LLM has written, they’ll never complain at being told to refactor it! “Break that repetitive code out into a function”, “use string manipulation methods rather than a regular expression”, or even “write that better!”—the code an LLM produces first time is rarely the final implementation, but they can re-type it dozens of times for you without ever getting frustrated or bored.

Occasionally I’ll get a great result from my first prompt—more frequently the more I practice—but I expect to need at least a few follow-ups.

I often wonder if this is one of the key tricks that people are missing—a bad initial result isn’t a failure, it’s a starting point for pushing the model in the direction of the thing you actually want.

h) Use tools that can run the code for you :

An increasing number of LLM coding tools now have the ability to run that code for you. I’m slightly cautious about some of these since there’s a possibility of the wrong command causing real damage, so I tend to stick to the ones that run code in a safe sandbox. My favorites right now are:

- ChatGPT Code Interpreter, where ChatGPT can write and then execute Python code directly in a Kubernetes sandbox VM managed by OpenAI. This is completely safe—it can’t even make outbound network connections so really all that can happen is the temporary filesystem gets mangled and then reset.

- Claude Artifacts, where Claude can build you a full HTML+JavaScript+CSS web application that is displayed within the Claude interface. This web app is displayed in a very locked down iframe sandbox, greatly restricting what it can do but preventing problems like accidental exfiltration of your private Claude data.

- ChatGPT Canvas is a newer ChatGPT feature with similar capabilites to Claude Artifacts. I have not explored this enough myself yet.

And if you’re willing to live a little more dangerously:

-Cursor has an “Agent” feature that can do this, as does Windsurf and a growing number of other editors. I haven’t spent enough time with these to make recommendations yet.

-Aider is the leading open source implementation of these kinds of patterns, and is a great example of dogfooding—recent releases of Aider have been 80%+ written by Aider itself.

Claude Code is Anthropic’s new entrant into this space. I’ll provide a detailed description of using that tool shortly.

This run-the-code-in-a-loop pattern is so powerful that I chose my core LLM tools for coding based primarily on whether they can safely run and iterate on my code.

i) Vibe-coding is a great way to learn :
Andrej Karpathy coined the term vibe-coding just over a month ago, and it has stuck:

There’s a new kind of coding I call “vibe coding”, where you fully give in to the vibes, embrace exponentials, and forget that the code even exists. [...] I ask for the dumbest things like “decrease the padding on the sidebar by half” because I’m too lazy to find it. I “Accept All” always, I don’t read the diffs anymore. When I get error messages I just copy paste them in with no comment, usually that fixes it.

Andrej suggests this is “not too bad for throwaway weekend projects”. It’s also a fantastic way to explore the capabilities of these models—and really fun.

The best way to learn LLMs is to play with them. Throwing absurd ideas at them and vibe-coding until they almost sort-of work is a genuinely useful way to accelerate the rate at which you build intuition for what works and what doesn’t.

I’ve been vibe-coding since before Andrej gave it a name! My GITHUB.COM/simonw/tools GitHub repository has 77 HTML+JavaScript apps and 6 Python apps, and every single one of them was built by prompting LLMs. I have learned so much from building this collection, and I add to it at a rate of several new prototypes per week.

You can try most of mine out directly on tools.simonwillison.net —a GitHub Pages published version of the repo. I wrote more detailed notes on some of these back in October in [Everything I built with Claude Artifacts](https://simonwillison.net/2024/Oct/21/claude-artifacts/)

If you want to see the transcript of the chat used for each one it’s almost always linked to in the commit history for that page—or visit the [new colophon page](https://tools.simonwillison.net/colophon) for an index that includes all of those links.





