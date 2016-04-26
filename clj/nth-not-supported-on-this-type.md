# nth errors

## nth errors caused by destructuring

### Error Message

```
UnsupportedOperationException nth not supported on this type: ...
```

### Cause

The above error indicates that clojure is calling nth on something that clojure does not implement nth for e.g. a keyword.
Generally this error is seen when we destructure something that is not a collection, e.g. if we have supplied the wrong arguments 
to the function e.g.

```clojure
(defn destructure-fn [[a b] num] 
      a)

(destructure-fn 3 [1 2]) ; wrong argument order
```

OR 

```clojure
(let [[a b] :a-keyword] 
      a)
```

This error may also be seen directly by calling nth directly on something that does not support nth:

``` clojure
(nth :keyword 0)
```

### Solutions

Supply the correct destructurable type to the function or binding.


```clojure
(let [[a b] [1 2]] 
      a)
```
