---
layout: page
title: Real World Software Development
---
### Single Responsibility Principle
- A class that has responsibility over a single functionality
- One reason for the class to change.
For example, in the book the author talks about how we can split a class can be broken down individually:

1. Reading input
2. Parsing the input in a given format
3. Processing the result.
4. Reporting the summary of the result.

### Principle of least surprise
When you implement methods ensure that it is obvious what is happening when looking at the code.
- Use self-documenting method names so it is immediately obvious what they do.
- Do not change the state of parameters as other parts of code may depend on it.


## Reference
[Books](/_posts/2018-10-10-Books.md)
