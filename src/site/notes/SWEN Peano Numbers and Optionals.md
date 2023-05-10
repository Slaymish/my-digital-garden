---
{"dg-publish":true,"permalink":"/swen-peano-numbers-and-optionals/"}
---

Related: #
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 10-05-2023
***

[[Minecraft Bug - If statements\|Why ifs are bad]]

# Peano Numbers

Peano numbers are a simple representation of natural numbers, based on the axioms proposed by Italian mathematician Giuseppe Peano. 

- A group of numbers
- Select a designated "zero" number
- Each time we make a request, a new number is produced
- The numbers never repeat.

```java
public interface N{
	static N zero(){ return new N(){};} // not defining any nums except for this
	default N add(N other){return other;}
	default N times(N other){return this;}

	default N succ(){
		N pred = this; // as i'm creating my successor, this is the predecessor
		return new N(){
			public N add(N other){return pred.add(other).succ();}
			// (a+1) + b = (a+b) + 1
			
			public N time(N other){return pred.times(other).add(other); }
			//. (a+1)*b = (a*b) + b

			public int toInt(){return pred.toInt()+1; } // for n amount of elems
				// add 1 to return (recursive)
		}
	}

	default int toInt(){return 0;} // until it adds zero (top elem)
	static N fromInt(int i){}
}
```

***

## Runs to Zero Operator

```java
if(sutff --> 0){...}
while(stuff --> 0){...}

// Actully just two operators

if(sutff-- > 0){...}
while(stuff-- > 0){...}

```

****

- Lecture 11 
	- For lab

