## Guava - Optional Classes

An **immutable object** that may contain a non-null reference to another object. Each instance of this type either contains a **non-null reference**, or **contains nothing**.

1. It is never said to "contain null". It is either empty or present.
2. To wrap nullable references for storage in a collection that does not support null

#### 1. Initializing Optional Object
* Reference: http://docs.guava-libraries.googlecode.com/git/javadoc/com/google/common/base/Optional.html#or(com.google.common.base.Optional)
``` java
        String firstString = null;
        String secondString = "Optional String";

        // "fromNullable" static methods allow to pass in null object - No NullPointerException.
        Optional<String> firstOptionalString1 = Optional.fromNullable(firstString); // Empty Optional
        Optional<String> secondOptionalString1 = Optional.fromNullable(secondString); // Present Optional

        // "of" static method does not allow null reference.
        Optional<String> firstOptionalString2 = Optional.of(firstString); // NullPointerException
        Optional<String> secondOptionalString2 = Optional.of(secondString); // Present Option - Same as using "fromNullable"
        
        // Making an absent Optional
        Optional<String> absentOptional = Optional.absent();

```

#### 2. Checking Optional Object State
* Reference: http://docs.guava-libraries.googlecode.com/git/javadoc/com/google/common/base/Optional.html#isPresent()
* **NullPointerCheck is not required** with Optional object. Simply use "isPresent" -- Cleaner & Simpler
``` java
        // Return False since it doesn't contain non-null object
        firstOptionalString1.isPresent();
        absentOptional.isPresent();

        // Return True since it contains not-null object
        secondOptionalString1.isPresent();
```

#### 3. Getting referenced object inside Object
* Reference: http://docs.guava-libraries.googlecode.com/git/javadoc/com/google/common/base/Optional.html#get()
``` java
        // Throws IllegalStateException since Optional object is empty
        firstOptionalString1.get();

        // Returns the contained instance
        secondOptionalString1.get();
```
#### Downloading Guava Library
##### Intellij 
1. insert this statement ``` import com.google.common.base.Optional; ```
2. Alt + Enter to find Jar online.

##### Other Platform
1. Download guava library from here - https://code.google.com/p/guava-libraries/
2. Import this jar into project 
