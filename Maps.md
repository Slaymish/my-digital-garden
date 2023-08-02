---
dg-home: false
dg-publish: true
---
Related: #java #programming #data-structures
[[UNI MOC]]
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

```rust
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
    MyMap<Integer,String> mapp = new MyMap<Integer,String>();
    mapp.add(3, "testtt");
    mapp.add(1, "blehh");

	System.out.println(mapp.get(3)); // should print testtt
  }
}   

class MyMap<K extends Object,V extends Object> {
  private final int arraySize = 10; // larger size = less collisions
  private LinkedPair[] mapArray = null; 
  
  private void initArray(){
    mapArray = (LinkedPair[]) new LinkedPair[arraySize];
  }

  private int hash(K key){
   return (int) key.hashCode() % arraySize;
  }

  class LinkedPair{
    public Object key;
    public Object value;
    public LinkedPair next;
    public LinkedPair(Object _key, Object _value){
      key = _key;
      value = _value;
      next = null;
    }
  }
  
  public void add(K key, V value){
    if(mapArray==null) initArray();
    int index = hash(key);
    if(mapArray[index]!=null){
      LinkedPair slot = mapArray[index];
      while(slot.next!=null){
       if(slot.key==key) return; // dup key
       slot = slot.next; // might not work cus immutable??
      }
      slot.next = new LinkedPair((Object) key,(Object) value);
    }
    else{
      mapArray[index] = new LinkedPair(key,value); 
    }
 }

  public V get(K key){
    int index = hash(key);
    if(mapArray[index]==null) return null;
    LinkedPair slot = mapArray[index];
    while((K) slot.key!=key){
      slot = slot.next;
    }
    return (V) slot.value;
  }
}


```