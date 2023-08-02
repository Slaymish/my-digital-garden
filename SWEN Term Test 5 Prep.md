---
dg-home: false
dg-publish: true
---
Related: #
Contents: [[SWEN221 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 14-06-2023
***

```
1. 
    //MapMulti!
    //Probably my favourite stream operator, due to how versatile it is! It's a map, it's a flatmap, it's a filter!
    
    
    //What does it do?
    //mapMulti() essentually allows us to perform T -> xR operations, where xR is an arbitrary number of R values
    
    
    //Non code example:
    //Say we have the stream [1,2,3], and we want to get all the elements and their doubled values
    //We can represent this goal with the function T -> T, 2*T for T in [T0,T1,T2]
    //If we were to apply this, we would get [T0, T0*2, T1, T1*2, T2, T2*2]
    //In the case of the given stream, that would be [1,2,2,4,3,6]
    
    
    //FlatMap example:
    //syntax reminder
    .flatMap(T -> Stream<R>) ==> Stream<R>
    
    List<Integer> in = List.of(1,2,3);
    List<Integer> out = in.stream()
                          //Stream<T> ==> T -> Stream<R>, which then gets flattened to Stream<R>
                          .flatMap(i -> Stream.of(i, i*2))
                          .toList(); //[1,2,2,4,3,6]
    //As can be seen, we can do this with flatMap, but flatMap is costly
    //flatMap in this case has to:
    // - Build entire new stream objects just to get flattened immediately
    // - Has heavy cost if we want to iteratively build the output (Stream.concat is not cheap!)
    // - Good luck trying to do anything recursive 🤡
    
    
    //Finally, MapMulti;
    //MapMulti follows the signature of
    <R> Stream<R> mapMulti(BiConsumer<? super T,? super Consumer<R>>)
    
    //Ok, that's really gross, let's get rid of the 🅵🅻🆄🅵🅵
    <R> Stream<R> mapMulti(BiConsumer<T, Consumer<R>>)
    
    //And maybe write it in my special lambda syntax
    .<R>mapMulti((T,Consumer<R>) -> {}) ==> Stream<R>
    //🔼 if you're confused, it's pretty much just writing out how you would use the function with lambdas
    
    //Essentually, mapMulti works by:
    // - Giving us a T and a Consumer<R> for each item in the stream
    // - Any items we pump into the Consumer<R> will be piped into the output Stream<R>
    // - We can put as many or as few items into the Consumer<R> and they will all flow into the output :)
    
    //and I outta text
    

2. 
    //MapMulti Part 2! because too many characters >:(
    
    
    //Important note!
    //The <T> in .<T>mapMulti is ᴍᴀɴᴅᴀᴛᴏʀʏ, otherwise you get Stream<Object>
    
    
    //Examples:
    //Simple T -> T example
    List<String> in = List.of("a", "b", "c");
    //I use cons as my usual name for the output consumer
    List<String> out = in.stream()
                         .<String>mapMulti((str, cons) -> cons.accept(str) /*puts str back into the Stream*/)
                         .toList(); //["a, "b", "c"]
    
    //String doubler T -> T, T
    List<String> in = List.of("a", "b", "c");
    List<String> out = in.stream()
                         .<String>mapMulti((str, cons) -> {
                             cons.accept(str);
                             cons.accept(str); //we can use the consumer any number of times :)
                         })
                         .toList(); //["a", "a", "b", "b", "c", "c"]
    
    //Flattening & mapping T[] -> T
    List<List<Tile>> board = Board.getTiles(); //[[Pawn,Rook],[Empty,Jester]]
    List<Tile> tiles = board.stream()
                            //for each List<Tile> tileRow in tiles, add each Tile in tileRow into the output :)
                            .<Tile>mapMulti((tileRow, cons) -> tileRow.forEach(t -> cons.accept(t)))
                            .toList(); //[Pawn,Rook,Empty,Jester], notice that it's flattened?
    
    //EvacuatingTowns
    Map<Town, List<Person>> region = ...; //be creative, I ain't
    int tsunamiHeight = 20;
    List<Person> peopleToEvacuate = region.entrySet() //Set<Entry<Town, List<People>>>
                                          .stream()
                                          //towns within the tsunami flood zone
                                          .filter(entry -> entry.getKey().meanAltitude() < tsunamiHeight)
                                          //collect/consume all the People from each town which is at risk
                                         .<Person>mapMulti((entry, cons) -> entry.getValue().forEach(p -> cons.accept(p)))
                                          .toList();
```

