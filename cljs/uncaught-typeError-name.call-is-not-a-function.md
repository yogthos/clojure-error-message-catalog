## Uncaught TypeError: name.call is not a function

### Error message

```
Uncaught TypeError: name.call is not a function
```

### Cause: name function is being shadowed

This error happens when you shadow cljs.core's `name` function.  The same error
would occur when you shadow any core function then try to call it.

ClojureScript does not warn when you shadow a core function inside a `let` form
or any other closure.

For example:

```clojure
(defn display-name [{:keys [person/name]}]
  (str (name :person/name) ": " name))
```

Attempting to use `name` on the `:person/name` keyword will throw `Uncaught
TypeError: name.call is not a function` because `name` was redefined in the
`display-name` function

### Solutions

Don't shadow core functions. The above example could be re-written as:

```clojure
(defn display-name [{person-name :person/name}]
  (str (name :person/name) ": " person-name)))
```
