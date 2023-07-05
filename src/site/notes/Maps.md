---
{"dg-publish":true,"permalink":"/maps/"}
---

Related: #
[[UNI MOC\|UNI MOC]]
Hamish Burke || 06-07-2023
***

# Maps

- Have a key and a value
- Key gets hashed, then modulo by the size of the storage array
	- This becomes the index to insert the data at
- Store both the value **and** the key 
	- Needed for later retrieval and deletion

## If Multiple Keys Have the Same Hash

- Can use store multiple items at the same hash
	- Using arraylist, or linkedlist
- Walk through list at hash, and check given key against stored key
	- This is why you store both

### Pseudocode

```
fn hash(inputstr : string) -> int 
{
	int longIndice = hash(inputstr)
	return longIndice % storageSize // mod the calculated hash by storage size
}

struct mapData {
	string: key,
	object: value,
	struct mapData: next
}


fn addItem(key : string, value : object) 
{
	int indexToAddAt = hash(key) // index I need to add it at
	struct mapData slot = mapArr[indexToAddAt]
	while(slot->next != null)
	{
		if(slot->key == key){return -1;} // break as duplicate key
		slot = slot->next;
	}

	mapArr[indexToAddAt] = struct mapData {key,object};
}

fn getItem(key: string) -> object
{
	int index = hash(key);
	if(mapArr[index]==null){return -1;} // not found
	struct mapData slot = mapArr[index];
	
	while(slot->key != key)
	{
		slot = slot->next;
	} 
	return slot->value;
}
```