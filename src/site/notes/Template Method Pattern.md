---
{"dg-publish":true,"permalink":"/template-method-pattern/"}
---

Related: [[SWEN221/SWEN221 MOC\|SWEN221 MOC]]
Contents: [[SWEN225 MOC\|SWEN225 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN225_2023T2/CourseSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 31-07-2023
***

# Template Method

- Have a abstract class that defines the functions
- Define the specifications in the implementations   
- Defer responsibilities
- Allows for extensions

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
}
```