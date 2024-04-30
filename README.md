# **Colorado Avalanche Goal Prediction through Machine Learning**

MSDS696: Data Science Practicum II

Author: Lonny Cox-Lauf

Link to presentation recording: LJC TO DO add this!

## High-Level Project Description

This code trains Machine Learning binary classifier models to predict whether shots taken by the Colorado Avalanche team resulted in goals.

## Purpose and Motivation

In the sport of hockey, as with all sports nowadays, stat analytics has been highly prevalent in recent years. This is partially due to increase in technology and database capabilities for holding vast amounts of team and player data, but also it is prevalent because analysts and franchises are catching on to the many benefits that it can offer. For example, further statistical analysis on expected goals in the National Hockey League (NHL) can result in:

* Coaching and play design for their teams (taking "smarter" shots during games)
* Building more fan engagement, as fans will enjoy more commentator discussion on expected goals versus actual goals
* More media coverage options, such as adding shot statistics real-time to the streams or during replays, amplifying the experience
* Increased revenue, as sponsorship on certain statistical analysis portions during game coverage ("shot speed, brought to you by Toyota", etc.)

## Dataset Description

Money Puck's website has historical shot-related data from NHL games starting from way back in the 2007-2008 season (in CSV format). This data contains shots from all the NHL teams, and every single unblocked shot is recorded. There are a total of 124 attributes for each of these shots. In total, there are 1,717,746 shots when adding all of the CSV files together for each season (from the 2007-2008 season through the 2022-2023 season). Money Puck updates the CSV file for the current season (2023-2024) regularly with new shot data as the games occur. Money Puck scrapes most of this shot data from the ESPN and NHL websites.

**Link to the dataset**: https://moneypuck.com/data.htm

## Data Cleaning

Some steps taken to clean the NHL shot-related data to fit my project's needs were as follows:

* Remove games that did not involve the Avalanche 
* Remove empty net shots
* Remove shots taken by the team opposing the Avalanche
* Remove any duplicate or unneccesary attributes (columns)
* Generate new features based on existing features, such as Power Play vs. Even Strength or Home vs. Away game
* Fill in missing shot type data with "Wrist", as wrist shots are the most common in hockey
* Fill in missing player position data with "Center", as Centers historically take more shots than any other position in hockey
* And more...

The biggest challenge, however, was addressing the data imbalance between the number of goal samples versus the number of non-goal samples. In other words, the Avalanche have taken almost 58,000 shots since 2007, but only about 4,000 of those shot went into the net. That means the ratio of goals to non-goals is only approximately 0.07295. Ideally, to train a model we would like that ratio to be closer to 0.5. To address this imbalance, we oversample the minority set (goals) using synthetically generated data, while we strategically undersample the majority (non-goals) to make the decision boundary a little more obvious.

