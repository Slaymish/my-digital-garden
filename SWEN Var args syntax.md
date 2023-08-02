---
dg-home: false
dg-publish: true
---
Related: #
Contents: [[SWEN221 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 27-04-2023
***

# Var Args Syntax

```java
int foo(String... ps){
	return ps.length;
}

int bar(){
	return foo("a","b","c");
}
```

- use `...`
- If multiple params, has to be last one

```java
@SafeVarargs
static <T> int foo(T... ps){return ps.length;}

// need to suppress warning when using generics
```

- Be careful when you use @SafeVarargs

```java

@SafeVarargs
static <T> T[] foo(T... ps){return ps;}
// returning parameterized varargs arrays is bad!

static <T> T[] callBadIdea(T a){return badIdea(a,a,a);}
static String[] breakBadIdea(String a){return callBadIdea(a);}
// exception occurs

```

## Correct Use of Var Args

```java
@SafeVarargs
static <T> int foo(T... ps){return ps.length;}
// reading info from ps is ok (eg length, ps[0] etc)

@SafeVarargs
static <T> List<T> make(T... ps){return List.of(ps);}
// Can pass to any var args methods in std library
// as they are correct
```