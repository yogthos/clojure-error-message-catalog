## java.lang.AssertionError: No fields vector given.

### Description

You have failed to supply a fields vector to a defrecord.

### Cause:

There is only one cause of this error: you've forgotten the vector of fields name that should follow the defrecord name, in a defrecord which implements at least one protocol:

```clojure
(defrecord a-record
    SomeProtocol
  (p-fn1 [arg])
  (p-fn2 [arg]))
```

### Solution:

Add the field vector.

```clojure
(defrecord a-record [field1 field2]
    SomeProtocol
  (p-fn1 [arg])
  (p-fn2 [arg]))
```
