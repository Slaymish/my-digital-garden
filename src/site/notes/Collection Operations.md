---
{"dg-publish":true,"permalink":"/collection-operations/"}
---

Related: #
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 17-05-2023
***

These operations are good to use with [[SWEN Lambdas\|SWEN Lambdas]]

# Collection Operations

## .forEach

- Iterate on the elements one at a time
- For maps
	- You get both keys and values

```java
void printLicensePlates(Map<Integer,Car> parkingLot){
	parkingLot.forEach( (slotId, car) ->
		System.out.println("Slot " + slotId + ": " + car.plate()));
}
```

## .removeIf

- Removes an element *if* it satisfies a predicate

```java
void removeTempEmails(ArrayList<String> emails){
	emails.removeIf(email -> email.startsWith("@temp.me"));
}

void removeBoomers(HashMap<String, Integer> nameToAge){
	nameToAge.entrySet().removeIf(e->e.getValue() >= 60); // updates the actual map
}
```

## .replaceAll

- xxx

```java
//

```