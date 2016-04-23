# clojure-error-message-catalog
a catalog of common Clojure errors and their meanings

## Attempting to use a component that hasn't been started

### Error message:

```
#object[mount.core.DerefableState 0x52691944 {:status :failed, :val #error { 
:cause "mount.core.DerefableState cannot be cast to clojure.lang.IFn"
```

### Cause:

The above error happens when you try to access a variable defined using `mount.core/defstate`
before the `:start` hook has been called. Mount will not automatically start states in namespaces
that are not referenced anywhere in the project.

For example, let's say we have the following namespace:

```clojure
(ns guestbook.db.core
  (:require
    [conman.core :as conman]
    [mount.core :refer [defstate]]
    [guestbook.config :refer [env]]))

(defstate ^:dynamic *db*
          :start (conman/connect!
                   {:datasource
                    (doto (org.sqlite.SQLiteDataSource.)
                          (.setUrl (env :database-url)))})
          :stop (conman/disconnect! *db*))
```

The `:start` hook has to be run before the `*db*` var is populated with the connection.
When we try to access the var before `:start` has been run, the above exception will occur.

### Solutions:

* Reference the namespace in a different namespace in the project, e.g:

```clojure
(ns guestbook.routest.services
  (:require [guestbook.db.core :as db]
            ...))
```

* manually load the namespace and start the state in the REPL:
 
```clojure
(require '[guestbook.db.core :as db])
(mount.core/start db/*db*)
```
