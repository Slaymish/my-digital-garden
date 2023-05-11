---
{"dg-publish":true,"permalink":"/intro-to-c/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

# Intro to C++

- *Most* C programs can run on a C++ compiler

## Difference with C

- Strong type checking
- New data types
- Classes
- OOP
- A standard library (STL)
	- String
	- List
	- stacks etc
- [[SWEN Generics\|Generic]] programming
- Exceptions for [[SWEN221/Error Handling\|Error Handling]]


## Writing C++ Code

- Save as  .cpp
- [[NWEN241/NWEN Run your code#Run C++\|Running C++]]

## Headers

- Library header are **not** supposed to have an extension
- Though still works with .h/.hh/.hpp
- Most libraries come with a xxx.h and cxxx file

```
#include <stdio.h> == #include <cstdio>
```

***

# Datatypes

- Character
- Integer
- Float
- Double
- Boolean
- Wide


Uses the [[C++ Standard Library\|C++ Standard Library]]


[[Namespaces\|Namespaces]] are used to organize code into logical groups
> [!failure]- Failure 
>   Error: There is another generation process
>   
>   - plugin:obsidian-textgenerator-plugin:56949 TextGenerator.eval
>     plugin:obsidian-textgenerator-plugin:56949:31
>   
>   - Generator.next
>   
>   - plugin:obsidian-textgenerator-plugin:78 eval
>     plugin:obsidian-textgenerator-plugin:78:61
>   
>   - new Promise
>   
>   - plugin:obsidian-textgenerator-plugin:62 __async
>     plugin:obsidian-textgenerator-plugin:62:10
>   
>   - plugin:obsidian-textgenerator-plugin:56935 TextGenerator.generate
>     plugin:obsidian-textgenerator-plugin:56935:12
>   
>   - plugin:obsidian-textgenerator-plugin:58440 AutoSuggest.eval
>     plugin:obsidian-textgenerator-plugin:58440:52
>   
>   - Generator.next
>   
>   - plugin:obsidian-textgenerator-plugin:78 eval
>     plugin:obsidian-textgenerator-plugin:78:61
>   
>   - new Promise
>   
>  
