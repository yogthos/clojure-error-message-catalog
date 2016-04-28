## Using single quotes

### Error Message

```
CompilerException java.lang.RuntimeException: Unable to resolve symbol: World' in this context,
```

### Cause

The above error is caused by trying to use single-quoted strings:

```clojure
(print 'Hello World')
```

### Solutions

Use double-quoted strings:

```clojure
(print "Hello World")
```
