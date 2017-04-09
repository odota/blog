---
layout:     post
title:      Explaining Rankings
summary:    An explanation of how rankings work
---

This post will hopefully explain the methodology behind hero rankings in a more layman-friendly manner.  While the [code](https://github.com/odota/core) is publicly available, it may not be understandable by many users.

Factors considered:  
----

 * Number of wins  
 * Average MMR in matches played  

Factors NOT considered:  
----

 * KDA, GPM, etc.  
 
The choice of factors discourages players from stat-padding in order to increase their rankings.

Methodology:  
----

 * When a player wins a match, they score points equal to (average visible MMR in match / 1000) ^ 7 for the hero they played.  
 * The exponential factor means higher MMRs are able to score points more rapidly than lower ones.  A match won at 6000 MMR scores 128 times as many points as one won at 3000 MMR.  
 * This factor has been adjusted several times to weight MMR more heavily and will be 7 starting 2016-10-01.  
 * Each hero has its own individual ranking list.
 * The score used for the ranking is the sum of the points in the current ranking period.

Data storage: 
----

 * Hero rankings utilize Redis zsets (sorted sets) for fast update/lookup of any player's rank.  
 * The methodology currently in use has the benefit of being efficiently updated.  We simply need to [ZINCRBY](https://redis.io/commands/zincrby) the player's score in the corresponding zset whenever they win a game.  

Reset (seasons):  
----

 *  Rankings reset every 3 months (January, April, July, and October 1st), which clears all lists.  This is for a couple of reasons:  
   * Rankings should reflect recent data.  If a player has played thousands of games previously on a hero but hasn't in a while, they should not occupy a permanent slot on the rankings.  
   * It's easier to tweak and adjust the ranking formula when the rankings reset periodically (we can apply the new formula shortly prior to the reset and avoid having to back-calculate rankings for all previous matches).  

If you have any suggestions or ideas, please open an issue on GitHub, or start a discussion on our Discord channel!  
