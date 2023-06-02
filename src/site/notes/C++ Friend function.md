---
{"dg-publish":true,"permalink":"/c-friend-function/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 02-06-2023
***

# Friend Function

- Make all members (even private) visible to method
- Used in [[C++ Classes\|C++ Classes]]

```C++
class Myset{
	int size;
	public:
		Myset(int size){
			this -> size = size;
		}

	friend show();
};

void show(){
	Myset s(10);
	cout << "size: "<<s.size<<endl; // access private 'size'
}
```