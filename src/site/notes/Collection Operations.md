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

# Lambda Collection Operations

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

- Can use for Lists and Maps, not Sets
	- Because its a one-to-one transformation, and sets can't have duplicates
- Replace all values with result of an operation

```java
void angryMob(List<Person> ps){
	ps.replaceAll(p -> ps.setAngry()); 
}

void resetMap(Map<String,Integer> map){
	map.replaceAll((event,eventCount) -> 0); // will set all eventCounts to 0
}

```

## .merge(key, Val, whatIfPresent)

- Only for maps
- Returning `null` in lambda removes that entry
- If entry not there, .merge acts as .put

```java
void updateScore(Map<String,Integer> playerScores, String name, int newScore){
	playerScores.merge(name,newScore,Math::max);
	// or
	playerScores.merge(name,newScore (oldS,newS) -> Math.max(oldS,newS));;
}


void updateScore(Map<String,Integer> playerScores, String name, int newScore){
	playerScores.merge(name,newScore (oldS,newS) -> {
		if(newS<0){return null;} // will remove if score < 0
		return Math.max(oldS,newS);
	}
}
```

## .compute("bob", (k,oldV)->newV)

- Similar to .merge
- Put can have a specific behaviour when the entry isn't there

```java
void updateInventory(Map<String,Integer> inventory, String id,int newAmount){
	assert newAmount >= 1;
	inventory.compute(id, (productId,oldAmount)->
		oldAmount== null ? newAmount-1:oldAmount+newAmount);
	)
}
```

### .computeIfAbsent("bob",k->v)

- If the key **is** present, does nothing and just returns currently mapped value
- `.computeIfPresent("bob",(k,oldV)-> newV)` also exists
	- Though not rly used

```java
private Image _getImage(String fName){ ... }

private final HashMap<String,Image> cache = new HashMap<>();

Image getImage(String fName){ // if value already exists, will just return
	// Tho if not, will call private method
	return cache.computeIfAbsent(fName, this::_getImage);
}
```

***



***

# Non Lambda Collection Methods

## List.subList

- Give a **view** of a part of a list
- Keep perms you have (if can mutate or not)
- Used for:
	- Recursive calls
	- Mutating a part of the list without touching rest

```java
int binarySearch(List<Integer> sorted, int e){
	// .. 

	if(midValue > e){ return binarySearch(sort.subList(0,mid),e);}
	return binarySearch(sorted.subList(mid+1,size), e) + mid + 1;

	// Splits list into three parts
}
```

## Map.getOrDefault(key, Default value)

- If element not there, return default value instead of null

```java
// if customer not there, will return 0
return customerPoints.getOrDefault(customerId, 0); 
```

