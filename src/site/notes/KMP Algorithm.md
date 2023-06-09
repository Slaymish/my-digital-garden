---
{"dg-publish":true,"permalink":"/kmp-algorithm/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 24-05-2023
***

# Knuth-Morris-Pratt Algorithm

- After a mismatch, advance to the earliest place where search string could possibly match
- *Faster* than a simple [[String Search\|String Search]]

> [!INFO]
> NEVER has to re-check a character

## How far Can We Advance?

- Use a table based on the search string
- Let `M[0..m-1]` be a table showing how far to back up the search if a prefix of S has been matched

- If mismatch at string position s (and text pos t+s)
	- find the longest *suffix of text* (up to just before the fail point) that matches a *prefix of string*
	- move k forward by (i-length of prefix)
	- keep matching from i = length of prefix
- Special case:
	- if i=0, then move k = k+1, and match from i=0

## How Do Build the Jump Table?

- Look for a proper suffix of failed match, which is a prefix of S, starting at each position of each position in S
- **So suffix ends at previous position**

<table>
  <tr>
    <th>Index</th>
    <td>0</td>
    <td>1</td>
    <td>2</td>
    <td>3</td>
    <td>4</td>
	<td>5</td>
	<td>6</td>
  </tr>
  <tr>
    <th>S</th>
    <td>a</td>
    <td>n</td>
    <td>d</td>
    <td>a</td>
    <td>n</td>
	<td>d</td>
	<td>b</td>
  </tr>
  <tr>
    <th>M</th>
	<td>-1</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>1</td>
    <td>2</td>
    <td>3</td>
  </tr>
</table>

### Building the Jump Table

```
input : S[0 .. m-1] // the string
output: M[0 .. m-1] // match table

initalise: M[0] <- -1, M[1] <- 0
j <- 0 // position in prefix
pos <- 2 // position in table

while pos < m
	if S[pos-1] = S[j] // substrings ..pos-1 and 0..j match
		M[pos] <- j+1,
		pos++, j++
	else if j > 0
		j <- M[j] // mismatch, restart the prefix
	else // j = 0 (run out of candidate prefixes)
		M[pos] <- 0,
		pos++
```

## Pseudocode

```
input: string S[0..m-1], text T[0 .. n-1], partial match table M[0 .. m-1]
output: the position in T at which S is found, or -1 if not present

// declare vars
k = 0; // start of current match in T
i = 0; // pos of current character in S

// loop
while ((k+i)<n){
	if S[i] = T[k+i] then // match
		i = i + 1
		if i=m then return k // found S
	else if M[i] = -1 then // mismatch, no self overlap
		k = k + i + 1
		i = 0
	else // mismatch, with self overlap
		k = k + i - M[i] // match pos jumps forward
		i = M[i]
}

return -1 // failed to find S
```