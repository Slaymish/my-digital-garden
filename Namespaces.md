---
dg-home: false
dg-publish: true
---
Related: #programming 
Contents: [[NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 27-02-2023
***

# Namespaces

- Similar to [[Java Packages]]
- NOT [[C++ Classes]]

- Groups named entities
- Changes them from global scope, to [[namespace scope]]
- Namespace can be **repeated**
	- Can't have same elements

## General Syntax

```C++
namespace namespace_name
{
	members
}
```

### Example

```C++
namespace myns
{
	const int N = 100;
	int count = 0;
	void printResult(){
		cout<<N;
	}
}
```

***

- Scope of a namespace member is **local** to that namespace


To access members *outside* of namespace:

```C++
// namespace_name::memberName
myns::N // gets N int
myns::printResult();
```

If you don't want to have to define the namespace every time, use:

<h2 align="center">
using namespace myns;
</h2>

Then can access directly:

```C++
int x = N; // can use members directly
printResult();
```

Can make only a specific member visible:

```C++
using myns::N;
```

***

## Example Using Namespaces

```C++
#include <iostream>
using namespace std;

namespace foo
{
	int value(){ return 5;}
}

namespace bar
{
	const double pi = 3.1416;
	double value() { return 2*pi;}
}

int main() {
	cout << foo::value() << '\n';
	cout << bar::value() << '\n';
	return 0;
}
```

# Ifndef

```C++
#ifndef NAMESPACE_A
#define NAMESPACE_A
namespace abc{
	int x ;
}
#endif
```

- if namespace not already defined, code insides if's gets executed