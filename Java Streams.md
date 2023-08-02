---
dg-home: false
dg-publish: true
---
Related: #java 
[[UNI MOC]]
Hamish Burke || 09-05-2023
***

# Java Streams

Source->Filter->Sort->Map->Collect

## Intermediate Operations

- Filter 
- Map
- sort

Return a **stream** 

## Terminal Operations

- forEach
- collect
- reduce

Return either void or a non-stream result


***

### Foreach

applies the same function to each element

### Collect

saves the elems into a collection



***

# Examples

```java

IntStream
	.range(1,10)
	.skip(5) // skip first 5 elems
	.forEach(x -> System.out.print(x))


// will pirnt 6 7 8 9

```

```java
Stream.of("Avf","giud","gdhuu")
	.sorted()
	.findFirst()
	.ifPresent(System.out::println);

// will print first item in sorted list
```

```java
List<String> aNames = new List<String>();
String[] names = {"gjgj","giig","ghduh","ahh","afuh"};
Arrays.stream(names) // same as Stream.of(names)
	.filter(x -> x.startsWith("a"))


	.forEach(aNames::add);

// will add all aNames to list
```

## Map

```java
map each integer to its square

ints.stream()
	.map(x -> x*x) // return stream (transforms whats there)
	.forEach(System.out::println); // print each square num


	.
```

***

# Combining

```java

// ### Find the tallest person of being for x city and return their name

return ps.stream()
	.filter(x -> x.city().equals(targetcity))
	.sort(Comparator.comparing::Person.height)
	.map(Person::name)
	
	
```

***

# .collect

==**Terminal function**==

```java
List<String> kids = ps.stream()
	.filter(x -> x.height>120) 
	.map(x -> x.name)
	.collect(Collectors.toList()); // returns a collection

kid.forEach(x -> {
	assert (x.name.isLowerCase())
})

// will throw an assert error if any of the kids that can go on the ride inputted their name wrong

```

# .count()

**Returns an int of how many items their are in the stream**

```java

ps.stream()
	.filter(x -> x.height>target)
	.count();

// Returns an int of how many ppl are above the target
```

***

# Two Options

**For functions inside streams**

```java
ps.stream()
	.filter(x -> x.age<18) // lambdas
	.map(x -> x.name) // or .map(Person::name)
	


List<String> validPpl = ps.stream()
	.filter(Person::IsValid)
	.map(Person::name)
	.collect(Collector.toList())
```

