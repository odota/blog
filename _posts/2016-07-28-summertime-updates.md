---
layout:     post
title:      Summertime Updates
summary:    Speedy! Quick! Swift! It's YASP!
categories: 
---

It's been a quiet summer for YASP, but we're back with some new features, just in time for TI!

### Compendium Predictions

Stats are useful because you can use them to predict the future. We've taken a look at all the pro games in 6.88 to give
you the best chance of getting your predictions right! Check out our insights [here](https://yasp.co/ti6predictions).

### "Pros" tab
A new tab on each player page now shows the games that that player has played with professional players!
The list is from a Steam API endpoint called GetProPlayerList.

### Denies @ 10
This stat is now available on match pages! A huge Thank You to community developer [@lomash](https://github.com/lomash)
for implementing this feature!!! See how it was done [here](https://github.com/yasp-dota/yasp/pull/1074).

### Ranking Update
We've updated our [ranking system](https://yasp.co/rankings) to more accurately rank the best players at the top. 

We've increased weighting of MMR again for the 2016Q3 ranking cycle, which started 2016-07-01. Essentially, a player 
with half the MMR of another player now needs 64 times as many wins to have the same ranking score.

### DotaCoach

We're proud to announce our new partnership with [DotaCoach](https://dotacoach.org/) to help you improve your game. 
DotaCoach.org is an on demand service sort of like an "Uber" for learning Dota. Review your YASP stats with a coach or ask 
them any questions you have on how to improve. Or just play a game together. Interacting with a skilled player is one of the 
best ways to improve at the game.

We love partnerships like these that help us further our mission: to make you a better Dota player.

***

And as always, we're always improving our infrastructure to improve site reliability and performance.

### Welcome, Cassandra!
After a lengthy migration, we've moved over 1.2 billion matches from PostgreSQL to a 4-node Cassandra cluster.
We're seeing *over 98% of requests served in under a second*! Yay! This is a huge improvement over the performance we were 
seeing with PostgreSQL. Now, load times scale linearly with the number of matches processed, so player pages with lots of 
matches (~5000+) might have slightly slower times, but this is still much better than the 15-30 second times from before!

Native support for compression has also cut our disk space usage in half! We were even able to switch to HDD storage for a 
4x reduction in storage costs. All this means future savings.

### Isolated Infrastructure
We moved Postgres, Redis, and each Cassandra node to their own separate compute instances to prevent them from contending for 
memory, which had previously been causing random crashes.
