# Creating records

## Missing protocol

### Error Message

```
java.lang.ClassCastException: clojure.lang.PersistentList cannot be cast to clojure.lang.Symbol
```

### Cause

The above error occurs when we declare a record that includes a protocol function implementation without including the protocol name.

For example, let's say we have the following protocol with a single function:

```clojure
(defprotocol Shape 
  (area [this] "The area of the shape"))
```

We create a new record but forget to include the protocol:

```clojure
(defrecord Rect [x y] 
  (area [this] (* x y)))
```

which yields the above error.


### Solutions

Add the protocol before the functions that implement the protocol:

```clojure
 (defrecord Rect [x y] 
   Shape
   (area [this] (* x y)))
```