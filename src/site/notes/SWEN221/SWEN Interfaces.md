---
{"dg-publish":true,"permalink":"/swen-221/swen-interfaces/"}
---

Related: #java [[SWEN221/SWEN Inheritance and Subtyping\|SWEN Inheritance and Subtyping]]
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 08-03-2023
***

# Interfaces

```java
interface Chest{
	List<Item> get();
	default void depositItem(Item i) { /* ...*/}
}

interface Minecart{
	Point position();
	void position(Point val);
	default void move(Map map){/*...*/}
}

class MinecartChest implements Chest, Minecart{
	Point position;
	List<Item> items = new ArrayList<>();
	public MinecartChest(Point p){position(p);}
	public List<Item> get(){return this.items;}
	public Point position(){return this.position;}
	public void position(Point val){ this.position = val;}
}
```

> [!You can have multiple implementations!]

- Can't extend multiple classes though

## Subtyping Recap

### Properties:

- Transitive
	- If X <: Y and Y <: Z then X <: 
- Reflexive
	- X <: X

# Primitive Types Dont Have Normal Casting:

- Less precise <: more precise
- int <: float
- float <: double

Narrowing conversions require explicit coercion

```java

// Example of coercion
float a = 3f;
int b = (int) a; // needs the (int)

// Example of casting not requiring coercion
int a = 3;
float b = a;
```

<h4 align="center">
Type coercion != Class Cast
</h4>
- Coercion creates a new number
- Class cast is just a check

