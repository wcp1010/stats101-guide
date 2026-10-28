pasted from https://prodduke-my.sharepoint.com/:w:/r/personal/wcp19_duke_edu/Documents/STATS101%20GUIDE.docx?d=w92bab80e954541baa694630669ff42d3&csf=1&web=1&e=AqQs2z

Introductory guide to STATS101: 

How to avoid making an easy class difficult.  

Why this class can be hard:	 

Many people taking this class do not code, and do not wish to code. These people often struggle with programming, and this struggle/difficulty/confusion generalizes, reducing their understanding of the course concepts (often, enough that they struggle on the midterm). As a result, they spend a lot of time doing work for this class, yet get very little out of this work. 

This can be avoided: just don’t code. All AI use is allowed, and while this does not mean AI should do your HW for you (it shouldn’t; you will not receive even decent grades; you will be unhappy), it does mean AI should write just about every line of code that is produced for this class. It should also run checks, compile, and so forth; your job on the HWs (1, 2, 3) is to: 

A) make predictions, thinking about how you expect the data to behave, and why; 

B) analyze the data, attempting to falsify your seemingly correct predictions, and attempting to understand what went wrong with your seemingly incorrect predictions; (you should also try to find unexpected behavior and explain what causes it/what it is) 

C) explain your findings, and how they verify or falsify your predictions.  
 
 

I would recommend writing the text sections in the text editor of your choice. If you are opening R and typing <-, you are probably doing something wrong.  

I’m going to explain the path of least resistance to the minimum viable coding setup (i.e., the easiest-to-achieve setup where you do not cost yourself (egregiously) many hours and much sanity). Then, I’ll give you some resources which will make the work of the class easier, explain general principles which help you perform well in the class, and give a short guide for the graph competitions; I’ll conclude with my HW3, because I think it give you the best intuitions about what a good project might look like without spoiling any of the fun of the projects for you. (Try to use it to help you think about what you might want to do, and what you might want to make, not as something to emulate; that’s never a good idea.) 

(If you already know how to code, I’d recommend running agent teams through tmux, or using a long-running agent with a modified memory system.) 

 

1: Setup  

(Preliminary requirement: you will need an account with a model provider; I highly recommend Claude, due to the slightly superior performance and moderately more generous subscription limits when compared with ChatGPT/Qwen/Kimi/etc.; the $20/month tier is sufficient for this. I will assume you are using Claude for this, but ChatGPT works similarly. I assume the Chinese models do as well. Not that I would ever recommend a non-Ant/OAI model for this.) 

(I highly recommend using Claude Code through the CLI of your choice. However, this guide will presume the level of technical literacy that makes this sketchy, and as such if you are interested in setting this up, I recommend asking Claude to help you through it (or searching for a guide).) 

Setup steps: 

Download the Claude app, and sign in.  

Make a folder called STATS101 somewhere reasonable on your computer, and put startup.md (link) in it. 

Start a new conversation, give it access to the STATS101 folder, drag startup.md in, and say "Follow startup.md." 

It’ll ask you questions or ask you to allow actions/change settings; unless it says something along the lines of ‘let me run rm -rf  ~ :)’, go along with it. (Broadly, this is very, very bad advice. Don’t normally do this. If you want to be careful, you can ask another Claude instance to explain each step. However, I pinky promise I’m not up to anything.) 

Don’t be horribly rude to Claude while it guides you through the rest of the process.  

2: How to approach a HW 

Luckily, I’ve included all the relevant information inside the startup.md. It should be enough to get you started finding your own method. Simply give Claude the project info from teams, and ask for it to understand and plan the homework; you should get something decent in response. Of course, this is not a reason not to read the project, or know what you are doing, but this should prevent you wasting huge quantities of time struggling to begin.  
 
3: How to approach the graph competition 

The graph competitions are run soon after a HW is due and reward the winner with a five percent higher score on the project. They take very little time to enter, so you have no reason not to submit something; you’d be surprised just how likely you are to win.  

If you only have fifteen minutes, just talk with Claude to improve/rework your best graph from the HW for the competition. If you have more than this much time, I’d recommend thinking about something that you can do with the data that is interesting, and how it could be visualized in a convincing manner. Graph competition entries are projected on the board; go with a light theme. For an example of what a good entry looks like, this was my winning entry to the second competition: 

 

However, you can win a graph competition with something much worse than this. Just an interesting graph that isn’t actively harmful to look at will probably get you the points.  

4: Links to my HW3 
 
HW3: https://wcp1010.github.io/retraction-watch-report/ 

Link to startup file again: https://github.com/wcp1010/stats101-guide/blob/main/startup.md 

 

5: Where to go from here? 
 
With technical setup, I’d recommend going from this to in-app Claude Code (very similar and easy) to Claude Code for the CLI (use Ghostty, if you don’t already have a preference). From there, you can adapt to what works best for you and your workflows.  

 

In terms of doing well on the assignments, I think exposure to text showcasing good epistemic habits is probably the most efficient way to study outside of simply spending a lot of time producing good work. When it comes to prestige papers, I’d recommend reading the FT; LessWrong (lesswrong.com) and ACX/SSC are somewhat more casual or fun, and often quite high quality; I’d particularly emphasize reading Beware the Man of One Study, Debunked and Well-Refuted , and The Control Group Is Out Of Control for their statistical relevance, but Meditations on Moloch, I Can Tolerate Anything Except the Outgroup, and The Anti-Reactionary FAQ are all good places to start.  

When it comes to understanding statistics/specific course concepts, I recommend working problems or, should they exist for the topic, highly recommend watching 3Blue1Brown videos.  

 

 
 
 

 
