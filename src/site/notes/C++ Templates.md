---
{"dg-publish":true,"permalink":"/c-templates/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 24-05-2023
***

# C++ Templates

- Allows generic types
- Compiler doesn't generate code from definition of template
- generates code only when we use the type 

## Template Parameters

- Used to pass data types as an argument

```C++
<class TYPE> /* or */ <typename TYPE>
```

## Function Templates

- Represents a *family* of functions
- header `<algorithm>` defines a collection of function templates
	- [[Standard Template Library\|Standard Template Library]]

### Example

```C++
template <class T>

void printMax(T a, T b){
	cout<<"Max "<< (a > b ? a : b);
}

// using
printMax<int>(a,b);
printMax<float>(a,b);
```

## Class Templates

- Allow classes members to use template parameters as types
- Represents a family of classes

```C++
template <parameter list> class_declaration;
```

- Each parameter can be:
	- A type parameter `class T`
	- A non-type parameter `int SIZE`
	- A template template parameter

### Example

```C++
template <class T>
class Item
{
	T data;
public:
	Item() : Data(T())
	{}
	void SetData(T nValue)
		{Data = nValue;}

	T GetData() const
		{return Data;}

	void PrintData()
		{cout << Data;}
};
```

### Writing Member Functions outside Class Template

```C++
template <class T>
	void item<T>::disp(){
		cout<<"bleh";
	}
```

## Variable Templates

- Defines a family of variables

```C++
template < parameter-list>
variable-declaration;
// The declared variable name become a template name
```