# 8 Most-Used Distributed System Design Patterns

> If you are building a distributed system, you’ll need to use some of these patterns.

## 1 - Ambassador Pattern
Focuses  on offloading all major tasks other than business logic to helper  services. Example of such tasks include logging, monitoring, and  retries.

## 2 - Circuit Breaker Pattern
This pattern helps prevent cascading failures when one service calls another service by preventing such calls.

## 3 - CQRS Pattern
Separate read and write operations for better flexibility and supporting different scaling requirements.

## 4 - Sharding
Split a monolithic database into multiple partitions known as shards for better horizontal scalability.

## 5 - Sidecar Pattern
Deploy  auxiliary components alongside the main service containers to manage  cross-cutting concerns like configuration management, logging, and  monitoring.

## 6 - Pub/Sub 
Used for asynchronous communication between publisher services and subscriber services.

## 7 - Leader Election 
In  distributed systems, some tasks (such as leader-follower replication)  need a single leader. Leader election algorithms ensure that only one  node is designated as the leader.

## 8 - Event Sourcing
Store the  events or state changes in a separate event store. The event store can  add the event to a message broker to update the read database.

