---
layout: page
title: Real World Software Development
---

## Key notes and concepts from the book *Real World Software Development*.
 *Thanks to the author for describing in detail with solid example.*

### Single Responsibility Principle

* A class that has responsibility over a single functionality
* One reason for the class to change.

For example, in the book the author talks about how we can split a class can be broken down individually:

1. Reading input
2. Parsing the input in a given format
3. Processing the result.
4. Reporting the summary of the result.

### Principle of least surprise

When you implement methods ensure that it is obvious what is happening when looking at the code.

* Use self-documenting method names so it is immediately obvious what they do.
* Do not change the state of parameters as other parts of code may depend on it.

### Cohesion

Cohesion is concerned with how related things are. To be more precise, cohesion measures how strongly related responsibilities of a class or method are.
 What do you want is to achieve high cohesion, which means that the code is easier for others to locate, understand and make change.

### Six common ways to group methods in a class:

* Functional (high cohesion)

Grouping methods for solving a defined task: parse lines in the CSV format. 

* Informational (medium cohesion)

Create, delete, read and update BankTransaction objects (CRUD operations). This way the class will exhibit informational cohesion with four different methods.

* Utility (low cohesion)

Normally when it is not obvious for the methods to be group together, you end up defining it in a utility class with low cohesion. It also exhibit poor discoverability characteristic.

* Logical (medium cohesion)

You need to provide implementation for parsing from CSV, JSON and XML. For this purpose, you can group the methods responsible for different format inside one class.
In the book, the author describes an example called BankTransactionParser

``` 
public class BankTransactionParser {

    public BankTransaction parseFromCSV(final String line) {
        // ...
        throw new UnsupportedOperationException();
    }

    public BankTransaction parseFromJSON(final String line) {
        // ...
        throw new UnsupportedOperationException();
    }

    public BankTransaction parseFromXML(final String line) {
        // ...
        throw new UnsupportedOperationException();
    }
}
```

* Sequential (medium cohesion)
As the name indicates, you are grouping methods so they follow a sequence of input to output. A better approach is to break down each responsibility inside individual, cohesive classes.

* Temporal (low cohesion)
Performs several operations that are only related in time. Example: connecting and closing a database connection.

### Coupling

Cohesion is about how related things are in class, package or method, coupling is about how dependent you are on other classes. It is about how much knowledge you are relying on about certain classes. The more classes you are rely on, the less flexible you become when introducing changes. 

You can decouple different components by using an interface, which is the tool of choice for providing flexibility for changing requirements. Example are as follows:

```
public interface BankStatementParser {
    BankTransaction parseFrom(String line);
    List<BankTransaction> parseLinesFrom(List<String> lines);
}
```
Your BankStatementCSVParser will now become an implementation of that interface:
```
public class BankStatementCSVParser implements BankStatementParser {
    // ...
}
```
This way you can decouple the BankStatementAnalyzer from the parser by specific implementation of a BankStatementCSVParser. 

![image](/assets/images/RealSoftDev_Coupling.png)

## Rest API based App
By using the example code from the book, I started to work on a side project that will expose a file upload endpoint via Swagger API. The endpoint will consume any bank statement CSV file with date, amount and description as described in the book examples. However, I decided to create a microservice and dockerize it.  

## how to dockerize MySQL container


```
$ docker run --restart always --name mysql8.0 --net dev-network -v /Users/[your_username]/Develop/mysql_data/8.0:/var/lib/mysql -p 3306:3306 -d -e MYSQL_ROOT_PASSWORD=[your_password] mysql:8.0
```

## Reference

[Books](/_posts/2018-10-10-Books.md)
[Dockerize MySQL](https://medium.com/@crmcmullen/how-to-run-mysql-in-a-docker-container-on-macos-with-persistent-local-data-58b89aec496a)
[github link to my project](https://github.com/divyaspec/bank)
