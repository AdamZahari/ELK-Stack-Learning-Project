# Elasticsearch Cluster Setup

This document describes how the 3-node Elasticsearch cluster was created for the Learning Project.

---

## Initial Node Setup (Node 1)

Operating System: Ubuntu Server  
Role: First cluster node (bootstrap node)

### Step 1 – Install Elasticsearch & Kibana

Elasticsearch and Kibana were installed on the first Ubuntu server.

After installation, Elasticsearch was started.  
Since this was the first node, it automatically:

- Generated the cluster UUID
- Generated the elastic user password
- Generated an enrollment token
- Enabled security by default

---

## Generate Enrollment Token

To allow other nodes to join the cluster, an enrollment token was generated on Node 1:

```bash
sudo /usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s node

---

## Adding Node 2 (Ubuntu Server)
