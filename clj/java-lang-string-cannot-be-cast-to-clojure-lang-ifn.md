# Working with lists

## Missing quote

### Error Message

```
ClassCastException java.lang.String cannot be cast to clojure.lang.IFn
```

### Cause

The above error can occur when we try to create a list literal without the quote:

```clojure
("a" "b" "c")
```

### Solutions

Either add the initial single quote:

```clojure
'("a" "b" "c")
```

or use the `list` function:

```clojure
(list "a" "b" "c")
```