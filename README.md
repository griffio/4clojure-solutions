# [4clojure-solutions](http://www.4clojure.com/)
## some solutions to 4clojure interactive problems

### [problem 26](http://www.4clojure.com/problem/26)

Write a function which returns the first X fibonacci numbers.

Uses a Math formula that runs in constant time and iterated over a sequence starting with 1

~~~clojure
(fn [n] (map #(let [sq5 (Math/pow 5 0.5M), rsq5 (/ 1 sq5)]
                        (Math/round (* rsq5 (- (Math/pow (/ (+ 1 sq5) 2) %)
                        (Math/pow (/ (- 1 sq5) 2) %)))))
                        (take n (iterate inc 1) ) ) ) 
~~~

_Notes_

Idiomatic lazy sequence of all Fibonacci numbers starting with 1.

~~~clojure
(fn [n] (take n (map first (iterate (fn [[a b]] [b (+ a b)]) [1 1]))))
~~~

### [problem 30](https://4clojure.com/problem/30)

Write a function which removes consecutive duplicates from a sequence.

[partition-by docs](https://clojuredocs.org/clojure.core/partition-by)

~~~clojure
#(map first (partition-by identity %))
~~~

_Notes_

~~~clojure 
(partition-by identity "Leerroyy") 
((\L) (\e \e) (\r \r) (\o) (\y \y))

(map first(partition-by identity "Leerroyy"))
(\L \e \r \o \y)
~~~

### [problem 32](https://4clojure.com/problem/32)

Write a function which duplicates each element of a sequence.

[interleave docs](https://clojuredocs.org/clojure.core/interleave)

~~~clojure
(fn [x] (interleave x x))
~~~

_Notes_

It is possible to use a (flatten (map )) function to solve half the problem but only if the output requires a flat sequence of values.

~~~clojure
(fn [x] (flatten (map #(list % %) x)))
~~~

### [problem 33](https://4clojure.com/problem/33)

Write a function which replicates each element of a sequence a variable number of times.

[iterate docs](https://clojuredocs.org/clojure.core/iterate)

[mapcat docs](https://clojuredocs.org/clojure.core/mapcat)

Using iterate

~~~clojure
(fn [col n] (mapcat #(take n (iterate identity %)) col))
~~~

_Notes_

mapcat will create the sequence as a single list, where as map will create a new list for each iteration.

~~~clojure
(([1 2] [1 2]) ([3 4] [3 4]))
~~~

alternative solution

~~~clojure
(fn [col n] (mapcat (partial repeat n) col))
~~~

### [problem 41](https://4clojure.com/problem41)

Write a function which drops every Nth item from a sequence.

[partition-all docs](https://clojuredocs.org/clojure.core/partition-all)

~~~clojure
(fn [coll n] (flatten (partition-all (dec n) n coll)))
~~~

_Notes_

Partition the collection into (n -1) sized collections stepping over n elements.

~~~clojure
(partition-all (dec 3) 3 [1 2 3 4 5 6 7 8])
((1 2) (4 5) (7 8))
~~~
