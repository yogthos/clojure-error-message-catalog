# Working with higher order functions

## Wrong argument order for iterators

### Error Message

```
java.lang.IllegalArgumentException: Don't know how to create ISeq from: ...
```

### Cause

The above error indicates that we're trying to iterate over something that does not implement the `ISeq` interface.
This error is often caused by passing the arguments in the wrong order to higher order functions such as
`map`, `filter`, and `reduce`, e.g:

```clojure
(map [1 2 3] inc)
```

### Solutions

Check that the function is passed the arguments in the correct order:

```clojure
(map inc [1 2 3])
```
