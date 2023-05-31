---
{"dg-publish":true,"permalink":"/suppliers-and-consumers/"}
---

Related: #java 
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 15-05-2023
***

# Suppliers and Consumers

```java
interface Supplier<T>{T get(); }
interface Consumer<T>{ void accept(T t);}
interface BiConsumer<T,U>{ void accept(T t, U u); }
```

Can implement a [[SWEN Lambdas\|lambda expression]] for when .get() or .accept() is called

## Supplier

- Defining supplier doesn't run its defined code
- has .get()

### Creating

```java
Foo f = A.doFoo(); // without supplier

Supplier<Foo> f = ()->A.doFoo(); // similar to c prepoccessor?
```

### Example

```java
void alice(Supplier<Cat> c){
	System.out.println(c.get().name());
}

void bob(){
	List<Cat> cats = new ArrayList<>(List.of(
		new Cat("bleh"),
		new Cat("gjfjd")
	));
	
	Supplier<Cat> c = () -> cats.remove(0);
	
	assert cats.size() == 3; // havn't removed any yet
	
	alice(c); // alice calls .get() on c, returning first cat
	
	assert cats.size() == 2; // alice took a cat
}
```

## Consumer

- Acts a way to *give cats*
- .accept()

### Example

```java
void alice(Consumer<Cat> c){
	c.accept(new Cat("belh"));
}

void bob(){
	Consumer<Cat> c = cat-> catList.add(cat);

	assert catList.size()==0;
	alice(c);
	assert catList.size()==1;
}
```

```java
// Alice decides *how* to accept cats
// Bob decides *when* to give cats and what cats

void alice(Consumer<Consumer<Cat>> c){
	List<cat> aliceCats = new ArrayList<>();
	c.accept(cat->aliceCats.add(cat));
}

void bob(){
	alice(cCat -> {
		cCat.accept(new Cat("Sbifdj"));
		cCat.accept(new Cat("jgdj"));
		cCat.accept(new Cat("wbjfe"));
	});
}
```

- cCat becomes: `cat->aliceCat.add(cat)`

```java
void alice(Consumer<Consumer<Cat>> c){
	var res = new ArrayList<>();
	c.accept(cat->res.add(cat));
	return Collection.unmodiifableList(aliceCats);
}

void bob(List<String> names){
	return makeList(c ->{
		for(String name:names){
			c.accept(new Person(name,"Brown"));
		}
	})
}
```

- Code is correct only if other user code can not break its contracts


***

