---
{"dg-home":false,"dg-publish":true,"permalink":"/swen-221/swen-inner-classes/","dgPassFrontmatter":true}
---

Related: #java #programming 
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 22-03-2023
***

# Static Inner Classes
- Just a way to do Hierarchical code organisation
	- packages -> classes -> static inner classes -> method etc
- Eg *Exp.BinOp* or *Exp.BinOp.Op*
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

# Non-static Inner Classes
- Static inner classes -> **Property** of classes
	- A single Foo.Bar class exists
- Inner classes -> property of instances
	- Each instance have its own (non-static) inner classes
	- *Like fields*






