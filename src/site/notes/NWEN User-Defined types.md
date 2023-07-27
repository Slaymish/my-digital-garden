---
{"dg-publish":true,"permalink":"/nwen-user-defined-types/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

# Enumeration

- Used to assign identifiers to **integral constants**

```C
enum enum_tag {name_0, name_1, ...., name_n} variable_list;
```

- *enum_tag* and *variable_list* are optional

## Can Override Integer Assignment

```C
enum colors {red = 3, yellow = 2, green = 1};
```

Can create an *alias*

```C
typedef enum color {red,yellow,green} color_t;
```

# Using

```C
enum colors { red, yellow = 3, green }

int main(void)
{
	enum colors fgcolor = blue, bgcolor = yellow;

	printf("%d %d\n", fgcolor, bgcolor);
	/* Will print 5 3 */

	return 0;
}
```

- Can't reuse an identifier (eg 'red')


***

# Unions

- Like a [[NWEN241/NWEN Structures\|struct]]
- But different fields take up the same space in memory
- Last thing assigned, will be the value of the union
![SCR-20230329-sqn.png](/img/user/SCR-20230329-sqn.png)

```C
union union_tag {
	type1 member1;
	type2 member2;
	...
} variable_list;
```

## Application:

- Data structure for a record which can contain at least 2 type, but only one type is active at any given time
- Good for saving memory (compared to structs), when you know only one of the values is active 

# Tagged Union

```C
enum record_type {MOVIE,BOOK};

struct data {
	enum record_type type;
	union value {
		struct movie m;
		struct book b;
	} value;
};
```

***

# Linked Lists

- Node in linked list declaration

```C
typedef stuct node
{   char data;
	struct node *next;
} Nodes;
```

**Node var init:**

```C
NOde node4 = {'t', NULL};
Node node3 = {'s', &node4};
Node node2 = {'i', &node3};
Node node1 = {'l', &node2};
Node *head = &node1
```

## Singly-Linked List Traversal

```C
Node *p = head;
for ( ; p != NULL; p = p->next)
	printf("$c", p->data)
```

next: [[NWEN File Stream IO\|NWEN File Stream IO]]
