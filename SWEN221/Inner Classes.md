---
dg-home: false
dg-publish: true
---
Related: #java #programming 
Contents: [[SWEN221 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 22-03-2023
***

# Static Inner Classes

- Just a way to do Hierarchical code organisation
	- packages -> classes -> static inner classes -> method etc
- Eg *Exp.BinOp* or *Exp.BinOp.Op*
- Have no outer pointer
	- So can't access field/methods of enclosing class

```java
public interface Exp{
	public static class StringLiteral implements Exp{
		String value;
	}
	public static class FieldAccess implements Exp{
		Exp reciever; String fName;
	}
	public static class MethodCall implements Exp{
		Exp reciever; String fName; List<Exp> params;
	}
	public static class BinOp implements Exp {
		Op op; Exp left; Exp right;
		public static enum Op{Plus,Minus,And,Or}
	}
}
```

- Inner records are implicitly static

***

# Non-static Inner Classes

- Static inner classes -> **Property** of classes
	- A single Foo.Bar class exists
- Inner classes -> property of instances
	- Each instance have its own (non-static) inner classes
	- *Like fields*

![[SCR-20230322-k29.png]]

- To use pos in the inner class
	- **Not** this.pos
	- InternalIter.this.pos

***

## External Construction

```java
class Shape {
	// ...
	public class Square {
		private int x,y,w,h;
		public Square(int x,int y, ..){
			/// ...
		}
	}
}
```

- To create a square object

```java
Shape outer = new Shape();

Shape.Square square = outer.new Square(0,0,8,42);
// or 
square = new Shape().new Square(0,0,8,42);
```

***

## Method Local Inner Classes

```java
class Outer {
	public Outer create(final int field){
		class Inner extends Outer {
			private int myfield = field;
			// ..
		}

		return new Inner();
	}
}
```

- Define classes in a method


***

# Anonymous Classes

^b98b6a

- Used everywhere
- An extension of existing class
- Can override methods/define fields
	- Instead of making a new 'MyList extends ArrayList' etc

```java
public static void main(String[] args){
	List<String> myList = new ArrayList<String>(){
		// override ArrayList.add
		public boolean add(String x){
			System.out.println("ADDED: " + s);
			return super.add(x);
		}
	};
}
```

![400][SCR-20230322-kl7.png]

![400][SCR-20230322-ko3.png]
- Good way to start up a swing app
![400][SCR-20230322-kpm.png]
- After java8, use Lambdas for event handling instead

- Lambdas 'play the role' of an a anon inner class
	- Though only for interfaces with 1 abstract method

![400][SCR-20230322-l8q.png]
- Useful for circular graph projects
- Can be used for any deep copy 
	- Can Cut and paste this

![[SCR-20230322-la8.png]]

