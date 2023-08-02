# Collections

![[Java Collections Library (in java.util) 1.png]]

- Manipulate info in lots of ways
- Collection is an object that contains other objects
- Can be different structures
- For tree structures, we will need to make our own
- We need to know what operations are expensive

## Standard Collections:

- Bag
	- just collection of values (unodered)
- set
	- not repeating, unordered
- map
	- Key/Value Pair
- list
- queue
- stack
- tree
- graph

## Different Structures:

- No structure
	- just collection of values
- Linear structure of values
	- order matters
- Set of key-value pairs
- Grid/table
- hierrchial structures
- networked structures

## Different Constraints:

- Duplicates?
	- get put remove anywhere?
	- or only at end/top etc

***

# Abstract Data Types:

- ADT is a type of data, described at an abstract lvl

## Set ADT:

- Conceptual
- Collection of items with no structure and no duplicates

### Operations

- Add()
- remove()
- contain() - boolean

### Behaviour

- A new set contains no values
- A set will contain a value iff the value has been added to the set and has not been removed
- A set will not contain a value if its never been added, or has been removed