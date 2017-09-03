# Working with -> and ->> threading macros

## threading macro is inserting an argument at the wrong position

### Error message

```
IllegalArgumentException Don't know how to create ISeq from: example.core$eval34632$fn__34633 clojure.lang.RT.seqFrom
```

### Cause

When you see a message similar to the one above when using a threading macro, it is likely that the argument is being
inserted in the wrong position. For example, you maybe have something like the following where the macro inserts the
argument in the first position but the functions expect it in the last position:

```clojure
(-> (range 10) (filter even?))
```

### Solutions

Use the `->>` macro to insert the argument in the correct position:

```clojure
(->> (range 10) (filter even?))
```

In cases where functions expect arguments in different positions, use the `as->` macro:

```clojure
(as-> (range 10) % (filter even? %) (apply str %) (clojure.string/includes? % "24"))
```
