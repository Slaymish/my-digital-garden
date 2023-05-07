---
{"dg-publish":true,"permalink":"/making-a-tree-in-java/"}
---

Related: #java [[Year 1/COMP103/Trees\|Trees]]
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 06-05-2023
***

# Define a Tree

## Usage Eg

```java
Tree<Integer> empty = Tree.empty();
```

## Starting

```java
interface Tree<E>{
	int depth();
}

final class EmptyTree<E> implements Tree<E>{
	public int depth(){ return 0; }
}

interface NonEmptyTree<E> extends Tree<E>{}

record Leaf<E>(E label) implements NonEmptyTree<E> {
	public String toString(){ return label+""; }
}

record Node<E>(NonEmptyTree<E> left, NonEmptyTree<E> right) implements NonEmptyTree<E>{
	public String toString(){
	
	}
}

}
```