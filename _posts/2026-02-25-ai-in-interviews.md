---
layout: post
title: Interviewing for AI Positions
date: 2026-02-25 08:00:00
description: Thoughts on interviews with and without AI while interviewing for AI positions
tags: career AI interview leetcode
categories: journal
thumbnail: assets/img/4.jpg
---


I have recently restarted my journey to find a new role in an organization that I can see myself spending years and years in, and at times, I was happy to learn the process hasn’t changed much and curious to learn some organizations are experimenting with newer approaches. That said, for the majority of the ones I was exposed to, much hasn’t changed. 

## Where I’m coming from and where I’m at

For the past 5 to 6 years, I have been knee-deep in the startup world. One of my dreams has always been to collaborate with a group of founders in creating something from scratch and, obviously, successfully. I am a very optimistic individual, and, as it happens with any young person, they think themselves invincible. They can do and achieve anything they set their minds to. 

I got to live that dream, and I was able to help create a team of brilliant, underrepresented, and talented engineers in one of these journeys. It was beautiful while it lasted. Unfortunately, the startup world is still very toxic, demanding, and intense. That ended up taking a toll on my physical and mental health, and I saw myself out the door. It took some time to reset both my mind and body, and today I’m in a much better place. Years later.

Since then, I have taken a few roles, one for the federal government during the current administration, where I thought I was going to be able to contribute and stay for years and years. Unfortunately, none of them panned out, and here I find myself again looking for new opportunities. Opportunities that aren’t toxic, have a good life-work balance, present the potential of working with thoughtful people, and, the most important part, open the door to spend many years as an engineer working on my technical and designing skills.

## Algorithms and Leetcode

Recently, I participated in an interview process for an AI/ML position, and I was a bit surprised to learn about their interview process. It was the old-school method: no AI tools, no take-home (which I even prefer), a technical Zoom interview with 2 engineers, a LeetCode /HackerRank problem, an on-site interview with a bunch of people (3+ hours), and whiteboarding.

Given the direction of technology, I didn’t think I was ever going to need to practice and study LeetCode problems again, so I asked for a few days in advance to practice for the technical. Initially, I found myself like an old car that hadn’t been turned on in a while. That dusty old car with a carburetor in the back of the garage had been covered for years. I felt heavy and slow.

It is important to note that in my most recent role, the majority of the team was vibe coding their new features and fixing production-level bugs on a daily basis. For the most part, that was working pretty well, and we learned a bunch of interesting techniques. Needless to say, I wasn’t ready to take LeetCode problems, hashing, sliding windows, and not even two-pointer problems. It is incredible how vibe coding and AI coding assistance will hinder you. I thought to myself: “Holy …., I’m bad”. I wonder if anyone else feels the same?

A few days later, I was in the groove. Any free time I had, I found myself practicing and re-learning the algorithms, the patterns. After a few days, I was addicted again to the process of solving problems. I realized how much I had missed that. There is something about solving problems, about writing your own code that culminates in this moment of feeling so successful. When I first re-experienced this, I realized: “Woah, what have I been doing?”. I missed that feeling so much. I’m not brilliant, at all, and I’m not afraid to say that some problems took me hours to solve. But, sticking to them allowed me to learn the proper pattern, learn new support data structures to aid in my solution, and much more. Not looking for an answer, not asking AI to help me was big.

I missed that.

## Interviewing

Back to the interview. 

With a few days to practice, I decided to focus only on two pointers and sliding window algorithms, which I thought I could cover given the time I had. Unsurprisingly, I had a 2-D array hashing problem to solve. Welp, I did poorly, but right at the end, I gave them something that I believed would help tip the scale (very lightly) in a positive way. I described and wrote some pseudo code showing them how I could use a dictionary to count the number of occurrences and calculate the answer. I think that helped. To be fair, I have no idea.

I pretty much had given up because I knew deep down it was a poor solution. To my surprise, they invited me to an on-site visit for a half-day of interviews. So I prepared for those a bit more.

The structure for the final on-site interview followed:

- AI Case Study
- Behavioral
- Behavioral (with Manager)

### AI Case Study

Simple problem that required me to ask a few clarification questions and whiteboarding a solution to assist with the problem described by the interviewers. The problem was simple:

1. Automate a certain matching task needed for insurance (The company was in the Healthcare segment)
2. Reduce the time needed to make that code/problem matching
3. Remove the admin in the middle that was performing that task manually

The solution I presented was also simple to follow:

1. Leverage an AI Agent that was in charge of orchestrating the entire flow and keeping the connection alive and open with the caller/consumer
2. That would trigger another AI agent and SLM to leverage some information kept in a vector database, leveraging existent algorithms to find insurance codes or relevant information that matched the consumer’s request. 
    1. For example, if the patient had diabetes, how many insurance codes can we retrieve that actually makes sense for their profile and information we have about their case? 
3. Use the information from #2 to run a classification model on the PCP’s notes to find some correlation
4. Run a recommendation model, fine tuning parameters
5. Add a human step at the end to validate the process
6. Track everything and make adjustments where necessary

Without going into much detail, that was the design I presented. Based on my most recent experience working as a tech lead for a startup in the AI space, I was pretty confident this would be a good starting point that I had validated in the real world already.

One thing that caught the eye of the interviewer was the step to cross-reference the PCP’s information, like demographics, age, style, specialty, and build a custom model to assist with the recommendation. At the end, off of thousands of codes, the idea was to narrow down to double digits and have a ranking system. Run that by the human at the end to help build the confidence in the system we built.

They seemed to be entertained, which left me confident for the next two interviews.

### Behavioral Interviews

Both were decent. Nothing interesting to be honest and nothing that is worth remembering. Bread and butter with questions that we usually get in these type of interviews. 

### Feedback

At the end, I didn’t get the position. Which is fine. That said, I asked for feedback because I want to be better prepared for similar positions in the future, and to my surprise, I got no response. It did leave a bad taste in my mouth not having that final feedback that, in my view, is crucial for me to understand where I may have made mistakes in the process.

I still think my technical skills weren’t as strong as they should be, and the more I think about it, the more I realize that could have been the deciding factor. But again, it’s a full AI/ML position.

  ¯\*( ͡° ͜ʖ ͡°)*/¯

## Final Thoughts

It’s hard to predict where things are going and what the recruiting process is going to be like. Some companies are running recruitment as if it was 2010 and others are in the middle. 

Personally, now that I have been exposed to both, I would like 2-part exercise:

1. Simple coding python problem
2. Simple agentic AI coding 

Both can be done in under an hour. You don’t need something more than a hashing exercise to test someone’s Python skill, and you should check how they interact with coding agents, agentic IDEs, planning and implementation modes, skills, and instructions.