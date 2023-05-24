---
{"dg-publish":true,"permalink":"/c-file-handling/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 24-05-2023
***

# Steps for File IO

1) Create file stream objects

```C++
ifStream fsin;
ofStream fsout;
fStream fsboth;
```

2) Open the file

## File Open Modes

| Name     | Des                |
| -------- | ------------------ |
| ios::in  | Open file to read  |
| ios::out | Open file to write |

```C++
fsIn.open("data.txt",fileOpenMode);
```

3) Check file opened properly

```C++
if(fsOut.is_open()) // returns true is file open

if(fsOut.bad()) // returns true for any errors
if(fsOut.eof()) // returns true if reached the end
if(fsOut.fail()) 

if(fsOut.good()) // returns false for any errors (kinda combines all of above)
```

4) Read/Write to files

### Formatted IO

- Can use stream insertion operator (<<) 
- Or stream extraction operator (<<)

```C++
fOut << a << " : " << c << " : " << s;

fin >> a1 >> c1 >> s1; // delimits by space and datatype
```

### Unformatted IO

- `int get();`  - Extracts a character from a stream and returns an int (ascii value)
- `istream & get (char & c);` Extracts character from stream, stores it in c, and returns the invoking istream reference

- ostream & put (char c); Insert char into stream returns stream reference

```C++
while((c=cin.get())!='\n')
{
	fOut.put(c);
}
```

### Reading [[NWEN241/NWEN Strings\|C String]]

- `istream& get (char * s, streamsize n);`
- `istream& get (char * s, streamsize n, char delim);`
	- Default delimiter is newline character

### Reading [[Strings in C++\|C++ String]]

- `istream& getLine (string);`


5) Close the file

```C++
fsIn.close();
fsOut.close();
```