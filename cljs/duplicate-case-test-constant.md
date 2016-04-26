## Creating multiple overloads of a function with the same arity

### Error message

```
Duplicate case test constant '1'
Error: Duplicate case test constant '1'
```

### Cause

The above error happens when you declare two overloads of a function with the same arity.

For example, let's say we have the following function:

```clojure
(defn twice-plus 
  ([x] (twice x 0)) 
  ([x extra] (+ x x extra)))
```

We decide we no longer want to support the second param, but we forget to remove the first overload:

```clojure
(defn twice 
  ([x] (twice x)) 
  ([x] (+ x x)))
```

This will result in the error above.

### Solutions

Delete one of the two duplicate overloads. In our example above, our function would become:

```clojure
(defn twice [x] 
  (+ x x))
```