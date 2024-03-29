---
{"dg-publish":true,"permalink":"/file-stream/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

# Stream Buffering

*common pitfall when dealing with file streams*

- If you don't close file properly, stuff you've written will remain in buffer

```C
char str[100];
scanf("%s", str); // User types "The quick brown fox"

// str will only be assign "The"
```

## Modes

| Mode          | Description |     
| ------------- | ----------- | 
| Unbuffered      |    Character written/read from an unbuffered stream are transmitted indivually to or from the file asap      |     |
| Line buffered | Transmitted in blocks when a newline character is encountered           |    
| Fully buffered             | Transmitted to/from file in block of arbitrary size           |

- Newly open stream are **fully buffered** by default
	- Except streams connected to interactive devices (they are line buffered)
- Can change buffering mode 


***

## C Has Access to 3 File Streams:

- stdin
- stdout
- stderr
	- Mostly used for error logging


- printf uses stdout


***

- <stdio.h> provides methods for accessing streams

***

## Stream I/O Functions

- fscanf
- fprintf
- fread
- fwrite
- ...

***

# Opening a File

*A file must be opened before it can be used*

```C
FILE *fp; // pointer to stream
fp = fopen(filename, mode); // can be absolute or local path
```

Example

```C
FILE *fp;
fp = fopen("mydata","r"); // opened for reading only

-------

FILE *fp;
fp = fopen("file.csv","w"); // Creates a file for writing

------

FILE *fp;
fp = fopen("file.csv","a"); // Creates a file (if doesn't exist), otherwise appends to file
```

**Check is fopen() succeeded**

```C
FILE *fp;
fp = fopen("data","r");
if(fp == NULL){
	printf("File open failed.\n");
	return 0;
}
```

***

# Closing a File

- Entire buffer will be flushed

```C
fclose(fp); // close the file

---

fflush(fp); // write buffer to file (only needed with 'w' and 'a')
```

***

## fscanf()

- Same as scanf() except need stream (FILE *) as a arg
	- scanf()  = reads formatted input from stdin stream
	- fscanf() = reads formatted input from specified stream
- Returns number of words read

EG:

```C
int a,b;
FILE *fp;
fp = fopen("datafile","r");
fscanf(fp, "%d %d", &a, &b);


// scanf("%d", &a) == fscanf(stdin, "%d", &a)
```

- '%x' interprets input as hex num
	- Can also be used to write a num as hex to file


***

# Detecting End of File

- End-of-file indicator (EOF) informs the program when there are no more data (no more bytes) to be processed
- fscanf() returns EOF if end-of-file is rached, or errors were encountered when reading from stream

Example:

```C
int ret, var;
ret = fscanf(fp, "%d", &var);
if (ret == EOF){
	printf("end of file encountered.\n");
}
```

--- OR ---

- feof() function returns a non-zero value (true) or zero (false) condition
	- TRUE if EOF reached (or errors encountered during read)
	- FALSE otherwise

EG:

```C
int var;
fscanf(fp,"%d",&var);
if(feof(fp)){
	printf("end of file encountered.\n");
}
```

***

# fprintf()

eg:

```C
int a = 100, b=200;
FILE *fp;
fp = fopen("datafile","w");
fprintf(fp,"%d %d",a,b);
```

***

# Example

*Capitalise the first letter of each line*

```c
#include <stdio.h>
#include <ctype.h>

int main(void)
{
	FILE *in, *out;
	char line[100];


	in = fopen("somewhere.txt","r");
	if(in==NULL){
		printf("Error opening input file.\n");
		return -1;
	}

	out = fopen("Somewhere.txt","w");
	if(out==NULL){
		printf("Error opening output file.\n");
		return -1;
	}

	while(!feof(in)){
		fgets(line,99,in); //gets line
		line[0] = toupper(line[0]); // first char of line
		fprintf(out,"%s",line);
	}


	fclose(in);
	fclose(out);
}

```