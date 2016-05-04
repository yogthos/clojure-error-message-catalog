# Clojure Error Message Catalog

a catalog of common Clojure errors and their meanings

## What is it?

We are experimenting with starting a community driven catalog of common errors. The main categories will be [Clojure](clj/), [ClojureScript](cljs/) and [libraries](/lib).

The idea is that people can submit an issue with a particular error, or make a pull request with the error, description and hopefuly one or two solutions to resolve it.

Eventually, the plan would be to create a site where you could paste errors and search for them that way, but it would make sense to start with a GitHub repo to see if there's interest. Hopefully, this will also help identify the most common errors people have trouble with and make error reporting better in Clojure itself.

This project was inspired by the way [Elm does this](https://github.com/elm-lang/error-message-catalog), where they have a repo for this purpose, and then provide custom compiler errors for these cases.

## We need your errors!

This catalog is community driven, hence _your_ contribution to this is _invaluable_.

It is very simple to contribute / share errors, exceptions, causes and possible solutions.
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

## How to submit a new error

In order to contribute, please check that the error is not already in the catalog.
If it is and you need to add / change anything, just send a pull request.

### Error file name

Errors are submitted as markdown files (i.e. `.md`). The file name would be very close to the exception.

For example, let's take an exception:

```clojure
#object[mount.core.DerefableState 0x52691944 {:status :failed, :val #error {
:cause "mount.core.DerefableState cannot be cast to clojure.lang.IFn"
```

So something like `derefablestate-cannot-be-cast-to-ifn.md` would be a great, descriptive file name for this error.

### Error file format

Would be really helpful to have all three in the error file:

* Exception
* Description of the exception
* Common cause(s)
* Solutions

Share a file that describes these sections in a  [markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) format:

```
## Title: Exception message
### Description: general description of the exception
### Cause 1: Cause title
### Solution 1
...
### Cause n: cause n title
### Solution n
```

#### Why the "format"?

Following this format / guideline allows this error catalog to be processed into a format that can be also _readable by programs_ (i.e. not just us, humans). Which enables great things like [contextual search] (https://en.wikipedia.org/wiki/Contextual_searching), IDE/tooling integration for suggestions, etc.

Check out [this error file](lib/clj/java-lang-boolean-cannot-be-cast-to-clojure-lang-symbol.md) to visualize the required format.

### Where to place the file?

Since there are 3 main sections ([clj](clj/) / [cljs](cljs/) / [lib](/lib)) place it under the section that matches the nature of the error.

For example the error (`"mount.core.DerefableState cannot be cast to clojure.lang.IFn"`) would live under [lib/mount/](lib/mount/)
since it is caused by the `library` that is called `mount`.

In case the error is Clojure _core_ related, place is under [clj](clj/).

ClojureScript _core_ related errors would go under [cljs](cljs/).

-

So the steps to contribute are:

* [fork](https://help.github.com/articles/fork-a-repo/) this repo
* Once the error file is ready to be contributed, just [send a pull request](https://help.github.com/articles/creating-a-pull-request/) to the repo.

In case you have any questions, suggestions, please let us know via [opening an issue](https://github.com/yogthos/clojure-error-message-catalog/issues) or
pinging us on [clojurian slack](http://clojurians.net/) (@yogthos, @tolitius).

## License

Copyright © 2016 Clojure Community

Distributed under the Eclipse Public License either version 1.0 or (at your option) any later version.
