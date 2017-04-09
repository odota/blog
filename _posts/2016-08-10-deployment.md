---
layout:     post
title:      Deployment and Infrastructure
summary:    An overview of the deployment process and infrastructure that powers the service.
---

YASP is hosted mostly on Google Compute Engine (GCE). 

This choice was made for two main reasons:

 * GCE offers flexible capacity resizing of both computational power and storage
 * GCE offers extremely cheap preemptible instances which are an excellent value for interruptible CPU-bound workloads, such as replay parsing.

Infrastructure
----

The current infrastructure consists of the following, with approximate monthly cost:

 * 4 Cassandra nodes, 2TB HDD each (hm-4) ~ $512 + $320 = $832
 * 1 Postgres node, 200GB SSD (hm-2) ~ $64 + $34 = $108
 * 1 Redis node, 50GB SSD (hm-4) ~ $128 + $9 = $137
 * 3 web nodes (preemptible g1-small, autoscaling up to 10 nodes) ~ $15
 * 15 parse nodes (preemptible highcpu-2, autoscaling from 3 to 30 nodes) ~ $162
 * 1 backend node (preemptible highcpu-4) ~ $22
 * 6 retriever nodes ~ $42
 * 4 proxy nodes ~ $16

Each node also has a 10GB SSD disk attached as a boot disk, which adds around $50.  Egress traffic also costs about $0.12 per GB, which adds another $50.

Preemptible:

 * We save money by running all our application code on preemptible instances.  
 * They have a maximum lifetime of 24 hours, but since they live in instance groups, GCE automatically spins up new nodes to replace the ones that expire.  
 * There are 3 web nodes, so a single node restarting does not interrupt service.  
 * Parse and backend nodes can be down for a few minutes without major service impact.

Autoscaling:

 * Instance groups also allow autoscaling based on CPU usage.
 * During off-peak hours, we might have only 5-8 instances running, whereas during peak hours, we might have around 15-20.
 * This elastic resizing saves money since we do not pay for infrastructure we are not actively using (instances are billed per minute).

Deployment
----

Data:

 * The database software is rarely updated.
 * All three (Cassandra, Postgres, Redis) run using Docker images which can be versioned by changing the version number and re-creating   the container.
 * The data is saved to persistent disks mounted into the instance so it survives the container re-creation.

Code:

 * The current state of the `master` branch is built by Travis CI.
 * When the build completes and all the tests pass, the built image is pushed to Docker Hub.
 * We use the deploy script `scripts/deploy.sh` to re-deploy one of the instance groups.
 * Each instance is shut down and restarted. On startup, they all pull the latest (freshly built) image.

Configuration:

 * We use a feature of GCE called "Metadata" in order to manage configuration.
 * GCE allows arbitrary strings to be saved and accessed from any instance within the project. 
 * Part of the startup script pulls this metadata down into a `.env` file, which defines the configuration.
 * To do a configuration deployment, we simply update the metadata and use the deploy script to restart the affected instances.

Schema updates:

 * To apply schema updates, ssh into a database node.  GCE has a one-click button to do this from their web portal.
 * Once in the node, running `sudo docker ps` lists the running containers.
 * Enter a shell within the container: `sudo docker exec -it $CONTAINER_NAME bash`
 * Open a query shell for the database:
   * Cassandra: `cqlsh -k yasp`
   * Postgres: `psql -U postgres yasp`
 * Run any schema updates/index builds

Administration:

 * GCE command line tool `gcloud`: https://cloud.google.com/sdk/downloads
 * Cassandra admin tool `nodetool`
   * `nodetool status` for cluster information
 * Cassandra query shell `cqlsh -k yasp`
 * Postgres shell `psql -U postgres yasp`
 * Redis shell `redis-cli`
 * List Docker containers: `sudo docker ps`
 * Enter a Docker container: `sudo docker exec -it $CONTAINER_NAME bash`
 * Backend node runs multiple processes at once via `pm2`
   * `pm2 list` shows running processes
   * `pm2 logs` shows logs
   * `pm2 reload` reloads a process
 * Otherwise, use Docker logs directly: `sudo docker logs -f --tail 100 $CONTAINER_NAME`
