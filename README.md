# Clojure Error Message Catalog

a catalog of common Clojure errors and their meanings

## We need your errors!

This catalog is community driven, hence _your_ contribution to this is invaluable.

It is very simple to contribute / share errors / exceptions, causes and possible solutions.
There are 3 main sections of the catalog:

#### 1. Clojure errors

* Live under [clj](clj/) 
* Here we collect all Clojure _core_ errors: i.e. errors that are raised from/by Clojure itself.

#### 2. ClojureScript errors

* Live under [cljs](cljs/) 
* Here we collect all ClojureScript _core_ errors: i.e. errors that are raised from/by ClojureScript itself.

#### 3. Library errors

* Live under [lib](lib/)
* Here we collect all errors that are raised from/by any Clojure / ClojureScript _library_ (Ring, Compojure, your library, etc..)

### How to submit a new error

In order to contribute, please check that the error is not already in the catalog, if it is and you need to add / change anything, just send a pull request.

#### Error file name

Errors are subitted as markdown files (i.e. `.md`). The file name would be very close to the `cause`.

For example, let's take an exception:

```clojure
#object[mount.core.DerefableState 0x52691944 {:status :failed, :val #error {
:cause "mount.core.DerefableState cannot be cast to clojure.lang.IFn"
```

So something like `derefablestate-cannot-be-cast-to-ifn.md` would be a great, descriptive file name for this error.

#### What is in the error file?

Would be really helpfult to have all three in the error file:

* Error message
* Cause
* Solution(s)

For example [derefablestate-cannot-be-cast-to-ifn.md](lib/mount/derefablestate-cannot-be-cast-to-ifn.md)

#### Where to place the file?

Since there 3 main sections ([clj](clj/) / [cljs](cljs/) / [lib](/lib)) place it under the section that matches the nature of the error.

For example the above error ("mount.core.DerefableState cannot be cast to clojure.lang.IFn") would live under [lib/mount/](lib/mount/)
since it is caused by the `library` that is called `mount`.

In case the error is Clojure core related, place is under [clj](clj/).

ClojureScript _core_ related errors would go under [cljs](cljs/)

## License

Copyright © 2016 Clojure Community

Distributed under the Eclipse Public License either version 1.0 or (at your option) any later version.
