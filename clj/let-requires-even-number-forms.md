## java.lang.IllegalArgumentException: let requires an even number of forms in binding vector

### Description

The `let` form `(let [a 1 ...])` must always have an even number of forms, which are interpreted as pairs of keys & values.

### Cause 1: Stray println

One very common cause for this error is adding a println partway through a `let` vector, like this:

```clojure
(let [x 1
      y 2
      (println (+ 1 2))]
  (+ 1 2))
```

### Solution 1

If you need a println in the middle of a `let`, a common solution is to assign it to a throwaway variable, conventionally `_`.
