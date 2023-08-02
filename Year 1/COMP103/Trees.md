# Trees

Related: #java #graphs
Hamish Burke || 19-09-2022
***

## BTNode

-   “normal”
-   (2+5)*(12-4)
-   polish notation
-   - - 2 5 - 12 4



Polish notation:

-   Pre-order traversal
-   2+3+4+5+6
-   Represented with BTNode
-   With skewed tree

  
![[Pasted Graphic.tiff]]

# Different Types of Trees:

- [[General tree]] = any num of child nodes
- [[Ternary tree]] = At most three child nodes
- [[Binary tree]] = at most two child nodes ^fdf183

 

## Data Structures for General Trees

```java
public class Person{
	private String name;
	private int dob;
	private Set<Person> children;
```

-   Use **set** if don’t care about order
-   **List** if you do

  

## Garbage Collector

-   Once removed from root tree, java will delete it
	-   And all children

```
```

# Traversing General Trees:

## Recursive Depth First Traversal

*same as binary trees*

```java
public void printTree(Person child){
	if(p==null){return;} 
	UI.println(p);
	for(Person child:p.getChildren()){
		printTree(child);
	}
}
```

## [[Depth-First traversal]]

-   Treversing the tree by level

## [[Breath-first traversal]]:

-   Use a Queue<Person> todo
	while(not empty){
	p = todo.poll()
	print(p);
	for(child :p.getchildren(){
	todo.offer(child);


