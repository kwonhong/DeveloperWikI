##### Map & FlatMap Documentation
* [Reference] (www.brunton-spall.co.uk/post/2011/12/02/map-map-and-flatmap-in-scala/)
* It is possible to think of flatMap method as reducing one wrapper.
``` scala
List[List[Int] => List[Int]
List[Some/Option[Int]] => List[Int]
```

##### Disjunction with Scalaz
* [Reference] (http://bytes.codes/2015/04/13/a-skeptics-guide-to-scalaz-gateway-drugs-part-2-options-with-disjunction/)
* Disjunction is similar to Option + No silent error.
``` scala
// Case1: Error handling with Options
val success = Some("Success Case")
val fail = None

for {
one <- success
two <- fail
} yield (one, two) // Silently fails without giving the reason why

// Case2: Error handling with disjunction
import scalaz_.
import Scalaz_.

val success = "Success Case".right
val fail = "Fail Reasoning".left

for {
one <- success
two <- fail
} yield (one, two) // Knows the error message in case of error.
```

##### Scala Monads
* Monad is something that has the following shape.
* Provides a standard interface for composing and sequencing operations on some contained values.
``` scala
trait Monad[A]
 def map[B](f: A => B): Monad[B] // Applies a "regular" function to the contained value
 def flatMap[B](f: A => Monad[B]): Monad[B] // Applies a "monadic" function to the contained value
}
```

##### Scala Objects
* [Reference] (https://www.safaribooksonline.com/library/view/learning-scala/9781449368814/ch09.html)
* A type of class that can have no more than one instance, known in object-oriented design as a singleton.
* Similar to "static" or "global" members + decoupled from instantiable classes.
``` scala
class Multiplier(val x: Int) { 
 def product(y: Int) = x * y
}

object Multiplier { 
 // Having apply methods allows to call the method like Multipler(3)
 def apply(x: Int) = new Multipler(x) 
}
```

##### Scala Case Classes
* [Reference] (https://www.safaribooksonline.com/library/view/learning-scala/9781449368814/ch09.html)
* An instantiable class that includes several automatically generated methods. 
* Great for data transfer objects, the kind of classes that are mainly used for storing data, given the data-based methods that are generated.

##### Scala Trait Classes
* A kind of class that enables muliple inheritance. Clas
