15th May 2019

A lil collection of notes while learning Java streams

## Using streams to count duplicates in lists
Using `Collectors.groupingBy()` method you can count duplicates like so:
```
Map<Integer, Long> scoreboard = Arrays.stream(dice)
        .sorted()
        .boxed()
        .collect(Collectors.groupingBy(Function.identity(), Collectors.counting()));
```

Finding this approach allowed me to remove my manual approach:

```
HashMap<Integer, Integer> scoreboard = new HashMap<>();
scores.forEach(value -> {
    if (scoreboard.get(value) == null) {
        scoreboard.put(value, 1);
    } else {
        int amount = scoreboard.get(value);
        amount = amount + 1;
        scoreboard.put(value, amount);
    }
});
```
###### Thoughts
* removed 10 lines of code
* adding more methods to a stream is always satisfying

* I feel I wouldn't have known what `Collectors.groupingBy()` did without looking it up
* Second approach is more familiar and simple but would require me to mentally step through to know what it did

[Reference](https://stackoverflow.com/questions/44367203/how-to-count-duplicate-elements-in-arraylist)
