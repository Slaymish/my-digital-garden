---
{"dg-publish":true,"permalink":"/swen-study-notes/"}
---


Related: #java 
Contents: [[SWEN221/SWEN221 MOC\|SWEN221 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 09-05-2023
***

# SWEN Study Notes

## Generic Methods

```java
public static <T extends Point> T min(T p1, T p2){   
  if(p1.y<p2.y){return p1;}
  return p2;
}

public static <? extends Point> boolean min()

```

## Maps

- Cannot contain duplicate keys

```java
Map<K, V> map = new HashMap<>();

// K = key
// V = value/entry 
```


