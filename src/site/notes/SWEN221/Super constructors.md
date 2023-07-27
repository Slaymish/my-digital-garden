---
{"dg-publish":true,"permalink":"/swen-221/super-constructors/"}
---


# SWEN Super Constructors

Related: #java 
Contents: [[SWEN221/SWEN221 MOC\|SWEN221 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 07-03-2023
***

## Traditional Java Sub-classing

- Point is responsible to initialise x and y
- Point 3D may not even know x,y

```java
class Point{
	private double x;
	private double y;
	public Point(double x, double y){
		this.x=x, this.y=y;
	}
}


class Point3d extends Point {
	private double z;
	public Point3D(double x, double y, double z){
		super(x,y);
		this.z = z;
	}
	public double z(){return z;}
	public void z(double v){z=v;}
}
```

- 'super' has to be the first thing in constructor
- 'this' can only be used after the super call


- 'super' added for you, if not typed







