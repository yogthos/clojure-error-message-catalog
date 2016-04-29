# nth errors

## nth errors caused by destructuring

### Error Message

```
UnsupportedOperationException nth not supported on this type: ...
```

### Cause

The above error indicates that Clojure is calling `nth` on a value that does not implement `nth` e.g. a keyword.

Generally this error is seen when we destructure something that is not a collection, e.g. if we have supplied the wrong arguments 
to the function:

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

This error may also be seen directly by calling `nth` directly on something that does not support `nth`:

``` clojure
(nth :keyword 0)
```

### Solutions

Supply a sequence or string to the function or binding:

```clojure
(let [[x y] '(1 2 3)]
  x)
;; 1
(let [[x y] [1 2 3]]
  x)
;; 1
(let [[x y] "abc"]
  x)
;; \a
```