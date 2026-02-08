---
title: "Redundancy vs Replication: Spot the Difference"
date: 2026-02-08
draft: false
tags: ["System Design", "Redundancy", "Replication", "Fault Tolerance"]
description: "Is having a backup server 'Redundancy' or 'Replication'? We clarify the difference—Redundancy is about survival, Replication is about data consistency."
authors: ["ckdash"]
categories: ["System Design"]
---

These two terms are often used interchangeably, but in System Design, they mean very different things.

*   **Redundancy**: "I have a spare tire."
*   **Replication**: "I have a spare tire, and it has the exact same air pressure and tread wear as the main tire."

## 1. Redundancy (The Survival Strategy)

**Redundancy** is simply the duplication of components to increase reliability. Ideally, it's about **Availability**.
It does **not** imply that the components share state or data.

*   **Example**: You have two web servers running the same code. If Server A dies, Server B takes over. Since the code is static, you don't need to "sync" anything in real-time.

### Types of Redundancy
*   **Active Redundancy**: All nodes are active and sharing the load (e.g., behind a Load Balancer).
*   **Passive Redundancy**: One node is active, the others are on standby (Cold Standby).

```mermaid
%%{init: {'theme': 'dark'}}%%
graph TD
    subgraph Active_Redundancy [Active Redundancy]
        LB[Load Balancer] --> S1[Server A]
        LB --> S2[Server B]
        S1 -.->|Both Active| S2
    end
    
    subgraph Passive_Redundancy [Passive Redundancy]
        LB2[Load Balancer] --> M1[Primary]
        M1 -.->|Failover| M2[Standby]
        style M2 stroke-dasharray: 5 5
    end
```

## 2. Replication (The Data Strategy)

**Replication** is Redundancy **+ Synchronization**.
It is used for **Data** (Databases, Caches) where state changes over time. You can't just have a specific "backup" DB; that backup must have the *latest* data.

*   **Example**: You have a Primary Database and a Replica. When you write `User.name = "Alice"` to the Primary, that change must be **Replicated** to the Replica.

### Types of Replication
*   **Active Replication (Multi-Master)**: You can write to any node, and they sync with each other. Complex conflict resolution needed.
*   **Passive Replication (Master-Slave)**: You write only to the Master. The Master syncs to Slaves. Slaves are Read-Only (usually).

```mermaid
%%{init: {'theme': 'dark'}}%%
graph TD
    Client -->|Write| Master[(Master DB)]
    Master -->|Sync Data| Slave1[(Replica 1)]
    Master -->|Sync Data| Slave2[(Replica 2)]
    Client -->|Read| Slave1
    Client -->|Read| Slave2
```

## Comparison Cheat Sheet

| Feature | Redundancy | Replication |
| :--- | :--- | :--- |
| **Goal** | **Availability** (Survive failure) | **Consistency** (Keep data in sync) |
| **Sync Needed?** | No (Usually stateless) | **Yes** (Critical) |
| **Use Case** | Web Servers, Power Supplies, Network Cables | Databases, Caches, File Storage |
| **Complexity** | Low | High (Handling lag, conflicts) |

## Conclusion

*   Use **Redundancy** to keep your application running (Stateless).
*   Use **Replication** to keep your data safe and consistent (Stateful).
