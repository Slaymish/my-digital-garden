---
{"dg-publish":true,"permalink":"/swen-221/swen-inheritance-and-subtyping/"}
---

Related: #java #programming 
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 02-03-2023
***

### Withers:
- Instead of mutating an object, create a new one *with* diff data
```java
Horse withLocation(Point2D dest) 
{
	// Returns new obj with new position
	return new Horse(name,dest);
}
```

***

## Inheritance
- Enables code reuse within a class hierarchy
- Avoids code duplication

Implementing inheritance:
```java
interface Animal {
	String name(); // fields are now just methods
	Point2D location();
	double speed();
	void draw(Graphics2D g);
	Animal withLocation(Point2D dest);

	default Animal run(Point2D dest){
		double s = this.speed();
		double diffX = dest.x-this.x
		//blah ablha blha
	}
	
}
```


Now for the specifc animal classes:
```java
// Horse class
record Horse(String name, Point2D location) implements Animal
{
	public Horse withLocation(Point2D dest)
	{
		return new Horse(name,dest);
	}

	public double speed(){return 10d;}
	public void draw(Graphics2D g){/*..*/}
}

// Dog class
record Dog(String name, Point2D location) implements Animal
{
	public Dog withLocation(Point2D dest)
	{
		return new Dog(name,dest);
	}

	public double speed(){return 10d;}
	public void draw(Graphics2D g){/*..*/}
}
```
- Record creates a new object for every change instead of mutating
***
Example of **mutable** running animal:
```java
interface Animal{ 
	String name(); 
	Point2D location(); 
	void location(Point2D location); // a setter! 
	double speed(); 
	void draw(Graphics2D g); 
	default void run(Point2D dest){ 
		double s = this.speed(); 
		double diffX = dest.x()-location().x(); 
		double diffY = dest.y()-location().y(); 
		// blahflahfhaldfadb not complete
	}
}
```

and implementing that into classes:
```java
class Horse implements Animal{
	public Horse(String name, Point2D location)
	{ 
		this.name=name; 
		this.location=location; 
	}
	public Point2D location(){ return location; } 
	
	public void location(Point2D location)
	{
		this.location=location;
	}
```

> [!Naming for getters and setting]
> Instead of naming the getLocation/setLocation etc,
> Just name location().
> 
> Getters with have no params, and setters will have one.


- When using immutable design for inheritance, use records
- Use classes for mutable objects
	- More verbose

***


## Overriding
{ #ec882d}


- At runtime, the computer explores the hierarchy and searches for the most specific implementation

EG:
```java
interface A{
	default String m() { return "A";}
}

interface B extends A{
	default String m() { return "B";}
}

interface C extends B{
	default String m() { return "C";}
}

System.out.println(new C().m());
```

This would return C

> [!Java Docs]
> Adding @Override pulls any documentation for the overridden method


***
**Subtyping:**
- Enables code reuse for our users
	- Usually means less code in the program at large


<p align="center">
Submethods > comments for code sections
</p>

- This is becuase you can overide methods
- Doing this is called 'the template method pattern'
```java
interface HouseDrawing extends Drawing{ 
	default void draw(Graphics2D g){ 
		drawWall(g); 
		drawWindows(g); 
		drawDoor(g); 
		drawRoof(g); 
		} 
	default void drawWall(Graphics2D g){
		g.setColor(Color.GRAY); 
		g.fillRect(50,200,3);
	}
```