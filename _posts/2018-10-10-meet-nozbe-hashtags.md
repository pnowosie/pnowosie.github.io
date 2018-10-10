---
layout: post
title: "Meet Nozbe hashtags"
date: 2018-10-10 21:34:11 +0200
---

As an introduction to this technical post, let me tell you that I discovered [Nozbe](https://nozbe.com) quite recently. My good friend [Bogusz from Startup My Way](http://startupmyway.com/) recorded a [podcast](http://startupmyway.com/smw-podcast-012-michal-sliwinski-budowa-startupu-od-1-do-500-tys-uzytkownikow-czyli-jak-powstala-aplikacja-nozbe/)(in Polish) with *Nozbe*'s creator [Michal Śliwiński](https://twitter.com/MSliwinski). What I found out from the talk Michal is running his company entirerly remotely and as a task manager they're using *Nozbe* (of course).

Michal has convinced me to create an account in *Nozbe* and then I let my month trial period pass. Only then I back to it's free plan and discovered it has some nice features that could gain me reduction of some obstacles I had in my former stack. This is how I became a *Nozber* ;)

Ok, but whole this isn't about productivity or people.

### Creating tasks

As described in [Nozbe help](https://help.nozbe.com/l/en/article/paO1EXJGLB-hashtags#hashtags) there is a quicker way to set task's details like project, due date or categories. Meet hashtag commands.

`New task title #PROJECT #DATE [#CATEGORY1 ...] #PERSON-TO-DELEGATE ##This is comment which will be included`

#### Date format
to add a specific date and time the format used should be for example: „#January 10 11:00" - this will make an action set to the nearest 10th of January for 11 a.m.

#### Delegation
Hash followed by person name will do the trick, however sometimes, there is more than one person with the same name. The use account email address of the person #email@example.com

**Delegating to yourself** Your name wouldn't work use **#You** instead. 

I don't use delegation yet.

#### And add a comment immediately
Use double hashes and write a comment which will be included in task.

### Creating tasks via email

[Here](https://help.nozbe.com/l/en/article/pSxj2VdB62-email-tasks#emailtask) is feature description. Above #hashtag rules are applied!

#### but there is more
You can create bunch of task with 1 email, just include in the email's body

```
. 1st task title #Project #today
. 2nd task title #Project #Category 
and this become ^task comment

. 3rd task with a checklist
checklist:
(-) todo 1
(-) todo 2
(+) done

--
^ text after 2 dashes will be ignored  
```

#### emailing new comment to existing task
Yep, that's supported too ;)

In the email's title: `Here is an comment title #task: TASK NAME #PROJECT`
In the body one can pass more comment's text.

And by the way, if t happen you have a '#' in your title, make sure you add spaces around it, to no fool the tool.

So as you can see *Nozbe* takes care of its users to makes their lives easier and more pleasant. 