---
dg-home: false
dg-publish: true
---
Related: #programming #java 
Contents: [[COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 21-05-2023
***

# String Search

"Given a string $S$ and a text $T$, look for an occurrence of $S$ as a substring of $T$"

## Variations

- Just check, returning boolean
- Find first/last/any occurrences of S in T
- Find all occurrences of S in T
	- What if occurrences overlap?
- Find occurrences as a whole word/anywhere?
- Find occurrences across line-breaks or not

# Implementing

- In java, can use:
	- `T.indexOf(S);`
	- `T.lastIndexOf(S);`
	- `T.contains(S);`

## Brute Force Search

```
String S = ananaba
Text: T = bannabanabanananaban

Look for S, starting at T[0]:
ananaba
bannabanabanananaban

Look for S, starting at T[1]:
 ananaba
bannabanabanananaban

Look for S, starting at T[2]:
  ananaba
bannabanabanananaban


Etc, till found, or none left
```

```java
for(int k = 0; k<(T.length-S.length);k++){
	if(T.subString(k, S.length()).equals(S)){return k;}
}
return -1;
```

### Improvements

- Don't call `length` in the loop
	- Store const as variable

- Don't call `subString` method in the loop
	- Don't need to copy the substring to a new string to compare with S

- Have a **fail point**
	- Where we should check next
	- When fail, it starts from here instead of start
	- Though its **unsafe** to jump all the way to end
		- Jump *before* fail point
	- Key idea of [[KMP Algorithm]]
		- Use characters in partial match to determine where to start next match attempt
	- [[Boyer-Moore]] as well

With improvements:

```java
int m = S.length();
int n = T.length();

for(int k = 0; k<(n-m);k++){
	found = true;
	for(int i = 0; i < (m-1);i++){
		if(S[i] != T[k+i]){ found = false; break;}
	}
	if(found){return k;}
}
return -1;
```

### Cost

 Best Cost - Failing at the first pos
 $$O(n) \ or\ O(m)$$
Worst Cost - Only failing at the last position
$$
O(???)
$$

