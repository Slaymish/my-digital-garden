---
{"dg-publish":true,"permalink":"/swen-lambdas/"}
---

Related: #
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-04-2023
***

- Convenient syntax for [[SWEN221/Inner Classes#^b98b6a\|anonymous inner classes]]

EG:
- Code for event handler

```java
// Without lambdas
SwingUtilities.invokeLater(new Runnable() {
	public void run() {
		MiniGui g = new MiniGui();
		...
		JButton b = new JButton("---Bar---");
		b.addActionListener(new ActionListener() {
			public void action performed(ActionEvent e){
				System.out.println("Button pressed");
		}});
	...}});
```

```java
// With lambdas
SwingUtilitites.invokeLater(() -> {
	MiniGui g= new MiniGui();
	...
	Button b = new JButton("---Bar---");
	b.addActionListener(e->System.out.println("Button Pressed"));
	...});
```

***

# Syntax

```java
p -> p.getAge()

(p1,p2)-> p1.getAge()>p2.getAge()

()->System.currentTimeMillis()

(customer,product)->{
	if(customer.getAge()<25 && product.hasAlcohol()){
		return "Show id!";
	}
	return "Do u need reciept?";
}

String::length // instance method
System::currentTimeMillis // static method
List<String>::size // explicit type args for generic type




// These three are all the same
p->p.getAge()

(Person p) -> p.getAge()

p->{return p.getAge();}
```

***

# Functional Interfaces

- Interfaces with at least one method

- `Function<T,R>`
	- Has
		- identity()
		- compose()
		- andThen()

Example of function:

```java
Function<Int,Tint> add2 = x->x+2;
Function<Int,Tint> multiply2 = x->x*2;

System.out.println(
	add2.andThen(multiply2).apply(1));
```

- `Consumer`
	- A function that eats up a value
	- Has
		- accept()
		- andThen()



- `Supplier<T>`
	- A kind of function that takes no arguments
	- `()->new Point(12,3)`
	- Has 
		- a get method returning a value of type T


- `Predicate<T>`
	- Has
		- test() - returns boolean



***

EG:

```java
// TO avoid this kind of repetition

public static int reduceSum(List<Integer> list){
	assert !list.isEmpty();
	int res = list.get(0);
	for(int i=1;i<list.size();i++){res = res + list.get(i);}
	return res;
}

public static int reduceMult(List<Integer> list){
	assert !list.isEmpty();
	int res = list.get(0);
	for(int i=1;i<list.size();i++){res = res * list.get(i);}
	return res;
}


------


public interface Reduce<T>{
	T apply(T e1, T e2);

	public static <T> T of(List<T> list, )
	
}
```

***

# `Optional<T>`

- Makes null pointer exceptions less prominent

```java
Optional<Person> marco = Optional.of(new Person("Marco",34));
Optional<Person> nope = Optional.empty();

if(marco.isPersent()){ ... }
```

`map()` 
- method applies a function to the value in the `Optional<T>` and returns a new `Optional<U>` instance as the result. 

`flatMap()` 
- method applies a function that returns an `Optional<U>` to the value in the `Optional<T>`, and returns the result directly.

`filter()` 
- method tests the value in the `Optional<T>` against a predicate and returns an `Optional<T>` that is empty if the predicate fails the test.

`ifPresentOrElse()` 
- method provides a way to safely handle the case where an `Optional<T>` is present or not present. If the value is present, the first `Consumer<T>` parameter is invoked, otherwise the second `Runnable` parameter is invoked.


