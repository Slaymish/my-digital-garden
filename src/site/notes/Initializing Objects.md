---
{"dg-publish":true,"permalink":"/initializing-objects/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 20-06-2023
***

# Way to Initialize Objects

## Default Initialization

```C++
student_info s;
```

- Undefined values if default constructor is not included
	- **Garbage values**

## Value Initialization

```C++
student_info s{};
```

- If no constructor given, values of members are set to zero
	- 0 for int, null terminator for string

## Direct Initalixation

```C++
student_info s{1,"John"};
student_info s(1,"John");
student_info s(); // not allowed
```

## Copy Initialization

```C++
student_info s{1, "John"};
student_info s1(s);

// or

student_info s1 = s;
```

Since C++11, supports brace initialisation

```C++
// All valid
int a = 5;
int a(5);
int a{5}; 
```

## Explicit Constructor

```C++
class A
{
public:
	A(int x) : i(x) { }

	int get() { return i; }

private:
	int i; 
};

void printobject(A a)
{
	int i = a.get();
	cout << "Object : "<<i<<endl;
}

int main(){
	A a1(2);
	printobject(a1);

	printobject(10);  // this will work
	// will implicitly convert to class unless explicit keyword added
}
```

```C++
class A
{
public:
	explicit A (int x) : i(x) { }

	//... rest of code
}
```