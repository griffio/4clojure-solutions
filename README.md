# 4clojure-solutions
### some solutions to 4clojure kata

[problem 32](https://4clojure.com/problem/32)

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
