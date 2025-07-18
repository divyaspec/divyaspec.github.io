---
layout: page
title: Java Cookbook 4th Edition
---
## Key takeaways

Java 11 and 12 added several new String methods, including indent (int n), stripLeading() and stripTrailing(), Stream<T> lines(), isBlank() and transform(). 

The author talks about Java String precedence rule. 

int result = ...;
System.out.println(result + '=' + " the answer.");

Given that result is an integer, then result + '=' is a valid numeric expression, which will result in a single value of type int. If the variable has a result 42, the character = in a Unicode has the value of 61, so the above two line code fragment would print:

103 the answer.

The wrong value and no equal sign! The safer approaches include using parentheses, double quotes around the equal sign, a StringBuilder.

```
StringBuilder sb2 = new StringBuilder ();
sb2 . append ( "Hello" ); sb2 . append ( ',' );
sb2 . append ( ' ' ); sb2 . append ( "World" );
```

Java 14 uses text blocks, as mutliline text strings. Example as follows:

```
String long = """
This is an example text for multiline strings."""
```
Immuatability of Strings is one of the fundamentals of the JVM. Immutability objects are good for software reliability. It is possible to tinker with the String's internal data structures using Reflection API. But Java module system from Java 9 has secured the API so you cannot mendle internals. String class are marked as final so it cannot be subclassed. 

### Putting Strings together with Stringbuilder
Problem:
If you need to put String pieces together.
Solution:
Use a StringBuilder. However there are cons in using StringBuilder. Firstly, its not thread safe. 
StringBuilder append(), delete(), replace() and reverse() method returns a reference to the builder object to facilitate fluent API style of coding.
