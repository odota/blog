---
layout:     post
title:      Why we don't distribute parse work to users
summary:    Answer to a commonly asked question.
---

Every few months, someone will suggest that we should have users parse replays, similar to how distributed computing projects like folding@home work.  There are a few reasons that we haven't attempted to do this:

* **Development Overhead** We would need to create a desktop client for users to download, install, and run on their own machines, which could be on many different platforms. This would mean additional code to maintain and more testing to be done.

* **Parser Updates** When the parser gets updated (e.g. to extract some new data, or replay format changes), we would need all users to upgrade their parsing software quickly in order to submit consistent data. As anyone who has ever tried pushing software updates knows, this is often a vexing process.

* **Data Integrity** If we allow users to submit parsed data, we would need some way to ensure that users don't submit incorrect (or even malicious) data. One possible solution could be to force all matches to be parsed by two distinct workers and the results to agree, but that doubles the workload and doesn't even guarantee correctness (if someone were running a large farm of malicious workers, for example).

* **Low Cost Impact** Parsing isn't a major component of our overall costs. At the time of this post, parsing only costs around $200 a month, which is only 1/7<sup>th</sup> of the cost of all of our servers.
