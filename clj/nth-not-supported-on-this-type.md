# Destructuring

## Left and right sides have incompatible types

### Error Message

```
UnsupportedOperationException nth not supported on this type: ...
```

### Cause

The above error indicates that we're trying to destructure some value as a vector, but that value can't be broken into sequential parts.

For instance, we'll see this error if we destructure the number 5:

```clojure
(let [[x1 x2] 5] 
  x1)
```

### Solutions

Ensure that the right-hand side has a sequence of elements:

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
