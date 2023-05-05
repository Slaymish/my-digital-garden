---
{"dg-publish":true,"permalink":"/swen-generics/"}
---

Related: #
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 02-04-2023
***

# Generics

*Create classes, interfaces, and methods that can work with any data type*

- Generics use type parameters that are defined when the class or method is declared.
	- Type parameters are typically represented using a single uppercase letter, such as 'T'.

- Acts similar to a local variable
- Can't do `instanceof` on a generic

```java
class Vec<T> {
	private T[] elems = (T[]) new Object[16];
	private int end = 0;
	public void add(T e){
		if (end == elems.length){...}
		elems[end] = e;
		end+=1;
	}

	public T get(int index){
		if(index >= end){ throw ...}
		else { return elems[index];}
	}
}

Vec<Cat> v = new Vec<Cat>();
v.add(new Cat());
Cat c = v.get(0); // Don't have to cast (when using generics)
```

***

# Shape EG (Generic Classes)

```java

interface Shape { void draw(Graphics g);}

class Square implements Shape {...}

class ShapeGroup<T extends Shape> implements Shape{
	private List<T> shapes = new ArrayList<T>();
	...

	public void draw(Graphics g){
		for(T s: shapes){
			s.draw(g);
		}
	}
}
}
```

## Using it

```java
ShapeGroup<Square> sg1 = new ShapeGroup<Square>();
sg1.add(new Square());
```

**Alternative to above**

```java
interface Shape { void draw(Graphics g);}

class Square implements Shape {...}

abstract class ShapeGroup<T> implements Shape{
	abstract void draw(T t, Graphics g);
	
	private List<T> shapes = new ArrayList<T>();
	...

	public void draw(Graphics g){
		for(T s: shapes){
			s.draw(s,g);
		}
	}
}
}

```

```java
class A<T>{...} == class A<T extends Object>{...}

class A<B extends C> {...}
```

- 'B' is a **type variable** of kind 'C'


***

# Generic Methods

```java
class Point{int x;int y;}
class ColPoint extends Point {int color;}

class Aux1 {
	<T extends Point> T min(T p1, T p2) {
		var p1IsMin = p1.x<p2.x || (p1.x==p2.x && p1.y<p2.y);
		if(p1IsMin){return p1;}
		return p2;
	}
	
	void foo(){
		ColPoint c1 = new ColPoint();
		ColPoint c2 = new ColPoint();

		c1 = this.<ColPoint>min(c1,c2);
	}
}
```

***

# Var Type

```java
final class Var<T> {
	private T f;
	private Var(T f){ this.f=f;}
	T get() {return f;}
	void set(T f){this.f = f;}
	@Override public String toString(){return f.toString();}
	@Override public int hashCode() {return f.hashCode();}
	@Override public boolean equals(Object o){
		if(!(o instanceof Var<?> v)){return return false;}
		return f.equals(v.f);
	}
}
```

- Now can define records with 'updatable fields'

```java
record Person(Var<String> name, Var<Integer> age){}
```

***

- [ ] Read generics reading in resources

***

```java
void doSomething(List<Object> os){
	os.add(new Integer(1));c //eg this would break it
}

void foo() {
	List<Object> os = new ArrayList<Object>();
	List<String> ss = new ArrayList<String>();


	doSomething(os); // works
	doSomething(os); // doesn't work
}
```

Instead generics:

```java
class Cup<T> {
	T f;
	Cup(T f){
		this.f = f;
	}
}

Cup<Tea> myCup = new Cup<Tea>(new Tea());
```

## Wildcards Type

```java
Cup<?> myCup = CupProvider.getCup();

// can add bounds
Cup<? extends Drink> myCup = CupProvider.getCup();
```

## Subtyping

- `Cup<Tea> ≠ Cup<Object>`
- `Cup<Tea> = Cup<?>`
- `Cup<Tea> = Cup<? extends Drink>`
- `Cup<? extends Tea> = Cup<? extends Drink>`



***

# Wildcard Capture

- Wildcard type = '?'
	- EG `List<?> x`

```java
void m(Cup<?> c) {
	this.test(c);
}

<X> void test(Cup<X> cx){

}

void swap(ArrayList<?> list){
	swapTwo(list);
}

<X> swapTwo(ArrayList<X> l){}
```

***

# Lower Bound

```java
static <T> void sort(List<T> list, Comparator<? super T> c)

// Sorts the specified list according to the order induced by the specified comparator
```

- Super indicates lower bound
- The comparator is able to compare any kind of super elements with respect to T is accepted
	- EG a list of ColoredPoints can be compared with a Comparator<Point>
