# Introductory guide to STATS101:

How to avoid making an easy class difficult.

### Why this class can be hard:

Many people taking this class are non-technical, and do not wish to be technical, and do not code, and do not wish to code. These people often struggle with programming, and this struggle/difficulty/confusion generalizes, reducing their understanding of the course concepts (often, enough that they struggle in the midterm). As a result, they spend a lot of time doing work for this class, yet get very little out of this work.

This can be avoided: just don’t code. All AI use is allowed, and while this does not mean AI should do your HW for you (it shouldn’t; you will not receive even decent grades; you will be unhappy), it does mean AI should write just about every line of code that is produced for this class. It should also run checks, compile, and so forth; your job on the HWs (1, 2, 3) is to:

> A) make predictions, thinking about how you expect the data to behave, and why;
>
> B) analyze the data, attempting to falsify your seemingly correct predictions, and attempting to understand what went wrong with your seemingly incorrect predictions; (you should also try to find unexpected behavior and explain what causes it/what it is)
>
> C) explain your findings, and how they verify or falsify your predictions.

I would recommend writing the text sections in the text editor of your choice. If you are opening R, you are probably doing something wrong.

I’m going to explain the path of least resistance to the minimum viable coding setup (i.e., the easiest-to-achieve setup where you do not cost yourself (egregiously) many hours and much sanity). Then, I’ll give you some resources which will make the work of the class easier, explain general principles which help you perform well in the class, and give a short guide for the graph competitions; I’ll conclude with my HW3, because I think it is the least likely to be problematic (I could conceivably get in trouble for sharing the others, I think) while giving you the best intuitions about what a good project might look like.

(If you already know how to code, I’d recommend running agent teams through tmux, or using a long-running agent with a modified memory system.)

(Quick aside on why my advice might be worth something; I took this course session one and while HW3 grades are not posted I’m on pace for roughly a ~104% in the class.)

## 1: Setup

(Preliminary requirement: you will need an account with a model provider; I highly recommend Claude, due to the slightly superior performance and moderately more generous subscription limits when compared with ChatGPT/Qwen/Kimi/etc.; the $20/month tier is sufficient for this. I will assume you are using Claude for this, but ChatGPT works similarly. I assume the Chinese models do as well. Not that I would ever recommend a non-Ant/OAI model for this.)

(I highly recommend using Claude Code through the CLI of your choice. However, this guide will presume the level of technical literacy that makes this sketchy, and as such if you are interested in setting this up, I recommend asking Claude to help you through it (or searching for a guide).)

Setup steps:

1. Download the Claude app, and sign in.
2. Make a folder called STATS101 somewhere reasonable on your computer, and put startup.md ([link](https://raw.githubusercontent.com/wcp1010/stats101-guide/main/startup.md)) in it.
3. Start a new conversation, give it access to the STATS101 folder, drag startup.md in, and say "Follow startup.md."
4. It’ll ask you questions, or ask you to allow/change settings; unless it says something along the lines of ‘let me run `rm -rf ~` :)’, go along with it.
5. Don’t be horribly rude to Claude while it guides you through the rest of the process.

## 2: How to approach a HW

Luckily, I’ve included all the relevant information inside the startup.md. It should be enough to get you started finding your own method. Simply give Claude the project info from teams, and ask for it to understand and plan the homework; you should get something decent in response. Of course, this is not a reason not to read the project, or know what you are doing, but this should prevent you wasting huge quantities of time struggling to begin.

## 3: How to approach the graph competition

The graph competitions are run soon after a HW is due and reward the winner with a five percent higher score on the project. They take very little time to enter, so you have no reason not to submit something; the quality of submissions is often quite low.

If you only have fifteen minutes, just talk with Claude to improve/rework your best graph from the HW for the competition. If you have more than this much time, I’d recommend thinking about something that you can do with the data that is interesting, and how it could be visualized in a convincing manner. Graph competition entries are projected on the board; go with a light theme. For an example of what a good entry looks like, this was my winning entry to the second competition:

![Where has Shanghai's air been? Winning graph competition entry](graph-contest.png)

However, you can win a graph competition with something much worse than this. Just an interesting graph that isn’t actively harmful to look at will probably get you the points.

## 4: Links to my HW3

HW3: <https://wcp1010.github.io/retraction-watch-report/>

Link to startup.md: [startup.md](startup.md) ([raw file, to save](https://raw.githubusercontent.com/wcp1010/stats101-guide/main/startup.md))

## 5: Where to go from here?

With technical setup, I’d recommend going from this to in-app Claude Code (very similar and easy) to Claude Code for the CLI (use Ghostty, if you don’t already have a preference). From there, you can adapt to what works best for you and your workflows.

In terms of doing well on the assignments, I think exposure to text showcasing good epistemic habits is probably the most efficient way to study outside of simply spending a lot of time producing good work. When it comes to prestige papers, I’d recommend reading the FT; LessWrong ([lesswrong.com](https://lesswrong.com)) and ACX/SSC are somewhat more casual or fun, and often quite high quality; I’d particularly emphasize reading [Beware the Man of One Study](https://slatestarcodex.com/2014/12/12/beware-the-man-of-one-study/), [Debunked and Well-Refuted](https://slatestarcodex.com/2014/12/13/debunked-and-well-refuted/), and [The Control Group Is Out Of Control](https://slatestarcodex.com/2014/04/28/the-control-group-is-out-of-control/) for their statistical relevance, but [Meditations on Moloch](https://slatestarcodex.com/2014/07/30/meditations-on-moloch/), [I Can Tolerate Anything Except the Outgroup](https://slatestarcodex.com/2014/09/30/i-can-tolerate-anything-except-the-outgroup/), and [The Anti-Reactionary FAQ](https://slatestarcodex.com/2013/10/20/the-anti-reactionary-faq/) are all good places to start.

When it comes to understanding statistics/specific course concepts, I recommend working problems or, should they exist for the topic, highly recommend watching 3Blue1Brown videos.
