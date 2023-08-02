---
dg-home: false
dg-publish: true
---
Related: #java 
Contents: [[SWEN221 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 24-05-2023
***

# Serialisation

*Aka marshalling*

- Turning an object graph into a set of bits

## Uses

- Bits can be saved to disk/send over network
	- Game save file
- JSON/XML formats serialize by piggy-backing on strings

## Deserialisation

- Go back from bits to the original (or similar) objects

# Java Serializable

- Java wanted to support **fully automatic** and general object serialisation
- If it solves your problem, best just to use (though can do manually if necessary)
- Handled automatically with this:
	- Aliasing is preserved
	- [[Cycles]] in graphs handled automatically
	- Lambdas/Anon inner classes
- **But** entire code needs to have @Serializable

## By Hand

- Often lost info about *aliasing* of the sub trees
- Sometimes needs
	- Eg if want to serialize/deserialize across diff languages
- When using [[Serialisation#Java Serializable\|Java Serializable]], **aliasing is preserved**

# Reachable Object Graph

- O inside ROG(O) // the object is inside ROG
- O' inside ROG(O) if O' is stored in a field of O or is captured by O, all fields are inside the ROG
- O'' inside ROG(O) if O' inside O

## Human Readable Encoding

- JSON
- XML
- CSV
Often used when data needs to be inspected/debugged/edited

- Slower to process
- More abstract, so more freedom to define how serialisation is done 

## Byte Format

- Converting objects into a binary stream of data
- Usually a **1-1 representation** of input
- Can work out of the box
- Java has `java.io.Serializable` interface
- Can be used for [[Deep Cloning]]

```java
byte[] serialize(Object o) throws IOException{
	var aux = new ByteArrayOutputStream();
	try(var out = new ObjectOutputStream(aux)){
		out.writeObject(o);
		out.flush();
	}
	return aux.toByteArray();
	// or can do a deep clone with this now
} // can print to disk/send etc

Object deserialize(byte[] data) throws IOException, ClassNotFoundException{
	try(var i = new ObjectInputStream(new ByteArrayInputStream(data))){
		return i.readObject();
	}
} // then cast as specifc type
```

# Using Serializable

```java
// simple for records
record Person(String name, int age) implements Serializable{}

// for classes, need the serialVersionUID
class Person implements Serializable{
	// handles code evoluton
	private static final long serialVersionUID = 1L;
}

// for lambda fns
interface MyFunction<T,R> extends Function<T,R>, Serializable{}
...
MyFunction<Integer,Person> solution1 = age-> new Person("Bob",age);

Function<Integer,Person> solution2 = (Function<Integer,Person> & Serializable)
										age -> new Person("BOB",age);
```

- [[Optionals]] are not serializable
- **Class instances** created with [[SWEN Reflection\|reflection]] and fills up fields (even final)
	- can/should declare a version and deserialising a class of a diff version would cause an error
- Records are created by calling the [[canonical constructor]]
	- Just get 'null' fields for fields that didn't exist at the time

- **Lambdas** we save:
	- Name of the functional interface this lambda is implementing
	- Location in code where lambda defined
	- Any captured vars that lambda uses

> [!INFO]
> Does **NOT** save the actual code (bytecode) of the lambda

# Serialize a `Supplier<T>` instead of a `T`

```java
interface SSupplierPerson extends Supplier<Person>, Serializable{
	static SSupplierPerson serializableForm(Person p){ // person isn't serializable
		String name = p.name();
		int age = p.age();
		return () -> new Person(name,age);
	}
}

// Serialize: Person -> SSupplierPerson -> byte[]
// Desserialize normally, cast to SSupplierPerson, and call get()
```

