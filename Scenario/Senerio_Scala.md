## Senerio Based Questions

The interviewers at the time of the interview asked the questions that are addressed below. We are not mentioning a company name or sources of the questions.

### Section -1 Scala Programme 

#### Q1. If a list/array has numbers from range 1 to 100 in random way, but a number is missing i.e. list will have only 99 elements. Find a missing element without sorting an array. ( Do not use min, max function )

**Sol** : We create a list of 100 numbers and we remove one element from that list using *.filterNot()*

```scala
package pack
import scala.io.StdIn
object scalastudy {

  def main(args:Array[String]):Unit={

    var l = List.range(1,101)
    l = l.filterNot(_==10)

    val s = (100*(1+100))/2
    var s1=0

   for(i <- 0 to 98)
     {
     s1 = s1+l(i)
     }
     println("The Missing number is "+(s - s1) )

  }
}
```

#### Q2.Calculate the sum of the elements in the diagonal of a following matrix / 2D array, and logic should be dynamic enough to work on any NxN matrix

**Input :** [1,2,3],[4,5,6],[7,8,9]

**Output :**

```math
\begin{pmatrix}
1 & 2 & 3\\
4 & 5 & 6\\
7 & 8 & 9
\end{pmatrix}

```
- sum1 = 1 + 5 + 9
- sum2 = 3 + 5 + 7 

```scala
package pack
import scala.Array.ofDim
import scala.io.StdIn
object digonalsum {

  def main(arg: Array[String]): Unit = {

    println("Enter the No of rows & Columns of Matrix")
    var m = StdIn.readInt()
    var n = StdIn.readInt()
    var A = ofDim[Int](m,n)
    var sum = 0
    var sum1 = 0

    if (m == n) {
      println("Enter The Elements of  Matrix")
      for (i <- 0 until m; j <- 0 until n) {
        print(s"$i $j th element : ")
        A(i)(j) = StdIn.readInt()
      }
      println()
      println("Display Matrix")
      for (i <- 0 until m) {
        for (j <- 0 until n) {
          print(" " + A(i)(j))
        }
        println()
      }

      for (i <- 0 until m; j <- 0 until n) {
        if (i == j) {
          sum = sum + A(i)(j)
        }
        if ((i + j) == (n - 1)) {
          sum1 = sum1 + A(i)(j)
        }
      }
      println()
      println("Sum of Main Diagonal : " + sum)
      println("Sum of Second Diagonal : " + sum1)
    }
    else {
      println("Not a Square Matrix")
    }

  }

}

```
