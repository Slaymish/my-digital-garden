---
{"dg-publish":true,"permalink":"/design-principles/"}
---

Related: [[SWEN221/SWEN221 MOC\|SWEN221 MOC]]
Contents: [[SWEN225 MOC\|SWEN225 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN225_2023T2/CourseSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 04-09-2023
***

# Design Principles

Software:
- Software has to be **extensible**
- Should have *loose coupling* between components
	- Reduces the amount of side effects when extending the program

## Modularity

- Work with *interfaces*, not implementation
- Should use *the min amount of interfaces* for amount of modules ($n$)

$$Amount\  of\ interfaces = n-1$$


One way to do this is to use **Layering**
- This is what happens for networking ([[NWEN243 MOC\|NWEN243 MOC]])

### Loose Layering Vs Strict Layering

- With loose layering, all layers can be swapped out underneath the Application layers
	- Ie, Each layer uses the *interface* of the layers below, not the implementation
- Strict builds each layer on top, not allowing change to any of the above, without changing all the ones below

### Low Coupling & High Cohesion

- **What you want**
- Each 'package' has a well defined purpose
- In each package, the objects are tightly coupled together
- But *loose coupling between packages*
	- Allows to programs/modules to be extended/changed by only changing one part of the code

### High Coupling & Low Cohesion

- This is bad
- Anytime you change code, it may cause a number of *side effects* to propagate through the program

## [[Decomposability\|Decomposability]]

- Dividing things into less complex subtasks
- Means multiple ppl can work on it, dividing work
- Dependencies have to be explicit, in form of interfaces

[[Composability\|Composability]] is using *components* in environments **different** from the one they were initially developed

## Understandability

- Bad example: Modules only working if activated in a certain order eg: A then B then C.
- Instead: *lazy* initialisation
	- if objects are required to initialised before creating another
		- Check if obj null in constructor, insatiate it there
		- Then return card
		- Used in the [[Singleton Pattern\|Singleton Pattern]]

### Protection

- Not about stopping error but their *propagation*


***

```java
interface Displayable<I extends ImageType> {
	I getImage();
	void display();
}

interface ImageType {
	int[][] getImageAsRGB();
}

class PNG implements ImageType {
	int[][] pngArr;

	public PNG(int[][] rgbArr){
		pngArr = convertToPNGArr(rgbArr);
	}

	@Override
	public int[][] getImageAsRBG(){
		return convertToRGBArr(pngArr);	
	}
}

class JPG implements ImageType {
	int[][] jpgArr;

	public PNG(int[][] rgbArr){
		jpgArr = convertToJPGArr(rgbArr);
	}

	@Override
	public int[][] getImageAsRBG(){
		return convertToRGBArr(jpgArr);	
	}
}


class PNGCircle implements Displayable<PNG> {
	
}
```