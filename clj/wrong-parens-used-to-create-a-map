### Working with data literals

### Error Message
```
IllegalArgumentException Wrong number of args passed to keyword: :bread
```
### Cause

Using parens instead of curly braces to create a map literal will cause the above error, e.g:

```clojure
(:first-name "Bob", :last-name "Bobberton")
```
What's happening here is that `:first-name` is being called like a function and the rest of the items in the list are treated as its arguments.
Keywords implement the IFn protocol and can be called like functions. The keyword expects a map and an optional default value as its arguments:

```clojure
(:first-name {:first-name "Bob"})

(:first-name {} "Bob")
```

When the first argument to a keyword is not a map, then the result will be `nil`.
This leads to a related error where trying to create a map with a single key/value pair will return a `nil`:

```clojure
(:first-name "Bob") ;=> nil
```

### Solution

Make sure you're using the `{...}` parens when creating the map:

```clojure
{:first-name "Bob", :last-name "Bobberton"}
```


