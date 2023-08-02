---
dg-home: false
dg-publish: true
---
Related: #programming #java 
Hamish Burke || 08-07-2023
***

# List

- Abstract Data type 
- **Interface**

## Classes Implementing the List Interface

- ArrayList
- LinkedList
- etc etc

## To Declare

```java
List<String> names = new ArrayList<String>();
```

- Creates a **List** of type **ArrayList** that can hold only String

## Operations with Lists

```java
names.add("Hamish");
names.add("Jack");
names.add("Emma");
```

- As we set the type of list to String, the add method for names can only take Strings as a input
- If we try add a different type, **your code won't compile**

```java
names.add(20); // This will not work
```

## Lists of other Types

```java
List<Integer> intList = new ArrayList<>();
List<Double> doubleList = new ArrayList<>();
```

- Can't use **primitive type** as the type
- This means use `Integer` instead of `int`
- and `Double` instead of `double`


