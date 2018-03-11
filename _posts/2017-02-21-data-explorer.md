---
layout:     post
title:      Introducing the Data Explorer!
date:       2017-02-20 00:00:00
summary:    A new tool to help you find interesting insights about Dota 2 matches
categories: 
---
Today we're proud to introduce a public preview of our newest feature, the [Data Explorer](https://www.opendota.com/explorer)!

Feature Overview
----
* The Data Explorer is a tool that helps users answer questions about players and performances in professional Dota 2 matches.  
* Users can easily construct queries by clicking on their desired fields and parameters.  
* Fields support auto-complete, so just entering `tim bat` into the `select` field will find `Timing - Battle Fury`.  
* Once you're done building your query, you can get your data in a table directly on the page (the `table` button) or open a new tab with the raw API response (the `JSON` button). 
* This flexibility ensures that you'll get the data you need regardless of whether you're you making a one-off query out of curiosity or trying to feed the result to another program for further analysis or visualization. 
* Users who are comfortable writing SQL can also tweak the generated query or write their own from scratch.  

Example Queries
----
* [Fastest Midas in 7.02](https://www.opendota.com/explorer?select=timing_hand_of_midas&maxPatch=7.02&minPatch=7.02)

* [Earliest courier kill in 7.02](https://www.opendota.com/explorer?select=kill_npc_dota_courier&maxPatch=7.02&minPatch=7.02)

* [Most kills at TI6](https://www.opendota.com/explorer?select=kills&patch=&league=4664)

* [Heroes with the highest average GPM of all time](https://www.opendota.com/explorer?select=gold_per_min&patch=&league=&group=hero)

* [Dendi's fastest Blink Dagger on Templar Assassin](https://www.opendota.com/explorer?select=timing_blink&patch=&league=&group=&player=70388657&hero=46)

Technical Details
----
* The database schema is available [here](https://github.com/odota/core/blob/master/sql/create_tables.sql).
* Only `SELECT` queries are allowed (obviously), so trying to `DROP TABLE matches` won't work. (Sorry, [script kitties](https://www.google.com/search?q=script+kitties&tbm=isch).)
* Queries time out after running for 30 seconds. Plan your queries accordingly, and use the `LIMIT` and `OFFSET` keywords to page your results as needed.

Conclusion
----
We hope you find this new feature both exciting and useful! Let us know on [GitHub](https://github.com/odota) or [Discord](https://discord.gg/0o5SQGbXuWCNDcaF) if you have any feedback regarding this feature or have any new feature requests, or submit a pull request yourself! Happy Dota :)
