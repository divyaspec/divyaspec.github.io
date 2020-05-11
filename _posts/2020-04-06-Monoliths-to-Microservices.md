---
layout: page
title: Monoliths to Microservices
---

## What are Microservices?

- Microservices are independently deployable services modeled around a business domain.
- The architecture choices offer many options for solving the problems you may face.
    - Technology agnostic
    - Independent deployability is key.
    - It's also type of SOA, opinionated about how services boundaries should be drawn.
- Microservices is a form of distributed system where you can expose and encapsulate the business capabilities via one or more network endpoints.
- Each microservice can communincate with each other via exposed network endpoint.
- It encapsulates data storage, data retrieval via well defined interfaces. So, the database are hidden inside the service boundary.

The main idea in the book is around making cross-service changes as infrequently as possible.
This ensures you don't need to make changes to two servies to roll out a feature, and orchestrate the deployment of these two changes. It takes less work in making changes inside single service (monolith) than rolling out changes in two services.

### key points to note:

*_High cohesion of Business Functionality rather than technology_*
*_Dont share database unless you really have to. It breaks the independent deployablity_*
*_Where appropriate encapsulate UI, application logic and data storage as we want our service as end-to-end slices of business functionality_*

### Advantage of Microservice

* Independent deployability means scale and robustness of the system can be greatly improved.
* Process isolation makes it possible to mix and match the technology choices we make (eg., programming styles, languages, databases or deployment platforms).

### What Problems they create?
* As with single process monoliths, transactions are relatively simple however with the services that spans mutiple computers, sometimes the network can go offline and service will fail or start to behave oddly. You will need to work out consistent view of data across multiple machines.
* Monoliths are also distributed systems (communication over the networks).The difference is the extent to which monolithic systems are distributed compared to microservice architectures. As you have more computers in the mix, communicating over more networks, you’re more likely to hit the nasty problems associated with distributed systems. 

## Reference
- [Monolithic to Microservices](https://www.amazon.co.uk/Monolith-Microservices-Evolutionary-Patterns-Transform/dp/1492047848/ref=sr_1_fkmr1_1?dchild=1&keywords=monolithic+to+microservices&qid=1589198193&s=kids&sr=8-1-fkmr1)