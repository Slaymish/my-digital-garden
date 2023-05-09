---
{"dg-publish":true,"permalink":"/swen-term-test-3-prep/"}
---


Related: #
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 07-05-2023
***

# SWEN Term Test 3 Prep

[[SWEN221/SWEN_Infomation#^a534a9\|Normal vs Capped]] -- Two options for marking

## Term Test 2 Review

### Friends Class:

```java
class Friends{
	Map<Cat,Integer> get(){return Map.of(
		new Cat("Furry",1.5),1,
		new Cat("Oscar",2.0),2,
		new Cat("Lucky",2.5),3
	);}
}
```

- Force yourself to read **character by character**

### Castle Towers:

- Use records!
- new Castle.Tower means Tower is a static nested class
	- Because we couldn't use static, we had to use **record**

Using a compact constructor

```java
record Castle(List<Tower> towers){
	Castle{
		assert tower.size() >= 4;
		assert tower.stream().allMatch(t-> t.height() >= 5);

		int maxH = towers.stream()
			.max(Comparator.comparing(t->t.height()))
			.get() // Supplier.get method
			.height();
			
		assert tower.stream()
			.filter(t->t.height()==maxH)
			.count() == 1; // count returns amount of values left

		for(var ti: towers){
			assert towers.stream() // basically a double for loop
				.filter(t-> t==ti)
				.count() == 1;
		}
	}

	record Tower(int height){}
}
```

- Ok to iterate on data multiple times
- We can use .get() since we know that there are at least 4 towers
- Use var when it can be multiple different types (or anytime)

Could also write the max height assert as this:

```java
assert towers.stream()
	.map(Tower::height) // or .map(t -> t.height())
	.max(Integer::compare)
	.map(maxH -> towers.stream()
		.filter(t -> t.height() == maxH)
		.count() == 1
	)
	.get();
```

And the double for like this:

```java
assert towers.stream()
	.allMatch(ti -> towers.stream()
		.filter(t->t==ti)
		.count()==1
	);
```

### When to Use T Vs ?

- You use T instead of ? when you are using T in scope
- When you are declaring a generic type or record
	- use ``<name>``
- When you are using something that has a generic type (List)

A time you'd use T:

```java
record Pasta<S extends Sauce>(S sauce) // using S here
{
	int fats(){ return sauce().fat()+2; }
}
```

A time you'd only need ?:

```java
class FoodProcessor {
    void process(List<? extends Food> foods) { // only need ? here
        for (Food food : foods) {
            // do something with the food objects
        }
    }
}
```

***

# Term Test 3

- Similar to TT2
- Including material up to lecture 21
- no preview features
- **Study Lab 5**
- myobject.getClass() is the most reflection used


Marco hinted something similar to this, where you can't use run




![SCR-20230507-x2w.png](/img/user/SCR-20230507-x2w.png)





***

```java

public static <T> void printMe(List<T> ray){
	ray.forEach(System.out::println);
}
```

```java

class Plant{
	String name;
	int height;

	public Plant(String name, int height){
		this.name = name;
		this.height = height;
	}

	public int getHeight(){
		return height;
	}
}

record Daisy extends Plant(String name, int height, Color petalColor){}

public static void main(){
	String name = findTallestPlant(
			List.of(
				new Plant("Pixie",105),
				new Plant("Womper",120),
				new Daisy("Engle",204),
				new Daisy("EINC",180)));

	Sytem.out.println(name);
}

public static <T extends Plant> findTallestPlant(List<T> fs){
	return fs.stream()
		.max(Comparator.comparing(Plant::getHeight))
		.getHeight();
	
}
```

***

# Anonoymouse Inner Calss

```java

public class AnonClass{
	public static void main(String[] args){
		Animal
	}

}
```

***

# something.getClass()

```java

"helloworld".getClass() // returns class object 'java.smth.String'

assert var1.getClass()==var2.getClass(); // asserts for classes the exact same

