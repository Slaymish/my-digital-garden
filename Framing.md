---
dg-home: false
dg-publish: true
---
Related: [[NWEN241 MOC]]
Contents: [[NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 13-07-2023
***

# Framing

- [[Data Link Layer]] Service

- Determining where a 'dataframe' begins and where it ends

## Dataframe

- Sequence of bits that form a unit of data from sending node to receiving node

## Using Special Bytes/bit-sequences (Option 1)

Can use [[Sentinel Bit]] to indicate the start and end

Problem is that that sequence of bits may come up in the data

### Bit-stuffing or Character-stuffing

- To fix this, escape the characters

Eg: Bit-stuffing

- Sending `011111110`
- After 5 1's, Sender inserts 0 before transmitting next bit
- Receiver then ignores a zero after 5 1's

## Specifying Frame Length (Option 2)

- Include number of bytes in frame in frame header
- A transmission error could corrupt the count field

## Clock-based Framing (Option 3)

- Still have a bit-pattern to specify start, and keep frame fixed
- But no bit-stuffing
- Checks when it sees the bit-pattern against time 


