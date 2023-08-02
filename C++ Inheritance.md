dg-home: false
dg-publish: true
---
Related: #programming 
Contents: [[NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 15-05-2023
***

- Extending [[C++ Classes]]

<https://ecs.wgtn.ac.nz/foswiki/pub/Courses/NWEN241_2023T1/LectureSchedule/NWEN241-W10-L1.pdf>

Extending a single base class:

```C++
class SubClass_Name : access_mode BaseClass_name {
	class_member_list
};
```

access_mode is one of the [[C++ Classes#Member Access Specifiers\|member access specifiers]]

# Example

- Because Dog is inherited from Animal, in Dog constructor you must invoke the Animal constructor explicitly (no [[Super constructors\|super]] like java) 

```C++
class Dog : public Animal {
	public:
		int bark(int loudness);
		int bite(int strength);
		void run(int speed);

		void eat(int food);

		Dog(const char *n) : Animal(n) {} // calling Animal constructor here

	private:
		int skills;
	
}
```

# Overloading

write two fns with same name and signature
only allowed with inheritance

# Overriding

- Allows us to have the same function in child class which is already present in parent class
- Like creating a new version of an old function, in the child class
- We always invoke the overridden method if there is one

```C++
Dog d;
d.eat(10);
```

To invoke base class function:

```C++
Animal::eat(10); //within member function of child class

// from instance
Dog d;
d.Animal::eat(10);
```

## Pointers and Inheritance

```C++
class Animal{
	public:
		void display()
		{
			cout << "display Animal" << endl;
		}
}

class Dog : public Animal{
	public:
		void display()
		{
			cout << "display Dog" << endl;
		}
}

int main(){
	Animal* bptr;
	Dog d;

	bptr = &d; // Valid because Dog is an Animal

	// Binded at compile time
	dptr->display();

	// Output: display Animal
}
```

## Run time Polymorphism

- Allow a member function to be called **based on the content** of the base class pointer rather than its **type**
- Implemented using [[Virtual Functions]]

```C++
class Animal{
	public:
		virtual void display()
		{
			cout << "display Animal" << endl;
		}
}

class Dog : public Animal{
	public:
		void display()
		{
			cout << "display Dog" << endl;
		}
}

int main(){
	Animal* bptr;
	Dog d;
	bptr = &d; 

	// Binded at compile time
	dptr->display();

	// Output: display Dog
}
```

## Abstract Classes

*Pure virtual function*

- Declared in the base class without any implementation

```C++
class Shape{
	public:
		// pure virutal function
		virtual float draw() = 0;

		virtual int getSides(){
			return 1;
		}
}
```

## Multiple Inheritance

- C++ supports multiple inheritance

```C++
class Subclass_name : access_mode1 Baseclass_name1, ...{}
```

### Example

- Constructors will always be invoked **left to right**

```C++
class Werewolf : public Human, public Dog {
	public:
		void transform();
		Werewolf(const char *n) : Human(n), Dog(n) {}

	private:
		int transformCount;
};
```

### Member Function Clash

```C++
class A : {
	public:
		void foo();
}

class B : {
	public:
		void foo();
}

class C : public A, public B {
	public:
		void foo(){
			// won't compile if not qualified
			
			A::foo(); // uses A's foo()	
		}
}
```

***

## Pointers

- Will decide what to call *based on type of pointer*
- Below pointer will call A
- This is **Static Binding**

```C++
B objB(1,2,3);

A *ptr = &objB;
ptr->disp(); // will decide what function to call based on type of pointer

```

- To get it based off the contents of pointer:
- Set base class method to **virtual**
- Enables **dynamic binding**
