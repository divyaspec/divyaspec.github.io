---
layout: page
title: SmallRye Mutiny & vert.x with Kafka
---

## Creating Async HTTP Endpoints

You want to create an Async HTTP Endpoint using mutiny, below lines of code shows how to create an async http endpoint.

```

GET
@PATH("/reactive")
@Produces(MediaType.TEXT_PLAIN)
public Multi<String> helloMutiny() {
    return Multi.createFrom().items("h", "e", "l", "l", "o");
}
```

With Mutiny, a Multi is a Publisher.

## Create a simple maven project

mvn archetype:generate
-DgroupId=com.kafka.smallrye.sample
-DartifactId=java-project
-DarchetypeArtifactId=maven-archetype-quickstart
-DinteractiveMode=false

## Reactive Programming in Java

Reactive programming is a development model oriented around data flows and the propagation of data. In reactive programming, the stimuli are the data transiting in the flow, which are called streams. There are many ways to implement a reactive programming model.

```
observable.subscribe(
  data -> { // onNext
    System.out.println(data);
  },
  error -> { // onError
    error.printStackTrace();
  },
  () -> { // onComplete
    System.out.println("No more data");
  }
);
```

In this snippet, the code is observing (subscribe) an Observable and is notified when values transit in the flow. The subscriber can receive three types of events. onNext is called when there is a new value, while onError is called when an error is emitted in the stream or a stage throws an Exception. The onComplete callback is invoked when the end of the stream is reached, which would not occur for unbounded streams.

## Reactive Systems

/** Reactive streams is an initiative to provide a standard for asynchronous stream processing with back-pressure. It provides a minimal set of interfaces and protocols that describe the operations and entities to achieve the asynchronous streams of data with nonblocking back-pressure. It does not define operators manipulating the streams, and is mainly used as an interoperability layer. This initiative is supported by Netflix, Lightbend, and Red Hat, among others. **/

While reactive programming is a development model, reactive systems is an architectural style used to build distributed systems (http://www.reactivemanifesto.org/). It’s a set of principles used to achieve responsiveness and build systems that respond to requests in a timely fashion even with failures or under load.

To build such a system, reactive systems embrace a message-driven approach. All the components interact using messages sent and received asynchronously. To decouple senders and receivers, components send messages to virtual addresses. They also register to the virtual addresses to receive messages.

An address is a destination identifier such as an opaque string or a URL. Several receivers can be registered on the same address—the delivery semantic depends on the underlying technology. Senders do not block and wait for a response. The sender may receive a response later, but in the meantime, he can receive and send other messages. This asynchronous aspect is particularly important and impacts how your application is developed.

Using asynchronous message-passing interactions provides reactive systems with two critical properties:

- Elasticity — The ability to scale horizontally (scale out/in)

- Resilience — The ability to handle failure and recover

## Reactive Microservices
When building a microservice (and thus distributed) system, each service can change, evolve, fail, exhibit slowness, or be withdrawn at any time. Such issues must not impact the behavior of the whole system. Your system must embrace changes and be able to handle failures. You may run in a degraded mode, but your system should still be able to handle the requests.

To ensure such behavior, reactive microservice systems are comprised of reactive microservices. These microservices have four characteristics:

- Autonomy
- Asynchronizity
- Resilience
- Elasticity

## What About Vert.x ?
Vert.x is a toolkit for building reactive and distributed systems using an asynchronous nonblocking development model. Because it’s a toolkit and not a framework, you use Vert.x as any other library. It does not constrain how you build or structure your system; you use it as you want. Vert.x is very flexible; you can use it as a standalone application or embedded in a larger one.

From a developer standpoint, Vert.x a set of JAR files. Each Vert.x module is a JAR file that you add to your $CLASSPATH. From HTTP servers and clients, to messaging, to lower-level protocols such as TCP or UDP, Vert.x provides a large set of modules to build your application the way you want. You can pick any of these modules in addition to Vert.x Core (the main Vert.x component) to build your system. Figure 2-2 shows an excerpt view of the Vert.x ecosystem.

![image](/assets/images/ReactiveProgramming.png)

## Asynchronous Development Model
Java offers two types of Asynchronous development methods:
- Callbacks : Asynchronous methods do not have a return value but instead takes an extra parameter (a lamda or an anonymous class) that gets called when the result is available. A well known example is good old Java old tech Swing Listener which is used to be the front end JS style but in java. The users interact with the screens but the result gets computed asynchronously without blocking the resource.
- Futures : This new Future<T> java version has been introduced in Java 8 and quite popular asynchronous method that immediately returns a T value. Future object wraps the computed value T. For instance, Java has a Executor service running Callable<T> tasks use Future objects.

### Links
- You can read more about Mutiny at [SmallRye Reactive](https://smallrye.io/smallrye-reactive-streams-operators/).
- [Vert.x Kafka Client](https://vertx.io/docs/vertx-kafka-client/java/).
- [OpenShift CodeReady Containers](https://cloud.redhat.com/openshift/install/crc/installer-provisioned)