---
{"dg-publish":true,"permalink":"/c-static-members/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 15-05-2023
***

# Static Members

- [[C++ Classes\|C++ Classes]] can contain static members
- Is a variable **shared** by all instances of class

```C++
#import <iostream>
using namespace std;

class Time{
	public:
		static int getCounter();
		Time();


	private:
		static int counter;
}


// Create constructor
Time::Time(){
	hour = 0; //etcetc
	counter++;
}

// Have to qualify with class name
int Time::counter = 0; // class specifc, not obj specifc

// define static member function
int Time::getCounter()
{
	return counter;
}


int main(void)
{
	cout << Time::getCounter() << "\n"; // count == 0
	
	Time time1; // create a time obj, and incr count
	cout << Time::getCounter() << "\n"; // count == 1
}
```

