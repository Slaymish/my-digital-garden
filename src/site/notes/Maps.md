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

	slot-> next = struct mapData {key,object};
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

# Test Java Code

```java
class ToTest {
  public static void main(String[] args) {
    MyMap mapp = new MyMap();
    mapp.add(3,(Object) "testtt");

	System.out.println(mapp.get(3));
  }
}   

record MapData(int key, Object value, MapData next){
    MapData(int key, Object value){
      this(key,value,null);
    }

    public MapData setNext(MapData nextOne){
      return new MapData(key,value,nextOne);
    }
}

class MyMap {
  private final int arraySize = 10;
  private MapData mapArray[];

  public MyMap(){
    mapArray = new MapData[arraySize];
  }

  private int hash(int key){
    int randomPrime = 1204814; // my incrediblee hashing algorithm
    return key*randomPrime % arraySize;
  }


  
  public void add(int key, Object value){
    int i = hash(key);
    MapData slot = mapArray[i];
    if(slot==null){slot = new MapData(key,value);}
    while(slot.next()!=null){
      if(slot.key()==key) return; // dup key
      slot = slot.next(); // might not work cus immutable??
    }
    slot.setNext(new MapData(key,value));
  }

  public Object get(int key){
    int i = hash(key);
    if(mapArray[i]==null) return null;
    MapData slot = mapArray[i];
    while(slot.key()!=key){
      slot = slot.next();
    }
    return slot.value();
  }
}

 
```