---
layout: page
title: Twelve Factor App
---

## What is Twelev-factor app?

The Twelve app evolved from the experiences of engineers at Heroku. It is a list of patterns that are used in cloud-native application architetures.

It is important to note that every single microservice is an app (that is independently deployable).

### Maintain One Codebase

Antipatterns are opposite of design patterns. Maintaining one codebase for each app that can be deployed. 

### Explicit Declaration of dependencies
"All dependencies must be explicitly declared and isolated, making it easy to configure and change dependencies. " - (Mastering Spring 5)

For java application where a maven pom/xml file is used for maintaining all your dependencies.

### Application configuration stored in an environment

Irrespective of the mechanism that's used, we recommend that you do the following:
- Manage configuration outside the application code (independent of the application's deployable unit)
- Use a standardized way of configuration

Having a centralised repository for application configuration should be considered.

### All dependencies are treated as backing services

"A backing service is any service that an application accesses over the network—an external application, an external database, or an email server." - (Mastering Spring 5)

### Clear separation between build, release, and run phases

Build: Creates an executable bundle (EAR, WAR, or JAR) from code, as well as dependencies that can be deployed to multiple environments
Release: Combines the executable bundle with a specific environment configuration to deploy in an environment
Run: Runs the app in an execution environment using a specific release

### Applications do not store states – stateless

Application do not store any data within the session. All data will be saved to a datastore.
Antipatterns is a sticky session.

### All the services are exposed with port binding

A Twelve-Factor App exposes all the services using port binding. While it is possible to have other mechanisms to expose services, these mechanisms are implementation-dependent. Port binding gives full control of receiving and handling messages, irrespective of where an app is deployed.

### Possibility to scale horizontally – concurrency

Scaling vertically has it limits. Scaling horizontally has its opportunities without limits.


### Each application instance is disposable

A Twelve-Factor App should do the following:

Have a minimum startup time. A long startup time means a long delay before an application can take requests.
Shut down gracefully.
Handle hardware failures gracefully.

### Acheiving environmental parity  - all environments are the same

All the environments, that is, development, test, staging, and production, should be similar. They should use the same processes and tools.

### Treating all logs as event streams

Visibility is critical to a Twelve-Factor App. Since applications are deployed on the Cloud and are automatically scaled, it is important that you have a centralized view of what's happening across different instances of the applications.

### No distinction for admin processes

Twelve-Factor Apps treat administrative tasks (migrations, scripts, and so on) in a similar way to normal application processes.



## Reference
- [Mastering Spring 5](https://www.amazon.co.uk/Mastering-Spring-effective-enterprise-applications/dp/1789615690/ref=sr_1_3?dchild=1&keywords=Spring+5&qid=1590822874&s=books&sr=1-3)