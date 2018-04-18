---
layout: post
title:  Important Changes to the OpenDota API
date: 2018-04-17
summary: Introducing the Free and Premium Tiers
---
**IMPORTANT: Users making more than 50,000 API calls per month will need to sign up for an API key in order to go beyond this limit.**

A year and a half ago, we launched the OpenDota API so that public developers could access advanced stats for millions of
matches for their own projects.

While this has been great for the developer and Dota 2 communities, making the OpenDota API publicly available has
significantly impacted our costs; only around 20% of our API requests come from the site itself ([opendota.com](https://www.opendota.com)).
As the costs of running the service have increased, we’ve looked for new revenue streams to cover these expenses while
improving availability and disaster resilience (e.g. performing routine backups of our databases).

As we’re committed to both providing the service free to our users and avoiding ad networks which monetize through your
data and browsing habits, we’ve decided to begin offering increased rate and call limits for registered high-volume users
on a premium plan. This will have no effect on the average end user of the site and app while ensuring heavy API users help
offset our costs.

We’re committed to continuing to support hobbyists and community developers with a Free Tier of 50,000 API calls per month.
Based on our survey of our API users, we feel the Free Tier limits will appropriately satisfy most hobbyist use cases.

**IMPORTANT: Users making more than 50,000 API calls per month will need to sign up for an API key in order to go beyond this limit.**

For those needing more API calls, we’re providing a new Premium Tier with higher rate limits and priority support. 
Usage of the Premium Tier will require a payment method and API key. Usage of the free tier will remain unchanged, no API key required.

**See the new [API page](https://www.opendota.com/api) where you can also signup and receive your API key so that you can migrate to this change ahead of time.
The new tiers and billing will be enabled starting 4/22 @ 1 PM PDT (UTC+7).**

![New tiers pricing information.]({{ "/assets/api_pricing_table.PNG" | absolute_url }})