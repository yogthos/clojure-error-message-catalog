## ClassCastException java.lang.Boolean cannot be cast to clojure.lang.Symbol

### Cause 1: Forgetting brackets around a require clause

Forgetting brackets around a require clause causes this error. For example:

```clojure
(ns error-sandbox.core
  (:require clojure.walk :as walk))
```

A clue that this is the cause of the exception is seeing `clojure.core/load-lib` in the stack trace.

### Solution 1

The above should instead be:

```clojure
(ns error-sandbox.core
  (:require [clojure.walk :as walk]))
```

### Cause 2: General case

There can of course be other causes, as simple as

```clojure
(symbol true)
```

### Solution 2

Don't try to call `symbol` on anything but a string. `symbol` ultimately depends on the `intern` method of `clojure.lang.Symbol.java`, which will only accept a string argument.
