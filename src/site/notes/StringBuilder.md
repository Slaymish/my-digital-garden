---
{"dg-publish":true,"permalink":"/string-builder/"}
---


# StringBuilder

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 24-03-2023
***

1. StringBuilder is a mutable class, allowing for efficient manipulation of strings.
2. Merging strings using "+" operator creates a new String object, causing performance issues in large concatenations.
3. StringBuilder should be used when you need to perform multiple string concatenations to avoid excessive memory usage.

**Example Code:**

```java
public class StringBuilderExample {
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder(); // create an empty StringBuilder object

        // append values
        sb.append("Hello,");
        sb.append(" World!");

        // insert values
        sb.insert(5, " Java");

        // delete values
        sb.delete(5, 10);

        // reverse StringBuilder
        sb.reverse(); 

        // convert StringBuilder to String
        String finalStr = sb.toString();

        System.out.println(finalStr); 
        // Output: !dlroW ,olleH
    }
}
```

**Using StringBuilder over Strings:**
StringBuilder is more efficient when appending multiple times, as it avoids creating new String objects for each concatenation. This reduces memory and CPU usage, improving performance.