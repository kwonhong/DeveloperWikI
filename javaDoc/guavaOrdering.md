## Guava - Ordering Class

Ordering is Guava's special Comparator instance which can be used to build complex comparators. This Ordering instance can be applied to any collections of objects. In addition to Comparator, Ordering class provides chaining methods to tweak and enhance existing comparators.

#### 1. Initializing Optional Object
* Reference: https://code.google.com/p/guava-libraries/wiki/OrderingExplained
``` java
        // Creating Ordering Object from existing Comparator
        Comparator<String> comparator = new Comparator<String>() {
            @Override
            public int compare(String o1, String o2) {
                return o1.compareTo(o2);
            }
        };
        Ordering.from(comparator);

        // Creating the custom Ordering Object.
        Ordering<String> byLengthOrdering = new Ordering<String>() {
            public int compare(String left, String right) {
                return Ints.compare(left.length(), right.length());
            }
        };

```

#### 2. Sorting collections of object
* Reference: https://code.google.com/p/guava-libraries/wiki/OrderingExplained 
``` java
        // Sorting in ascending order.
        Collections.sort(list, integerOrdering);

        // Sorting in ascending order - by using static method "natural"
        Collections.sort(list, Ordering.natural());

        // Sorting in ascending order by comparing its string value
        Collections.sort(list, Ordering.usingToString());
```

#### 3. Tweaking Ordering object
* Reference: https://code.google.com/p/guava-libraries/wiki/OrderingExplained 
``` java
        // Reversing the comparator
        Ordering<Integer> descendingOrder = integerOrdering.reverse();

        // Putting all the Null Value first or last
        Ordering<Integer> nullFirstOrder =  integerOrdering.nullsFirst();
        Ordering<Integer> nullLastOrder = integerOrdering.nullsLast();

        // Complex version of tweaking ordering comparison.
        Ordering<Integer> ordering = Ordering.natural().nullsFirst().onResultOf(new Function<Integer, String>() {
            public String apply(Integer integer) {
                return integer.toString();
            }
        });
```

#### 4. Compounding Ordering - ordering "tie" values
* Reference: http://docs.guava-libraries.googlecode.com/git-history/release/javadoc/com/google/common/collect/Ordering.html#compound(java.util.Comparator)
* Compounded ordering instances only take place when **original ordering results to tie**.

``` java
        // Compounding ordering - when first ordering "tie" - use compound ordering to determine order.
        Ordering<Integer> compoundedOrdering = nullFirstOrder.compound(descendingOrder);
        Ordering<Integer> multipleCompoundedOrdering = nullFirstOrder.compound(Arrays.asList(descendingOrder, nullLastOrder));
```

#### 5. Other cool Ordering functions
* Reference: http://docs.guava-libraries.googlecode.com/git-history/release/javadoc/com/google/common/collect/Ordering.html
``` java
        // Returns a mutable list containing elements sorted by this ordering.
        List<Integer> mutableCopyList = ordering.sortedCopy(list);
        List<Integer> immutableCopyList = ordering.immutableSortedCopy(list);

        // Getting max & min from list using ordering
        int maxNum = ordering.max(list);
        int minNum = ordering.min(list);

        // Returns the k greatest/least elements of the given iterable according to this ordering.
        // Not stable - when multiple equal value exists, uncertain which one will get returned.
        List<Integer> kGreatestList = ordering.greatestOf(list, 2);
        List<Integer> kLeastList = ordering.leastOf(list, 2);

        // Checking if the list is already sorted according to ordering
        boolean isOrdered = ordering.isOrdered(list)
````
