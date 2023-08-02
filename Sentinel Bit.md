---
dg-home: false
dg-publish: true
---
Related: #programming #java  [[Compression]]
Contents: [[COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 19-05-2023
***

# Sentinel Bit

Can be used in [[Compression#Variable Length Codes\|Variable length codes]] as a possible fix to decide boundaries

between different symbols. This is an extra bit that is added at the end of each code to indicate the end of a symbol. 

Can also be used as an option for [[Framing]]

## Example

Let's take an example where we want to encode the following four symbols with their respective frequencies and corresponding variable length codes:

```
Symbol   Frequency   Code
A         5           0
B         3           10
C         1           110
D         1           111
```

Now, let's encode the string "ABACAD". Without using sentinel bits, the encoded string would be:

`010110110111`

It's difficult to determine when one code ends and another begins. However, if we use a sentinel bit (let's say "0"), we can clearly distinguish between the codes:For example, let's consider the following codes:

A: 110
B: 01
C: 111

We can use the sentinel bit "0" to separate these codes as follows:

A: 1100
B: 0100
C: 1110

Now, when we combine these codes together, it becomes easy to identify where one code ends and another begins:

Original message: A B C A B
Encoded message with sentinel bits: 11000100111011000100

To decode this message, we can simply read the bits in groups separated by the sentinel bit "0":

Decoded message: A B C A B

> [!failure]- Failure 
>   Error: There is another generation process
>   
>   - plugin:obsidian-textgenerator-plugin:56949 TextGenerator.eval
>     plugin:obsidian-textgenerator-plugin:56949:31
>   
>   - Generator.next
>   
>   - plugin:obsidian-textgenerator-plugin:78 eval
>     plugin:obsidian-textgenerator-plugin:78:61
>   
>   - new Promise
>   
>   - plugin:obsidian-textgenerator-plugin:62 __async
>     plugin:obsidian-textgenerator-plugin:62:10
>   
>   - plugin:obsidian-textgenerator-plugin:56935 TextGenerator.generate
>     plugin:obsidian-textgenerator-plugin:56935:12
>   
>   - plugin:obsidian-textgenerator-plugin:58440 AutoSuggest.eval
>     plugin:obsidian-textgenerator-plugin:58440:52
>   
>   - Generator.next
>   
>   - plugin:obsidian-textgenerator-plugin:78 eval
>     plugin:obsidian-textgenerator-plugin:78:61
>   
>   - new Promise
>   
>  
