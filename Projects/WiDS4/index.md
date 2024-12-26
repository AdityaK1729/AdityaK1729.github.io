---
layout: post
title: WiDS 4.0
subtitle: Probability-Based IPL Simulator
mathjax: true
gh-repo: AdityaK1729/AdityaK1729.github.io
gh-batch: [star, fork, follow]
author: Aditya Khambete
---

# Probability Based IPL Simulator

## Description
We will develop an IPL simulator model similar to how FIFA/EAFC simulates football games. We will use existing datasets to create a probability distribution based on different parameters, and using this new data, we will make a prediction for who wins IPL 2025.

## Resources for Week 1 (13th December-19th December)
For week 1, we will start with some basics of Python and a few libraries. If you have some good resources yourself, feel free to follow that. Otherwise, use the following:
- [Python Tutorial](https://www.w3schools.com/python) Do upto functions here.
- [NumPy Tutorial](https://www.w3schools.com/python/numpy) Mainly we will be using NumPy Random, so focus on that.
- [Pandas Tutorial](https://www.w3schools.com/python/pandas) This is important for importing and playing around with the dataset.

If you are already familiar with python, you might play around and explore a bit of the dataset (which you can find below on this page). 

Roughly what we are going to do is analyse each player in the dataset, that how he score runs, and the exact probability distribution on each ball, then we will run the simulation bowler against the batsman (based on the exact team matchup), and based on the points table and playoffs, we will predict the winner. You can find a really basic version of the idea [here](https://github.com/AdityaK1729/IPLProbSimulator).

Soon, I will post an assignment based on the above concepts, which will be a mandatory requirement for certification, as I don't want this to be just one-day coding project, so I sincerely request you to all the above-mentioned tasks this week only.
### Week 1 Assignment
Find it [here](https://adityak1729.github.io/Projects/WiDS4/Week1Assignment/)
## Week 2,3 {#Week-2and3}
Its time to make our original model now, the thing which you guys took this project for. To make the results more realistic, we will be using IPL 2025 squads after the recentmost IPL auction. [Here](https://www.espncricinfo.com/series/ipl-2025-1449924/squads) are the squads, we only need the main playing 11s, so we can ignore rest of the things, so for playing 11, either you can use your own cricket expertise and make your playing 11s, or just use mine linked [here](https://adityak1729.github.io/Projects/WiDS4/playing11.txt).  
Now once we have playing 11s, now lets come to the dataset, to make the predictions more reliable we will be using all 3 of the ball by ball datasets i.e. 2022.csv, 2023.csv, 2024.csv. A nice idea could be to just merge all 3 into 1, and remove the unnecessary columns and/or rows.
Next thing we do is get player by player distribution, for now you may ignore extras (if you find a way to work around that its nice), so leaving extras, make each batsman and bowler's distribution. This distribution will be something like this: 
```python
XYZ bowling: 1:100, 2: 19, 3: 1, 4: 28, 6:49, W: 13, Total: 210
# The above values are just arbitary, this is what you need to find by code
```
Also since there are some new players in each team, so another thing we need to do is assign some global data to them, now for this if you have a better method in mind go with that. Otherwise, firstly get global distribution (i.e. independent of the player). Then take some value of cutoff number of balls, such as say 60, w if a player has played less than 60 balls, complete the remaining distribution from the global distribution (might near it down to integers). So now for each player we have atleast 60 balls of data. Now an issue here is that when we do this, we are not keeping the batsman's position in mind, but for this project we can ignore this, as we are averaging out everything so it works just fine.  
An important thing to note here is we need to complete this for just the allrounders and bowlers for the bowling dataset, as batters wont bowl. So for classifying batters and bowlers, a possible idea is to take the ratio of the games that player has played and the games in which he has bowled, if that ratio is >0.5 for example, we might consider this player an allrounder. After that adjust the batting order so that all players who can bowl are below, even if you dont do that, atleast assign some boolean variable to each allrounder/bowler to make sure he can bowl. 
### Single Match Simulation
Once we have the above dataset ready, we are ready to find what a match would look like, now there are numerous factors even in a single game, so for simplicity here is what is a proposed plan, if you have a better idea, feel free to follow that.  
- First of all, randomly decide who will bat first.
- Say team A is batting, so for each over assign one bowler, with a limitation of max 4 overs per bowler. Here you might use some other method to assign bowlers, for example preassign bowling order for each team etc, all that you are free to do.
- For simplicity, consider only 1 batsman is at the crease for 1 over, and it alternates between the overs, and changes on fall of wicket, this is to make the simulation process easier.
- Now, to simulate a batsman vs bowler matchup, just use the batting dataset of batter, and bowling dataset of bowler, and to simulate the matchup, use those datasets to make a combined dataset, and with the weights of the combined dataset, simulate each bowl. To combine dataset, an easy idea might be to just add all the corresponding values of the dataset, and make that the combined dataset, this algorithm takes the experience into account as well.
Thats it, repeat this for 20 overs, then change the team, and do this till target is achieved/10 wickets fall down/20 overs are done.

### Season Simulation
This is the easy bit, now there are some choices you need to make here, firstly do you want to update the dataset of players each game on their performance, secondly are you comfortable handling the net run rate calculations, etc. Brownie points if you track other data such as orange cap/purple cap (most runs and wickets resp.) also. Now for NRR calculations used for tiebreaks, here is the formula-  
$$ NRR=\frac{Total Runs Scored Throughout Season}{Overs Batted Throughout Season}-\frac{Total Runs Conceded Throughout Season}{Overs Bowled Throughout Season} $$  
Note: We consider all out to be 20 overs bowled/batted by the respective teams, regardless of how quick you were bowled out.  
I would recommend to use NRR only, as its not something too hard to implement, but still if you find it too hard, the thing you might do is just simulate each game till the full 20 overs, irrespective of whether the team won already (We anyways consider all out to be 20 overs batted only as above mentioned), and then just use the score difference logic you used in week 1 assignment.  
For the schedule just use the first 70 columns (so that you dont include the playoffs) of the matches.csv file from the dataset for the league games (just like you did in week 1 assignment). Now once this is done, the thing you need to do is just use the old code from week 1 assignment and based on that simulate the whole tournament. That's it, you have successfully completed the project.  
{: .box-note}
As I said in the week 1 assignment, use constant seed for all the random simulations, as that makes it a lot easier.

## Week 4
This week is mainly buffer, if you have completed the project well and good, you might want to incorporate and record some more things, such as orange  cap/purple cap leaderboard etc, you might want to incorporate more factors such as home advantage, etc. This is just totally upto you.  
If you havent done the code already, this week will be for just that.

## Submission Guideline
For the final code submission, include these things in your notebook: 
- head of your players dataset csv file
- a single example game simulated with full scorecard
- the points table
- the playoffs schedule and results (with scores)
- the final result and scores

## How to code this
This file mainly deals with the algorithm, for specificities about code that how exactly to code it, refer this section. This is empty for now, so that you can think for some days atleast. I will be updating this in 4-5 days.
## Dataset
Here is the dataset 
[IPL 2024 Ball-by-Ball Dataset](https://www.kaggle.com/datasets/sahiltailor/ipl-2024-ball-by-ball-dataset). Credits to Kaggle user [Sahil Tailor](https://www.kaggle.com/sahiltailor) for the dataset.
