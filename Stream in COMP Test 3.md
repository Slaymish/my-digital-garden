# Stream in COMP Test 3

```java
public int bottleNeck(ArrayList<Edge> path){
	return path.stream()
		.min(Comparator.comparing(Edge::capacity))
		.get().capacity();

	// or (old way)
}
```