# [4clojure-solutions](http://www.4clojure.com/)
## some solutions to 4clojure kata

### [problem 30](https://4clojure.com/problem/30)

Write a function which removes consecutive duplicates from a sequence.

[partition](https://clojuredocs.org/clojure.core/partition)

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

---

### [problem 32](https://4clojure.com/problem/32)

Write a function which duplicates each element of a sequence.

[interleave](https://clojuredocs.org/clojure.core/interleave)

~~~clojure
(fn [x] (interleave x x))
~~~

_Notes_

It is possible to use a (flatten (map )) function to solve half the problem but only if the output requires a flat sequence of values.

~~~clojure
(fn [x] (flatten (map #(list % %) x)))
~~~
