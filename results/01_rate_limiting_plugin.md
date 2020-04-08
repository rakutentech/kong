## Objective

Confirm our Rate Limiting plugin using Redis Sentinel performs better than Kong out of the box Rate Limiting plugin using Cassandra or Redis (single node).

## Test Result Summary

Our Rate Limiting plugin using Redis Sentinel performed better in all key metrics when compared with Kong out of the box Rate Limiting plugin using Cassandra or Redis (single node).

## Success Criteria

| Key Metric              | Expected Result |
| ----------------------- | --------------- |
| Kong Latency            |     <260 ms     |
| API Error Response Rate |     < 1%        |
| Data store CPU usage    |     < 80%       |

## Test Environment

| Kong               | Cassandra              | Redis (Single Node) | Redis Sentinel |
| ------------------ | ---------------------- | ------------------- | -------------- |
| v1.2.2             | v3.0.14                |  v3.2.5             |  v3.2.5        |
| 16 pods            | 3 nodes                |  1 node             |  3 nodes       |
| 1 CPU / pod        | 8 CPUs / node          |  4 CPUs / node      |  4 CPUs / node |
| 2 GB memory / pod  | 40 GB memory / node    |  16 GB memory / node|  16 GB memory / node|


## Test Results

| ﻿Test Num | Max QPS (per sec) | Fault Tolerant | Data Store          | Error Response Rate (QPS) | Kong Latency (200ms) | Kong Latency (1000ms) | Data Store CPU |
|----------|---------|----------------|---------------------|---------------------------|---------------------|----------------------|----------------|
| 1        | 1551    | TRUE           | Cassandra           | 0                         | 251                 | 1051                 | 18%            |
| 2        | 2400    | TRUE           | Cassandra           | 0                         | 320                 | 3500                 | 60%            |
| 3        | 1551    | FALSE          | Cassandra           | 0.018                     | 238                 | 1038                 | 18%            |
| 4        | 2480    | FALSE          | Cassandra           | 0.361                     | 341                 | 1228                 | 25%            |
| 5        | 1555    | TRUE           | Redis Sentinel      | 0                         | 260                 | 1065                 | 18%            |
| 6        | 3108    | TRUE           | Redis Sentinel      | 0                         | 253                 | 1057                 | 25%            |
| 7        | 1549    | FALSE          | Redis Sentinel      | 0.051                     | 330                 | 1140                 | 18%            |
| 8        | 3110    | FALSE          | Redis Sentinel      | 0.027                     | 255                 | 1059                 | 25%            |
| 9        | 1339    | TRUE           | Redis (Single Node) | 1.086                     | 255                 | 1051                 | 3%             |
| 10       | 2395    | TRUE           | Redis (Single Node) | 1.224                     | 350                 | 1141                 | 5%             |
| 11       | 1365    | FALSE          | Redis (Single Node) | 1.095                     | 245                 | 1043                 | 3%             |
| 12       | 2450    | FALSE          | Redis (Single Node) | 1.236                     | 270                 | 1060                 | 5%             |
--- 
[Back](../README.md)

