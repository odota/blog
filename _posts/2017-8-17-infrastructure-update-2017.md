---
layout:     post
title:      Infrastructure Update, 2017
summary:    An update on the current costs of the project

As a follow-up to the post from last year detailing the infrastructure costs, here's an up-to-date snapshot. 
We are still using Google Cloud Platform, although we generally prefer running open-source software on VMs rather than relying on hosted services, which are more expensive.

 * 4 Cassandra nodes, 2TB HDD each (hm-4) ~ $512 + $320 = $832
 * 1 Postgres node, 250GB SSD (hm-4) ~ $128 + $43 = $171
 * 1 Redis node, 50GB SSD (n1-standard-2) ~ $48 + $9 = $57
 * 5 web nodes (g1-small, autoscaling up to 20 nodes) ~ $50
 * 30 parse nodes (preemptible highcpu-2, autoscaling from 3 to 150 nodes) ~ $330
 * 1 backend node (preemptible n1-standard-2) ~ $14
 * 40 retriever nodes ~ $150
 * 5 proxy nodes ~ $15
 * 3 load balancers ~ $60
 * Boot disks (10 GB per instance) ~ $100
 * Bandwidth out ~ $130

Total: $1909
