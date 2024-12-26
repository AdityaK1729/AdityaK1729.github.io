---
layout: page
title: WiDS 4.0
subtitle: Probability-Based IPL Simulator
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
## Week 2,3
Its time to make our original model now, the thing which you guys took this project for. To make the results more realistic, we will be using IPL 2025 squads after the recentmost IPL auction. [Here](https://www.espncricinfo.com/series/ipl-2025-1449924/squads) are the squads, we only need the main playing 11s, so we can ignore rest of the things, so for playing 11, either you can use your own cricket expertise and make your playing 11s, or just use mine linked [here](https://adityak1729.github.io/Projects/WiDS4/playing11.txt).  
Now once we have playing 11s, now lets come to the dataset, to make the predictions more reliable we will be using all 3 of the ball by ball datasets i.e. 2022.csv, 2023.csv, 2024.csv. A nice idea could be to just merge all 3 into 1.  
Next thing we do is get player by player distribution, for now you may ignore extras (if you find a way to work around that its nice), so leaving extras, make each batsman and bowler's distribution. This distribution will be something like this:
```
XYZ bowling: 1:100, 2: 19, 3: 1, 4: 28, 6:49, W: 13, Total: 210
# The above values are just arbitary, this is what you need to find by code
```
Also since there are some new players in each team, so another thing we need to do is assign some global data to them, now for this if you have a better method in mind go with that. Otherwise, firstly get global distribution (i.e. independent of the player). Then take some value of cutoff number of balls, such as say 60, w if a player has played less than 60 balls, complete the remaining distribution from the global distribution (might near it down to integers). So now for each player we have atleast 60 balls of data. Now an issue here is that when we do this, we are not keeping the batsman's position in mind, but for this project we can ignore this, as we are averaging out everything so it works just fine.  
An important thing to note here is we need to complete this for just the allrounders and bowlers 
### Single Match Simulation
Once we have 
## Dataset
Here is the dataset 
[IPL 2024 Ball-by-Ball Dataset](https://www.kaggle.com/datasets/sahiltailor/ipl-2024-ball-by-ball-dataset). Credits to Kaggle user [Sahil Tailor](https://www.kaggle.com/sahiltailor) for the dataset.
