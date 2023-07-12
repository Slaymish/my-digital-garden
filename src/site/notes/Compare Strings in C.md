---
{"dg-publish":true,"permalink":"/compare-strings-in-c/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

# Compare String Insensitive to case in C

You can compare strings in C without considering the case by converting both strings to either uppercase or lowercase and then using the strcmp() function to compare them. Here's an example of how to do this:

```c
#include <ctype.h>
#include <stdbool.h>
#include <stdio.h>
#include <string.h>

// Function to convert a string to lowercase
void toLowerCase(char *str) {
    for (int i = 0; str[i]; ++i) {
        str[i] = tolower(str[i]);
    }
}

// Function to compare two strings case-insensitive
bool caseInsensitiveCompare(const char *str1, const char *str2) {
    char lowerStr1[strlen(str1) + 1];
    strcpy(lowerStr1, str1);
    toLowerCase(lowerStr1);

    char lowerStr2[strlen(str2) + 1];
    strcpy(lowerStr2, str2);
    toLowerCase(lowerStr2);

    return strcmp(lowerStr1, lowerStr2) == 0;
}

int main() {
    const char *str1 = "Hello";
    const char *str2 = "hello";

    if (caseInsensitiveCompare(str1, str2)) {
        printf("The strings are equal (case-insensitive).\n");
    } else {
        printf("The strings are not equal (case-insensitive).\n");
    }

    return 0;
}
```