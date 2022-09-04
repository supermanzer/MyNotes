This chapter will introduce the `Service Layer` and further abstract the interface with our domain & repository patterns.  We wll also start to wire up our Flask API.

## Starting Architecture:
```mermaid
flowchart TD;
A[Tests]
subgraph Repository
    direction LR
    B[SQLAlchemy Repository] --> C[Abstract Respository]
end
B --> D[(DB)]
subgraph Domain
    E[/allocate/] --> F[Batch] --> G((Order LIne))
end
A --> Repository
A --> Domain
C --> Domain
```
---
## Eventual Architecture
We are going to build out our system to match the following architecture:
```mermaid
flowchart TD;
ZA[Flask] --invoke--> ServiceLayer
ZB[Tests] --invoke--> ServiceLayer
subgraph ServiceLayer
    G[/service.allocate /]
    H[/service.add_batch/]
end
subgraph Domain
    direction LR
    D[/allocate /]
    E[ Batch ]
    F((Order Line))
    D --> E --> F
end
subgraph Repositories
    direction LR
    A[Fake Repository]
    B[SQLAlchemy Repository]
    C[Abstract Repository]
    A --> C
    B --> C
end
ZC[(DB)]
B --> ZC
Repositories --retrieves--> Domain
ServiceLayer --models.allocate-->Domain
ServiceLayer --list/add batches-->Repositories
ZA --instantiates-->B
ZB --instantiatesP-->A
```

We will also be exploring the differences between ochestration logic, business logic and interface code.  The `Service Layer` we introduce in the above architecture will handle the orchestration of workflows.  It also serves to define the use case(s) for our system.

Impmlementing a service layer with our repository pattern also allows us to write tests faster and more complete.