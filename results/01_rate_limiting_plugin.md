## Objective

Confirm our Rate Limiting plugin using Redis Sentinel performs better than Kong out of the box Rate Limiting plugin using Cassandra or Redis (single node).

## Test Result Summary

Our Rate Limiting plugin using Redis Sentinel performed better in all key metrics when compared with Kong out of the box Rate Limiting plugin using Cassandra or Redis (single node).

## Success Criteria

| Key Metric              | Expected Result |
| ----------------------- | --------------- |
| Kong Latency            |                 |
| API Error Response Rate |                 |
| Data store disk usage   |                 |
| Data store CPU usage    |                 |

## Test Environment

| Kong               | Cassandra              | Redis (Single Node) | Redis Sentinel |
| ------------------ | ---------------------- | ------------------- | -------------- |
| v1.x.x.x           | vx.x.x                 |                     |                |
| # pods             | # nodes                |                     |                |
| # CPUs / pod       | # CPUs / node          |                     |                |
| # GB memory / pod  | # GB memory / node     |                     |                |

## Test Results

| Test Num | Max QPS  | Fault Tolerant | Data Store          | Error Response Rate | Kong Latency | Data Store CPU | Data Store Disk Usage | 
| -------- | -------- | ---------------| ------------------- | ------------------- | ------------ | -------------- | --------------------- |
| 1        |          |                | Cassandra           |                     |              |                |                       |
| 2        |          |                | Redis (Single Node) |                     |              |                |                       |
| 3        |          |                | Redis Sentinel      |                     |              |                |                       |

--- 
[Back](../README.md)

