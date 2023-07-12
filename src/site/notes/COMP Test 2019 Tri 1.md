---
{"dg-publish":true,"permalink":"/comp-test-2019-tri-1/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP261 MOC\|COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 31-05-2023
***

<https://ecs.wgtn.ac.nz/foswiki/pub/Main/ExamArchiveCOMP261/exam2019.pdf>

# Question 5: [[String Search\|String Search]]

a) 

```
Descibe search string of length M and text of length N which the Brute forve string search algorithm will perform the greatest (ie worst case). State how many comparison will be performed using big O notation
```

```
 Best Cost - Failing at the first pos
 O(M) or O(N)

Text: "A"
Search String: "B"

This will be one comparsion in this.
```

b) [[KMP Algorithm\|KMP Algorithm]]

```
Explain how the match table could be used to speed up the search

Using a partial match table speeds up the string search by adding a 'fail point' that tells the algorithm where to continue if it fails. The number in the table represent how far back you have to jump if a prefix of S has been matched

For example with the above table, if the match fails at index 6 or 8, the prev two characger matched were an A and a G (and that was the longest prefix of S that matched), so we can move along two posiitons and start matching at index 2 in S
```

i) 

```
Would you expect KMP to be much faster than Brute force search for finding phrases in the text of java programs?

Yes, as it would as it skips rechecking already known matched prefixes
```

# Question 6 [[Compression\|Compression]]

a) [[Huffman coding\|Huffman coding]]

```
mad_as_malaise

m = 2/14
a = 4/14
d = 1/14
_ = 2/14
s = 2/14
l = 1/14
i = 1/14
e = 1/14


((i+e)+a) + ((_+s)+((d+l)+m)) = 14/14
```