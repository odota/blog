---
layout: post
title:  Introducing the Meta Explorer!
date: 2017-12-13
summary: A new feature to investigate what's going on in the world of public matches
---

The [Meta Explorer](https://www.opendota.com/meta) is a tool to allow users to query a sampled set of public matches.
This is the public match counterpart to the original [Explorer](https://www.opendota.com/explorer), which allows advanced queries on professional matches.
Roughly 10% of the public matches played where 2 or more players have a rank (to determine skill level) are sampled.
We hope this tool allows users to find some interesting patterns or trends in the current state of the game!

Currently, this works on the last 24 hours of matches (this may be configurable in the future if there is demand).

Here are some examples of questions you can answer:
* [Which heroes are picked the most in Divine matches?](https://www.opendota.com/meta?minRankTier=7)
* [Is Lycan stronger on Radiant or Dire?](https://www.opendota.com/meta?minRankTier=&result=&side=&group=side&hero=77)
* [Which heroes are most common in matches lasting longer than 90 minutes?](https://www.opendota.com/meta?minRankTier=&result=&side=&group=hero&hero=&minDuration=90&gameMode=)
* [What's the win rate of Anti-Mage in games lasting 40 minutes?](https://www.opendota.com/meta?minRankTier=&result=&side=&group=duration&hero=1&minDuration=&gameMode=&lobbyType=)

Have fun digging into the data!
