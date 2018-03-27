# Migrating From Guava

Many of the utilities provided by Alloy are intended to take the place of similar functionality in the Guava library. This guide will assist in making necessary changes to convert from Guava to Alloy

## Suppliers

- Guava: com.google.common.base.Suppliers
- Alloy: org.starchartlabs.alloy.core.Suppliers

### Unchanged APIs

- Suppliers.memoize(Supplier)
- Suppliers.memoizeWithExpiration(Supplier, long, TimeUnit)
- Suppliers.synchronizedSupplier(Supplier)

### Updated APIs

- Guava Suppliers.compose(Function, Supplier)
  - In Alloy, this is presented as Suppliers.map(Supplier, Function) to better match the naming of similar operations in the Java language and reflect the chaining of elements that occurs

### Removed APIs

- Suppliers.ofInstance(T)
  - As of Java 8, lambdas allow easier providing of implementations. In place of providing Suppliers.ofInstance(T), instead use the lambda form `() -> T`
- Suppliers.supplierFunction()
  - As of Java 8, a supplier's `get` function can be referenced for use in a lambda. Use `Supplier::get` instead
  
## Preconditions

- Guava: com.google.common.base.Preconditions
- Alloy: org.starchartlabs.alloy.core.Preconditions

### Unchanged APIs

- Preconditions.checkArgument(boolean)
- Preconditions.checkArgument(boolean, Object)

- Preconditions.checkState(boolean)
- Preconditions.checkState(boolean, Object)

### Updated APIs

- Guava Preconditions.checkArgument with message formatting
  - Instead of the large number of Guava methods for built-in message formatting, Alloy separates out the formatting concerns using Java's Supplier via Alloy Preconditions.checkArgument(boolean, Supplier<String>). Alloy may in the future supply a String.format with similar performance to the removed in-built Guava message formatting
  - Affected Guava Preconditions.checkArgument methods:
    - Preconditions.checkArgument(boolean, String, Object...)
    - Preconditions.checkArgument(boolean, String, char)
    - Preconditions.checkArgument(boolean, String, int)
    - Preconditions.checkArgument(boolean, String, long)
    - Preconditions.checkArgument(boolean, String, Object)
    - Preconditions.checkArgument(boolean, String, char, char)
    - Preconditions.checkArgument(boolean, String, char, int)
    - Preconditions.checkArgument(boolean, String, char, long)
    - Preconditions.checkArgument(boolean, String, char, Object)
    - Preconditions.checkArgument(boolean, String, int, char)
    - Preconditions.checkArgument(boolean, String, int, int)
    - Preconditions.checkArgument(boolean, String, int, long)
    - Preconditions.checkArgument(boolean, String, int, Object)
    - Preconditions.checkArgument(boolean, String, long, char)
    - Preconditions.checkArgument(boolean, String, long, int)
    - Preconditions.checkArgument(boolean, String, long, long)
    - Preconditions.checkArgument(boolean, String, long, Object)
    - Preconditions.checkArgument(boolean, String, Object, char)
    - Preconditions.checkArgument(boolean, String, Object, int)
    - Preconditions.checkArgument(boolean, String, Object, long)
    - Preconditions.checkArgument(boolean, String, Object, Object)
    - Preconditions.checkArgument(boolean, String, Object, Object, Object)
    - Preconditions.checkArgument(boolean, String, Object, Object, Object, Object)

- Guava Preconditions.checkState with message formatting
  - Instead of the large number of Guava methods for built-in message formatting, Alloy separates out the formatting concerns using Java's Supplier via Alloy Preconditions.checkState(boolean, Supplier<String>). Alloy may in the future supply a String.format with similar performance to the removed in-built Guava message formatting
  - Affected Guava Preconditions.checkState methods:
    - Preconditions.checkState(boolean, String, Object...)
    - Preconditions.checkState(boolean, String, char)
    - Preconditions.checkState(boolean, String, int)
    - Preconditions.checkState(boolean, String, long)
    - Preconditions.checkState(boolean, String, Object)
    - Preconditions.checkState(boolean, String, char, char)
    - Preconditions.checkState(boolean, String, char, int)
    - Preconditions.checkState(boolean, String, char, long)
    - Preconditions.checkState(boolean, String, char, Object)
    - Preconditions.checkState(boolean, String, int, char)
    - Preconditions.checkState(boolean, String, int, int)
    - Preconditions.checkState(boolean, String, int, long)
    - Preconditions.checkState(boolean, String, int, Object)
    - Preconditions.checkState(boolean, String, long, char)
    - Preconditions.checkState(boolean, String, long, int)
    - Preconditions.checkState(boolean, String, long, long)
    - Preconditions.checkState(boolean, String, long, Object)
    - Preconditions.checkState(boolean, String, Object, char)
    - Preconditions.checkState(boolean, String, Object, int)
    - Preconditions.checkState(boolean, String, Object, long)
    - Preconditions.checkState(boolean, String, Object, Object)
    - Preconditions.checkState(boolean, String, Object, Object, Object)
    - Preconditions.checkState(boolean, String, Object, Object, Object, Object)

### Removed APIs

- Guava Preconditions.checkNotNull
  - As of Java 8, the langauge libraries provide built-in null validation. Use `Objects.requireNonNull()' instead
  - Affected Guava Preconditions.checkNotNull methods:
    - Preconditions.checkNotNull(T)
    - Preconditions.checkNotNull(T, Object)
    - Preconditions.checkNotNull(T, String, Object...)
    - Preconditions.checkNotNull(T, String, char)
    - Preconditions.checkNotNull(T, String, int)
    - Preconditions.checkNotNull(T, String, long)
    - Preconditions.checkNotNull(T, String, Object)
    - Preconditions.checkNotNull(T, String, char, char)
    - Preconditions.checkNotNull(T, String, char, int)
    - Preconditions.checkNotNull(T, String, char, long)
    - Preconditions.checkNotNull(T, String, char, Object)
    - Preconditions.checkNotNull(T, String, int, char)
    - Preconditions.checkNotNull(T, String, int, int)
    - Preconditions.checkNotNull(T, String, int, long)
    - Preconditions.checkNotNull(T, String, int, Object)
    - Preconditions.checkNotNull(T, String, long, char)
    - Preconditions.checkNotNull(T, String, long, int)
    - Preconditions.checkNotNull(T, String, long, long)
    - Preconditions.checkNotNull(T, String, long, Object)
    - Preconditions.checkNotNull(T, String, Object, char)
    - Preconditions.checkNotNull(T, String, Object, int)
    - Preconditions.checkNotNull(T, String, Object, long)
    - Preconditions.checkNotNull(T, String, Object, Object)
    - Preconditions.checkNotNull(T, String, Object, Object, Object)
    - Preconditions.checkNotNull(T, String, Object, Object, Object, Object)

### Unimplemented APIs

Guava Precondtions also provides some element index checking, however there does not appear to be a general use case for these. Issues/Pull requests accompanied by supporting arguments on why these are not overly-specialized are welcome

- Affected Guava Preconditions.checkNotNull methods
  - Preconditions.checkElementIndex(int, int)
  - Preconditions.checkElementIndex(int, int, String)
  - Preconditions.checkPositionIndex(int, int)
  - Preconditions.checkPositionIndex(int, int, String)
  - Preconditions.checkPositionIndexes(int, int, int)