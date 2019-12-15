# scala-learning
Scala Practice Programing


#### Primitive Data Type
Data Type  Definition

Boolean    true or false

Byte       8-bit signed two's complement integer (-2^7 to 2^7-1, inclusive)
           -128 to 127

Short      16-bit signed two's complement integer (-2^15 to 2^15-1, inclusive)
           32,768 to 32,767

Int        32-bit two's complement integer (-2^31 to 2^31-1, inclusive)
           2,147,483,648 to 2,147,483,647

Long       64-bit two's complement integer (-2^63 to 2^63-1, inclusive)
           -9,223,372,036,854,775,808 to +9,223,372,036,854,775,807

Float      32-bit IEEE 754 single-precision float
           1.40129846432481707e-45 to 3.40282346638528860e+38 (positive or negative)

Double     64-bit IEEE 754 double-precision float
           4.94065645841246544e-324d to 1.79769313486231570e+308d (positive or negative)

Char       16-bit unsigned Unicode character (0 to 2^16-1, inclusive)
           0 to 65,535

String     a sequence of Chars 
#### First Program
```scala
object ScalaLearning{
  def main(args: Array[String]){
    println("Himanshu Kesarvani")
  }
}
 ```


#### Working on while loop

```scala
object ScalaLearning{
  def main(args: Array[String]){
    var i = 0
    while(i < 10){
      println(i)
      i+=1
    }
  }
}
```


#### for loop for printing numbers
```scala
object ScalaLearning{
  def main(args: Array[String]){
    var i = 0
    for(i <- 1 to 10)
      println(i)
  }
}
```

####  Iterating each letter in string
```scala
object ScalaLearning{
  def main(args: Array[String]){
    val randLetters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"

    for(i <- 0 until randLetters.length)
      println(randLetters(i))
  }
}
```

#### <- is called generator More to read

####  Iterating List item
```scala
object ScalaLearning{
  def main(args: Array[String]){

    var list = List(1,2,3,4,5)

    for(i <- list)
      println("List item " + i)
  }
}
```

#### Comprehension in the Scala
```scala
object ScalaLearning{
  def main(args: Array[String]){

    var evenList = for { i <- 1 to 20} yield i
    println(evenList)
  }
}
```

#### Generating even numbers using comprehension and it returns a Vector
```scala
object ScalaLearning{
  def main(args: Array[String]){

    var evenList = for { i <- 1 to 20; if(i%2 == 0)} yield i
    println(evenList)
  }
}
```

#### Printing the list generated by comprehension

```scala
object ScalaLearning{
  def main(args: Array[String]){

    var evenList = for { i <- 1 to 20; if(i%2==0)} yield i
    for(j <- evenList)
      println(j)
  }
}
```

#### Iterate list one after another nested iteration

```scala
object ScalaLearning{
  def main(args: Array[String]){

    for(i <- 0 to 5; j <- 6 to 10){
      println(i)
      println(j)
    }
  }
}
```


#### Importing libraries and console input
import scala.io.StdIn.{readLine, readInt}
import scala.math._
import scala.collection.mutable.ArrayBuffer
import java.io.PrintWriter
import scala.io.Source
```scala
object ScalaLearning{
  def main(args: Array[String]){
    
    var numberGuess = 0

    do {
      print("Guess a number")
      numberGuess = readLine.toInt
    } while(numberGuess != 15) 
      printf("You guessed the secret number %d\n", 15)

  }
}
```

#### Printing string, float and Interger with println
```scala
object ScalaLearning{
  def main(args: Array[String]){

   val name = "Himanshu Kesarvani"
   val age = 39
   val weight = 175.5

   println(s"Hello $name") 

   println(f"I am ${age + 1} and weight $weight%.2f") 
  // %c for character
  // %d for integer
  // %f for floating
  }
}
```

#### Functions
```scala
object ScalaLearning{
  def main(args: Array[String]){

  def getSum(num1: Int = 1, num2: Int = 1): Int = {
    return num1 + num2
  }    


  println("5 + 4 = " + getSum(5,4))
  }
}
```

#### Important => Scala Return last line as output of function

#### Unknown number of parameters in the function
```scala
object ScalaLearning{
  def main(args: Array[String]){
    
    def getSum(args: Int*): Int = {
      var sum: Int = 0
      for(num <- args){
        sum += num
      }
      sum
    }
    println("Get Sum " + getSum(1,3,5,6,9))
  }
}
```

#### Recursion in the function
```scala
object ScalaLearning{
  def main(args: Array[String]){

    def factorial(num: BigInt) : BigInt = {
      if(num <= 1)
        1
      else
        num * factorial(num - 1)
    }  

    println("Factorial of 4 = " + factorial(4))
  }
}
```

#### Using of Array and ArrayBuffer(When we have variable number of data)
```scala
object ScalaLearning{
  def main(args: Array[String]){

    val favNums = new Array[Int] (20)

    val friends = Array("Bob", "Tom")

    friends(0) = "Sue"

    println("Best friends " + friends(0))
    
    val friends2 = ArrayBuffer[String]()

    friends2.insert(0, "Phil")
    friends2 += "Mark"
    friends2 ++= Array("Susy", "Paul")

    friends2.insert(1, "Mike")

    friends2.remove(1,2)

    var friend: String = ""

    for(friend <- friends2)
      println(friend)

    for(j <- 0 to (favNums.length - 1)) {
      favNums(j) = j
      println(favNums(j))
    }


    val favNumsTimes2 = for (num <- favNums) yield 2 * num
    favNumsTimes2.foreach(println)
    // println(favNumsTimes2)

    var favNumsDiv4 = for(num <- favNums if num % 4 == 0) yield num
    favNumsDiv4.foreach(println)
  }
}
```

#### Example of traits
```scala
object ScalaLearning{
  def main(args: Array[String]){
    
  val superman = new Superhero("Superman")
  println(superman.fly)
  println(superman.hitByBullet)
  println(superman.ricochet(2500))
  } // End of main
  trait Flyable {
    def fly: String
  }

  trait BulletProof {
    def hitByBullet : String

    def ricochet (startSpeed: Double): String = {
      "The bullet is going to ricochet at a speed of %.1f ft/sec".format(startSpeed*.75)
    }
  }

  class Superhero(val name: String) extends Flyable with BulletProof {
    def fly = "%s flys through the air".format(this.name)
    def hitByBullet = "The bullet bounces off of %s".format(this.name)
  }

} // End of ScalaLearning
```

#### High Order functions( functions except functions as parameter)

```scala
object ScalaLearning{
  def main(args: Array[String]){

    val log10Func = log10 _

    println(log10Func(1000))


    def times3(num : Int) = num * 3
    def times4(num : Int) = num * 4

    def multIt(mul: (Int) => Double, num: Int) = {
      mul(num)
    }
   
    printf("3 * 4 = %.1f\n", multIt(times3, 4))
  }
}
```

#### Exception Handling
```scala

object ScalaLearning {
  def main(args: Array[String]) {

    def divideNums(num1: Int, num2: Int) = try {
      (num1 / num2)
    } catch {
      case ex: java.lang.ArithmeticException => "Can't divide by zero"
    } finally {
      //Clean up after exception
    }

    println("3 / 0 = " + divideNums(3, 0))

  }
}
```
