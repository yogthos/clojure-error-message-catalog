# Working with `deftype`, `defrecord`, and `gen-class`

## imported type but did not require namespace

### Error message

```
java.lang.ClassNotFoundException: link_dataflow.models.maxwell.MaxwellEvent, compiling:(tables.clj:1:1)
```

### Cause

Classes created using `defrecord`, `deftype` and `gen-class` do not get created until the clojure namespace in which they
are defined is loaded using `require` or equivalent. However there's nothing stopping you importing a class without requiring
its namespace, and maybe not seeing this error show up immediately because there's a different set of namespaces loaded
in development compared to production etc.

### Solutions

If you use a class created by `deftype`, `defrecord`, or `gen-class` you should include that namespace in the require list.

```
(ns foo
+  (:require [bar])
   (:import [bar Baz]))
   
(def baz-instance (Baz.))
```
