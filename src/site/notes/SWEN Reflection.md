---
{"dg-publish":true,"permalink":"/swen-reflection/"}
---

Related: #
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 26-04-2023
***

# Whats Reflection?
*access with java.lang.Class*


```java
Class<? extends Point> myClass = this.getCLass();
Class<? extends Object> objClass = obj.getClass();
if(myClass != objClass){return false;}
```

```java
String.class == "Foo".getClass(); // .class is a language feature


Class<?> x = belh.getClass(); // same as Class<? extends Object>
```


# Methods
```java
Object o = new SimpleClass();

Class<?> c = o.getClass();

Method[] ms = c.getDeclaredMethods();
for(Method m: ms){
	//print m.getName();
}
```

- o.getClass()
	- Returns Class<\?>
- c.getDeclareMethods()
	- Returns all public and private user declared methods
- c.getMethods()
	- Returns all methods in class (though not private methods)


# Invoke methods through reflection
*Surround in try/catch*

- Method m = c.getMethod("aSimpleMethod");
- m.invoke(c);

Can throw:
- NoSuchMethodException
- InvocationTargetException
- IllegalAccessException


# Get/Set fields
```java
Field f = o.getField("aField");
f.get(o,f); // 2
f.set(4,f); // sets field to 4 (only if public)

//if private
f.setAccessable(true); // throws inaccessableObject in certain conditions
f.set(4,f); // Allows for changing private fields 
```



# Why is reflection useful
*Used to plug-in loading and automatically upgradable programs*

```java
Class<?> c = Class.forNmae("question.QW0_0");
Question q = (Question)c
	.getDeclaredConstructor()
	.newInstance();

// Now can use question object with any more reflection
```


