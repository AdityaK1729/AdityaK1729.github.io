---
layout: page
title: Week 1 Assignment
subtitle: why do you need a subtitle
---

## The Problem Statement
The thing which we are ultimately going to do is make a logic for game by game simulation, and run a loop of it for 70 games of the league phase, so for week 1 this is what we are going to do right now, so here are the details of what exactly you need to do: (use jupyter notebook/google colab for easy coding, if you dont know how to use, follow this tutorial https://www.youtube.com/watch?v=5pf0_bpNbkw)
1. Import the dataset, from the dataset, take schedule of 2024 season, we will use this schedule as a reference.
2. For each of the above game, using the random module, pick a random winner for each game, but wait there is a twist, select any logic you like to pick a random score of each inning for each team, and whatever is the result based on it, assign 2 points for a win, 1 for a tie and so on, and mantain a points table.
3. Create a tie-breaker mechanism for breaking ties using score difference (basically what you need to do is after each game, add +(your score-opponent score) to the present score difference (start from 0). (If there are still ties, you might just use alphabetical order, or anything you like, just mention it in the code as a comment)
4. At the end of league phase, using top 4 teams, make a playoff logic (given below if you don't know) , and hence pick the winner, and then fill whoever won in the form below.  
NOTE: For random, use any seed, but just make sure to write the seed at the beginning of the notebook as a comment or so, just dont have non deterministic seed, predeclare it, so that even on running again code gives same output. (I have put it in the form as well)
Submit your assignment [here](https://forms.gle/wmLKH8JGTd5bmt5s6). Upload the annotated notebook to github, and hence share the link to github repo, or just directly share the google colab link, whatever you wish. What I would suggest is to create and mantain a github repo, so that it will be easier for you to look at the complete project at one place, whenever you come back at it.
Feel free to DM me over whatsapp for any issue you face, Happy Coding!
