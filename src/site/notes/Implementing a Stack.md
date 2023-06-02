---
{"dg-publish":true,"permalink":"/implementing-a-stack/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 02-06-2023
***

# C++ Stack

- Use a [[NWEN241/NWEN Structures\|NWEN Structures]] to maintain individual records
	- Content
	- and Pointer to next
- Use [[C++ Classes\|C++ Classes]] to maintain stack

```C++
struct LinkedNode{
	char value; // data
	LinkedNode *next;

	LinkedNode(char c, LinkedNode *n){
		value = c;
		next = n;
	}

	LinkedNode(){}	
}
```

- `nullptr` = Typesafe way to specify its a pointer set to null (only in C++)
- Declare a [[C++ Constructors and Destructors\|C++ Constructors and Destructors]] with `~`

```C++
class LinkedStack{
	LinkedNode *top = nullptr;
	int count = 0;
	public:
	void push(char c){
		LinkedNode *newptr = new LinkedNode(c,top);
		top = newptr;
		count++;
	}
	char pop();
	void print();
	~LinkedStack(); // destructor
}
```

## Implementing Methods

```C++
char LinkedStack::pop(){
	LinkedNode *n = top;
	top = top->next;
	count--;
	char c = n->value;
	delete n;
	return c;
}

void LinkedStack::print(){
	LinkedNode *n = top;
	cout<<"\nElements in stack";
	while(n){
		char c= n->value;
		cout<<c<<" ";
		n = n->next;
	}
}

// Destructor 
LinkedStack::~LinkedStack(){
	while(top){
		cout<<"Destructor called";
		LinkedNode *d = top;
		top = top->next;
		delete(d);
	}
}
```