---
{"dg-publish":true,"permalink":"/testing-with-mock-objects/"}
---

Related: #
Contents: [[SWEN221/SWEN221 MOC\|SWEN221 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 24-05-2023
***

[[SWEN221/Java Testing\|Java Testing]]

```java
record DuplicateFinder(ArrayList<Path> toDelete, Path root){
	public void deleteAllDuplicateFiles(){
		assert toDelete.isEmpty();
		...
		Files.walk(root)
			.filter(/* only text files */)
			.forEach(this::checkIfDuplicate);
		for(var p:toDelete){Files.delete(p);}
	}
}
```

To test code like above, don't really just want to run it (as could delete everything)

System programmer: Use a docker image!
OO programming answer: Use mocks!

# Mocks

- An object or method that:
	- does not do the expected task on the actual resources,
	- but facilitates testing by doing a simulated version of the task

## To Use Mocks

- Could separate above into two type, **FileAccess** and **DuplicateFinder**
- Why using an interface here?
	- Want dynamic dispatch
	- If you can use an interface, **use an interface**

```java
interface FileAccess {
	default String readFile(Path path){
		try { return Files.readString(path);}
		catch(IOException e){throw new UncheckedIOException(e);}
	}
	default void writeFile(Path path, String content){
		...
	}
	
	default void deleteFile(Path path){
		...
	}
	
	default Stream<Path> walk(Path path){
		try { return Files.walk(path);}
		catch(IOException e){throw new UncheckedIOException(e);}
	}

	static FileAcesss instance(){return new FileAccess(){};}
}
```

```java
record DuplicateFinder(FileAccess files, ArrayList<Path> toDelete, ){
	public void deleteAllDuplicateFiles(){
		assert toDelete.isEmpty();
		files.walk(root)
			.filter(p->p.toString().endWith(".txt"))
			.forEach(this::checkIfDuplicate);
		for(var p : toDelete){files.deleteFile(p);}
	}

	void checkIfDuplicate(Path pi){
		if(toDelete.contains(pi)){return;}
		String content = files.readFile(pi);
		files.walk(root)
			.filter(p->p.toString().endsWith(".txt"))
			.filter(p-> !p.equals(pi))
			.filter(p->files.readFile(p).equals(content))
			.forEach(toDelete::add);
	}
}
```

### To Test

- Start by making a MockFileAccess
- can have a **log** instead of performing the actions
	- The more you log, the more precise, but need more verbose tests

```java
record MockFileAccess(ArrayList<String> log, Map<Path,String>map) implements FileAccess{
	public String readFile(Path path){return map.get(path);}
	public void writeFile(Path path,String content){throw new Error();}
	public void deleteFile(Path path){log.add("Deleted " + path);}
	public Stream<Path> walk(Path path){
		log.add("walking on " + path);
		return map.keySet().stream()
			.sorted(Comparator.comparing(Path::toString));
	}

}
```

```java
@Test
void testNoDupFiles() {
	var log = new ArrayList<String>();
	var fa = new MockFileAccess(log,Map.of(
		Path.of("a"),"",
		Path.of("a","b.txt"),"bText",
		Path.of("a","c.txt"),"cText",
	));
	var deleted = new ArrayList<Path>;
	var df = new DuplicateFinder(fa,deleted,Path.of("a"));
	assertEquals(List.of(),deleted);
	assertEquals(List.of("walking on a","walking on a","walking on a"),log);
}
```

## Test Structure

1) Initialise the data
2) Run the operations
3) Check the result satisfies our expectations
4) Check that the log satisfy our expectations

# Limits of Mock Testings

- we are only testing against the behaviour of our mocks

