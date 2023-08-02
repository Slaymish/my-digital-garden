## Standard Template Library (STL)

### Containers

- [[Containers]] are data structures that store objects and provide methods to access, insert, and delete elements.
- The Standard Template Library (STL) provides several container classes for common data structures like arrays, lists, and queues.
- Some commonly used containers in STL are:
  - std::vector: A dynamic array that automatically resizes itself when elements are added or removed.
  - std::list: A doubly-linked list that provides fast insertion and deletion of elements at any position.
  - std::deque: A double-ended queue that allows insertion and deletion of elements from both ends.
  - std::map: An associative container that stores key-value pairs in a sorted order.
  - std::set: A collection of unique elements in a sorted order.

### Iterators

- Iterators are objects that allow traversing through the elements of a container in a sequential manner.
- They act as an abstraction for pointers and provide a uniform interface for accessing elements in different containers.
- STL provides five types of iterators:
  - Input Iterator: Allows reading the value of an element (forward direction only).
  - Output Iterator: Allows writing the value of an element (forward direction only).
  - Forward Iterator: Supports reading and writing operations in the forward direction only.
  - Bidirectional Iterator: Supports reading and writing operations in both forward and backward directions.
  - Random Access Iterator: Supports direct access to any element within the container.

### Algorithms

- STL provides generic algorithms that can operate on various data structures through iterators.
- Some commonly used algorithms include:
  - Sorting (sort, stable_sort, partial_sort): Sorts the elements in a specified range according to a comparison function or operator <.
  - Searching (find, find_if, binary_search): Searches for an element or an element satisfying a condition within a specified range.
  - Permutations (next_permutation, prev_permutation): Generates the next or previous lexicographically ordered permutation of a sequence.
  - Numerical operations (accumulate, inner_product, partial_sum): Performs various numerical operations on elements of a sequence.

### Template Functions

- Template functions allow writing generic functions that can work with different data types.
- They provide a way to create reusable code without having to write separate functions for each data type.
- A template function is defined using the template keyword followed by a list of template parameters enclosed in angle brackets.

