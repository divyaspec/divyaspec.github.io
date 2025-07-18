---
layout: page
title: What is Java Object Serilization
---

Supports the transformation of a graph of java objects into a stream of bytes for storage or transmission.

Serialisation - Objects gets transformed into byte stream.
Deserialisation - Bytes can be transformed into a graph of java objects.


### Serializable Classes
- Save and restored fields of each object.
- Allow classes to evolve by adding field or superclasses.

A serializable class can be 
- Declare which of its fields are saved or restored.
- Write and read optional values and objects.

By default, non-transient and non-static fields are serialized. Transient fields are fields those have meant to be non-persistent.

### Object Output Serialization

- Implements object serialization
- Maintains the state of the stream including the objects already serialized.
- Write object method used to serialize an object to the stream.

Note: Only data is stored in a serialization byte stream. - Code is not serialization

JVM in order to de-serialization of an object needs to identify the objects into the class definition it has access to.


### The write object method
- The specified object
- Traverses references to other objects in the object graph recursively to create a complete serialized representation of the graph.

Primitive types (int, float, bytes, arrays) can also be serialized.
