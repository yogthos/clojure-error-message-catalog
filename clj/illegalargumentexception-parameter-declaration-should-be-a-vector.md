## IllegalArgumentException Parameter declaration "+" should be a vector 

### Description

Function declaration is missing arguments vector.

### Cause

When you declare a new function with documentation strings, it is easy
to forget argument vector, especially if function documentation isn't
small. Here is an example:

```clojure
(defn my-static-adder
  "This is my-static-adder function which will simply add
two built-in numbers. Nothing spectacular, just to demonstrate
how easy is to miss argument vector."  
  (+ 1 2))
```

After you evaluate it, you can get this:

```log
IllegalArgumentException Parameter declaration "+" should be a vector  clojure.core/assert-valid-fdecl (core.clj:7196)
```

### Solution

Add argument vector.

```clojure
(defn my-static-adder
  "This is my-static-adder function which will simply add
two built-in numbers. Nothing spectacular, just to demonstrate
how easy is to miss argument vector."  
  []
  (+ 1 2))
```
