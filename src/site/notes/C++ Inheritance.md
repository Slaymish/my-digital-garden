---
{"dg-publish":true,"permalink":"/c-inheritance/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 15-05-2023
***

- Extending [[C++ Classes\|C++ Classes]]

<https://ecs.wgtn.ac.nz/foswiki/pub/Courses/NWEN241_2023T1/LectureSchedule/NWEN241-W10-L1.pdf>

Extending a single base class:

```C++
class SubClass_Name : access_mode BaseClass_name {
	class_member_list
};
```

access_mode is one of the [[C++ Classes#Member Access Specifiers\|member access specifiers]]

# Example

- Because Dog is inherited from Animal, in Dog constructor you must invoke the Animal constructor explicitly (no [[SWEN221/Super constructors\|super]] like java) 

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
- Implemented using [[Virtual Functions\|Virtual Functions]]

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