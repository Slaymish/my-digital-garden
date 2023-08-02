---
dg-home: false
dg-publish: true
---
Related: #programming 
Contents: [[NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 24-05-2023
***

# C++ Templates

- Allows generic types
- Compiler doesn't generate code from definition of template
- generates code only when we use the type 

## Template Parameters

- Used to pass data types as an argument
- typename is legacy code

```C++
<class TYPE> /* or */ <typename TYPE>
```

## Function Templates

- Represents a *family* of functions
- header `<algorithm>` defines a collection of function templates
	- [[Standard Template Library]]

### Example

```C++
template <class T>

void printMax(T a, T b){
	cout<<"Max "<< (a > b ? a : b);
}

 // instantiate a specific instance of the template
printMax<int>(a,b); // compiler generates fn replaces each T with int
printMax<float>(a,b);
```

```C++
printMax(5,10); // int a , int b
printMax(5.0,10.0); // float a, float b

printMax(5,10.0); // Compiler dependent (usually generates error)
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
	Item() : Data(T()) { }
	
	void SetData(T nValue)
		{Data = nValue;}

	T GetData() const
		{return Data;}

	void PrintData()
		{cout << Data;}
};

Item<int> i1;
Item<float> f1;



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