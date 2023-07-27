---
{"dg-publish":true,"permalink":"/swen-stream-method/"}
---

Related: #
Contents: [[SWEN221/SWEN221 MOC\|SWEN221 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 08-05-2023
***

# Stream Method

See [[Java Streams\|Java Streams]]

## Stream.of()

- Empty stream constant

## Stream.concat(left.stream(), right.stream())

- Recursively concatenate

### Example in [[Making a tree in java\|Making a tree in java]]

```java
record Node<E>(NonEmptyTree<E> left, NonEmptyTree<E> right) implements NonEmptyTree<E>{
	public Stream<E> stream(){ return Stream.concat(left.stream(),right.stream();)}
}
```

***

# Iterator

- Similar to scanner

- Methods
	- .hasNext()
	- .next()


There's no Iterator.of():

```java
interface Tree<E> extends Iterable<E> {
	public Iterator<E> iterator(){
		return List.<E>of(label).iterator(); 
	}
}
```

## Custom Iterator

```java
class TreeIterator<E> implements Iterator<E>{
	private final ArrayList<NonEmptyTree<E>> stack = new ArrayList<>();
	public boolean hasNext(){ return !stack.isEmpty();}

	public TreeIterator(Node<E> n){ stack.add(n); } 
	// the top lvl nodes the next node to visit

	public <E> next(){
		if(!hasNext()){throw new NoSuchElementException();}
		var last = stack.remove(stack.size() - 1); // remove the end thing
		return last.itAdvance(stack).label(); // next left + grow stack
	}
}
```

***

