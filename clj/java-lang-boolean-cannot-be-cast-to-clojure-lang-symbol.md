## ClassCastException java.lang.Boolean cannot be cast to clojure.lang.Symbol

### Description

You have attempted to call [`symbol`](https://github.com/clojure/clojure/blob/master/src/jvm/clojure/lang/Symbol.java#L58) on something other than a string or symbol (in this case a boolean). `symbol` ultimately depends on the [`intern` method](https://github.com/clojure/clojure/blob/master/src/jvm/clojure/lang/Symbol.java#L58) of `clojure.lang.Symbol.java`, which will only accept a string argument (symbol arguments to `symbol` are special-cased to return themselves). Note that `symbol` *will* accept arguments that result in non-conformant symbols (eg `(symbol "ab cd")`), but it is highly recommend that you not do so.

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

Don't try to call `symbol` on anything but a string.
