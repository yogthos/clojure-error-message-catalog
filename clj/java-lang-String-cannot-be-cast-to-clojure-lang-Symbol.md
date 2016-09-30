## java.lang.ClassCastException java.lang.String cannot be cast to clojure.lang.Symbol

### Description

You can run whole project perfectly with `lein run`, and after a while, when you attempted to uberjar or call nrepl from it. a bunch of complicated error raised. compiling some file in magic path. Seems like non-relationship with your code.

```log
Exception in thread "main" java.lang.ClassCastException: java.lang.String cannot be cast to clojure.lang.Symbol, compiling:(/private/var/folders/nl/_g09mk616xb1hwl5lntzthn40000gp/T/form-init7159807757487430777.clj:1:125)
```

It is highly recommended to do really small changes of `project.clj`.

### Cause: defproject main shuold be a symbol

Go back and check your project.clj

```clojure
:main "demo.core"
```

### solution

change the :main section to symbol

```clojure
:main demo.core
```
