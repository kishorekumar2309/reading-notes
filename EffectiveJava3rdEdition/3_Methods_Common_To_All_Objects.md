## 3. Methods Common to All Objects

equals, hashCode, toString, clone and finalize - non final methods are explicit *general contracts* because they are designed to be overridden

### **ITEM 10: OBEY THE GENERAL CONTRACT WHEN OVERRIDING** *EQUALS*

Avoid overriding the equals method under following conditions:

- **Each instance of the class is inherently unique**
- **There is no need for the class to provide a “logical equality” test**
- **A superclass has already overridden** `equals`, **and the superclass behavior is appropriate for this class**
- **The class is private or package-private, and you are certain that its** `equals` **method will never be invoked**

Appropriate to override under following conditions:

- when a class has a notion of *logical equality* that differs from mere object identity and a superclass has not already overridden `equals`
- in case for *value classes* - a value class is simply a class that represents a value, such as `Integer` or `String`
- The `equals` method implements an *equivalence relation*
  - *Reflexive*: For any non-null reference value `x`, `x.equals(x)` must return `true`.
  - *Symmetric*: For any non-null reference values `x` and `y`, `x.equals(y)` must return `true` if and only if `y.equals(x)` returns `true`.
  - *Transitive*: For any non-null reference values `x`, `y`, `z`, if `x.equals(y)` returns `true` and `y.equals(z)` returns `true`, then `x.equals(z)` must return `true`.
  - *Consistent*: For any non-null reference values `x` and `y`, multiple invocations of `x.equals(y)` must consistently return `true` or consistently return `false`, provided no information used in `equals` comparisons is modified.
  - For any non-null reference value `x`, `x.equals(null)` must return `false`.
- recipe for a high-quality `equals` method:
  1. **Use the** `==` **operator to check if the argument is a reference to this object.** If so, return `true`
  2. **Use the** `instanceof` **operator to check if the argument has the correct type.** If not, return `false`
  3. **Cast the argument to the correct type**
  4. **For each “significant” field in the class, check if that field of the argument matches the corresponding field of this object**
- caveats:
  - **Always override** `hashCode` **when you override** `equals`
  - **Don’t try to be too clever.** If you simply test fields for equality, it’s not hard to adhere to the `equals` contract
  - **Don’t substitute another type for** `Object` **in the** `equals` **declaration**



### **ITEM 11: ALWAYS OVERRIDE** `HASHCODE` **WHEN YOU OVERRIDE** `EQUALS`

- When the `hashCode` method is invoked on an object repeatedly during an execution of an application, it must consistently return the same value, provided no information used in `equals` comparisons is modified
- If two objects are equal according to the `equals(Object)` method, then calling `hashCode` on the two objects must produce the same integer result
- If two objects are unequal according to the `equals(Object)` method, it is *not* required that calling `hashCode` on each of the objects must produce distinct results
- **Do not be tempted to exclude significant fields from the hash code computation to improve performance**
- **Don’t provide a detailed specification for the value returned by** `hashCode`**, so clients can’t reasonably depend on it; this gives you the flexibility to change it**



### **ITEM 12: ALWAYS OVERRIDE** `TOSTRING`

- **providing a good** `toString` **implementation makes your class much more pleasant to use and makes systems using the class easier to debug**
- **the** `toString` **method should return** ***all*** **of the interesting information contained in the object**
- **Whether or not you decide to specify the format, you should clearly document your intentions**
- **provide programmatic access to the information contained in the value returned by** `toString`
- Don't override toString() in Static utility classes or enums







