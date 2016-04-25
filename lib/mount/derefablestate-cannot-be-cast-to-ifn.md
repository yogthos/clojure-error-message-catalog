## Attempting to use a component that hasn't been started

### Error message

```
#object[mount.core.DerefableState 0x52691944 {:status :failed, :val #error { 
:cause "mount.core.DerefableState cannot be cast to clojure.lang.IFn"
```

### Cause

The above error happens when you try to access a variable defined using `mount.core/defstate` before the `:start` function has been called.

There are [many ways to start states](https://github.com/tolitius/mount#composing-states) with Mount,
but when the app is started via `(mount/start)` Mount will only start states Clojure Compiler saw/compiled: i.e. states in namespaces
that are not referenced won't be started.

For example, let's say we have the following namespace:

```clojure
(ns guestbook.db.core
  (:require [conman.core :as conman]
            [mount.core :refer [defstate]]
            [guestbook.config :refer [env]]))

(defn- connect-to-db [{:keys [database-url]}]
  (conman/connect! {:datasource
                     (doto (org.sqlite.SQLiteDataSource.)
                           (.setUrl database-url))}))

(defstate ^:dynamic *db*
          :start (connect-to-db env)
          :stop (conman/disconnect! *db*))
```

The `:start` function has to be run to bind a new databse connection to the `*db*`.
When we try to access `*db*` _before_ `:start` has been run, the above exception will occur.

### Solutions

* Reference the namespace in a different namespace in the project, e.g:

```clojure
(ns guestbook.routest.services
  (:require [guestbook.db.core :as db]
            ...))
```

Depends on where `(mount/start)` is called, if it knows `guestbook.routest.services`,
it will also know (and hence will start) `guestbook.db.core/*db*`.

* manually load the namespace and start the state in the REPL:
 
```clojure
(require '[guestbook.db.core :as db])
(mount.core/start db/*db*)
```