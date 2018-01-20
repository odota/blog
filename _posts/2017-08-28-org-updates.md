---
layout:     post
title:      Three Years of OpenDota, 2017 Financial Report, and Organizational Changes
summary:    A review of the past year, and updates going forward
---

Three Years of OpenDota
====

OpenDota is now three years old! Here's a summary of the features that were released in the last year:
* [Data Explorer](https://www.opendota.com/explorer), a feature for allowing advanced queries on pro match data
* [Meta Explorer](https://www.opendota.com/meta), a feature allowing advanced queries on sampled public matches
* [Mobile application beta](https://blog.opendota.com/2017/11/17/mobile-beta/), with a full release sometime later this year
* [Hero pages](https://www.opendota.com/heroes) with additional data on heroes
* [Team pages](https:///www.opendota.com/teams) with a real-time ranking of teams and a page for each team with detailed data
* A [data dump](https://blog.opendota.com/2017/03/24/datadump2/) of over a billion matches for researchers and analysts to work with
* [Feed API](https://github.com/odota/core/blob/master/docs/feed.md), an alternative WebSocket-powered way of getting matches from the OpenDota platform
* Match stories, automatically generated verbal summaries of Dota matches
* "Played with", the ability to immediately see your record when playing with other players by viewing their profile
* New graphing library (Recharts) for prettier looking charts, and updates to React 16 and styled-components for increased performance/maintainability
* Along with hundreds of other visual improvements and bug fixes, a summary of which can be found [here].(https://github.com/odota/web/pulls?q=is%3Apr+is%3Aclosed+label%3Arelease)

All of these features were built by volunteer contributors, and it's incredibly exciting to see what the community comes up with next!

2017 Financial Report
====

In 2017, revenues and expenditures were as follows:
```
Sponsors	$40,354.08
Donations	$2,620.00
Ads	$1,093.12
Fees	-$2,332.81
Servers	-$22,530.55
```
Net operating margin for 2017:	**$19,203.84**

Notes on these figures:
* Ads include revenue from advertisements supplied by networks. There were removed in February 2017.
* Fees include federal/state income taxes, as well as the 2.9% + $0.30 on each transaction charged by our payment processors (PayPal and Stripe)
* Donations include remaining revenue from individual donors (after processing fees) via [https://carry.opendota.com](https://carry.opendota.com)
* Servers include infrastructure costs, plus administrative costs such as website registration and developer fees.

Including the existing surplus from years past, the current project balance is **$24,301.93**.

Organizational Changes
====
Since its inception, the OpenDota Project has operated as a personal project for tax purposes (sole proprietorship). However, the project has grown over the years (now exceeding $30,000 in annual revenue), and we feel that it is finally time to make some organizational changes. The details are as follows:

* Albert and Howard, the project founders, will create a LLC which will administer opendota.com and pay taxes on its revenues as a legal entity.
  * With the recent tax changes passed by the US government, incorporation will result in a lower tax rate than our personal marginal tax rates, which reduces our tax burden.
* We don't anticipate any changes to the end-user experience. We are committed to maintaining feature parity for all users, so everyone can have access to the same functionality.
* The costs of hosting the public opendota.com API (api.opendota.com) will be funded by sponsors, who get product placement on the public hosted OpenDota UI (www.opendota.com).
* We are planning to remove the donation link (carry.opendota.com) from the public UI.
  * For the past 18 months, sponsors have more than covered the operating costs of the service. We retained a token $100 per month goal for the site footer (roughly 5% of operating costs), just to show some progress for those interested in donating. We've found that setting the value too high causes people to make panicked Reddit threads, so we've been careful about keeping the value low. 
  * Removing the donation link/meter should resolve this issue completely.
  * Most months, we receive between $150 and $200 in donations.
  * Our goal has always been to build a service that's sustainable in the long-term, and sponsors have proven to be an effective way of achieving that goal.
  * If circumstances change in the future, we may re-enable individual contributions, possibly through Patreon or a similar platform.
* Existing cheese counts and profile icons will be preserved on individual profile pages.
* The project codebase will remain fully open source and maintained by volunteer developers in the community.
  * Any features/fixes from Albert/Howard will continue to be contributed to the open-source repository.
  * Additionally, we are relicensing odota/core from GPLv3 to the MIT License, which is more permissive. We want to ensure that the code is easily usable by anyone without any legal encumbrances.
* If you are interested in becoming a sponsor, please contact sponsor@opendota.com

We believe these changes make the most sense given how The OpenDota Project has come to operate in the past few years and how we envision it continuing to operate in the future. If you have any questions, comments, concerns, or suggestions, please feel free to reach out to any of us and we would be more than happy to discuss our motivations for these changes.

Happy Dota, everyone!
