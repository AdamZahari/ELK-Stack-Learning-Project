# Architecture Overview

## Why 3 Nodes?

A 3-node cluster was chosen to simulate a production-style distributed system.

With 3 nodes:
- The cluster can tolerate 1 node failure
- Majority voting (quorum) prevents split-brain
- Replica shards can be distributed safely

Minimum nodes for high availability in Elasticsearch: 3

---

## Fault Tolerance

If 1 node fails:
- Cluster remains operational
- Replica shards are promoted to primary
- No data loss (if replicas are configured)

If 2 nodes fail:
- Cluster becomes unavailable (no majority)

---

## Current Node Role Design

Currently:
- All nodes use default roles
- Each node can act as master
- Each node stores data
- Each node can perform ingest

Future improvements may include:
- Dedicated master nodes
- Dedicated data nodes
- Coordinating-only nodes
