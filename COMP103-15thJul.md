    

# Abstract Data Types (interfaces):

- Bag
- List
	- Ordered Collection
- Set
	- Unordered, no duplicates
- Queue
	- Ordered collection, limited access
- Map
	- Key-value pairs

# Classes:

- List classes
	- ArrayList, linkedList,vector

- Set classes
	- Hashset, treeSet, Enumset, LinkedHashSet

- Map classes
	- EnumMap
	 - HashMap

  

**Java Interfaces and ADT’s**

  

- A java interfaces corresponds to an ADT

- Specifies what methods can be called on objects of this type
- Behaviour of methods is only given in comments
- **No constructors**
- **No fields**

  

eg:

```java
public interface Set<E> {
	public boolean add(E item);
	public boolean remove(E item);
	public boolean contains(E item);
}
```

## Use ADT as Type, Create Using Classname

### Example

`Set<students> students = new HashSet<students>();`

- Using **Set** instead of **HashSet** on left hand side

Why not just use class?

- Variable is now of type `Set`
- Meaning anything that takes a List, 

More examples:

old:

`ArrayList<Double> nums = new ArrayList<Double>();`

  

new:

`List<Double> nums = new ArrayList<Double>();`

  

  

**Stack (is an exception):**

- No interface - so class so:
- `Stack<Action> myStack = new Stack<Action>();`

Operations:

- Empty() - bool
- push(item) - push an item onto the top of the stack
- pop() - removes and _returns_ the item at top of stack
- peek() - return item on top of stack

  

  

## Code Style:

- drop ‘this’
- Leave out {} when just one statement

- eg

- if (true) println(“yey”);

  

## Undo:

- use a **stack**
- add a record of everything you do to stack
	- has to be more than just object, as you need to know weather to add/remove
- Pop the top of stack off
- Make new class (brickAction)

- vars

- actionStr (add/move/delete)
- brick (object itself)

- new Stack<Brickaction> in main class
- after each action, push onto stack

  

  

  

Collection:

- Like a bag