---
dg-home: false
dg-publish: true
---
Related: [[SWEN221 MOC]]
Contents: [[SWEN225 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN225_2023T2/CourseSchedule)
[[UNI MOC]]
Hamish Burke || 02-08-2023
***

# Observer Pattern

Also known as [[Publish-Subscribe Pattern]]

When you want to **send events** to *observers*
- Implicit Invocation

## What is it

- **notify observers** when subject sends event
- Want to *reuse observers* for different subjects
- Enables **loss coupling** between *subjects* and *observers*

Can be used in the [[Model-View-Controller]] Pattern

### Specification

- Subject superclass
	- notify()
	- attach(Observer)
- Observer interface
	- update() abstract method
- Concrete subjects *implement* Subject superclass
- Concrete observers *implement* Observer interface

### Implementation

```java
class Subject{
	Collection<Observer> obs;
	void notify(){
		for(Observer o: obs){ o.update();}
	}
}

interface Observer {
	void update();
}

class Board extends Subject {
	void stateChanged(){
		this.notify(); // sends a notify msg to itself
	}
}

class BoardCanvas implements Observer {
	void update(){
		// do stuff here
	}
}
```

#### To Subscribe

```java
public static void main(String[] args){
	print("enter value:")
	Model model = new Model();
	model.addObserver(new Observer(){
		public void update(Observable obj, Object arg){
			print("recieved response: " + arg);
		}
	});
}
```

### Implementations in Java

- KeyListener
- MouseListener

**java.util.Observable** == Subject
**java.util.Observer** == Observer

Send events *pressed* and *released*