## Synechron - Interview Senerio Based Question (Data Engineer)

The interviewers at the time of the interview asked the questions that are addressed below. We are not mentioning sources of the questions.


### Section -1 : Scala Spark or Pyspark (For this Example We are using Scala Code)

#### Q1. Read the contents of a text file called "sync.txt" using Scala Spark or PySpark to get the desired output.

**SYNC.Txt**

1,Rahul,Dravid-100k <br />
2,Virat,Kohli-200k <br />
3,MS,Dhoni,270k <br />
4,Dinesh,Karthik,180k <br />

**Desired Output**


| ID|First Name  |Last Name  |Salary |
|---|:----------:|:---------:|------:|
|  1|     Rahul  |   Dravid  |  100k |
|  2|     Virat  |    Kohli  |  200k |
|  3|        MS  |    Dhoni  |  270k |
|  4|    Dinesh  |   Karthik |  180k |


**Sol : ** 

Here If you look at the content of text file, You can able to the delimiter of Thrid colum of first and second row is hyphen **-**, So first replace that with comma **,**
then *split() & getItem()* solves the problem.


```scala

package pack
import org.apache.spark.SparkContext
import org.apache.spark.sql.SparkSession
import org.apache.spark.SparkConf
import org.apache.spark.sql.functions._
import org.apache.spark.sql.types._

object sync {
  
    def main(args: Array[String]): Unit = {

    val conf = new SparkConf().setAppName("first").setMaster("local[*]")
    val sc = new SparkContext(conf)
    sc.setLogLevel("ERROR")

    val spark = SparkSession.builder.getOrCreate()
    import spark.implicits._
    
    val df = spark.read.text("file:///D:/Data_Sets/Senerio/sync.txt")
    df.show()

    val odf = df.withColumn("value", regexp_replace(col("value"),"-",","))
      .withColumn("ID",split(col("value"),",").getItem(0))
      .withColumn("First Name",split(col("value"),",").getItem(1))
      .withColumn("Last Name",split(col("value"),",").getItem(2))
      .withColumn("Salary",split(col("value"),",").getItem(3))
      .drop("value")
    odf.show()
    
    }
}
      
  ```

One interviewer mentions it while answering a similar question with a small variation. 

###### Let's say the following describes the contents of Sync.txt, Use Scala Spark or PySpark to read the contents of a text file named "sync.txt" to get the required result.

**SYNC.Txt**

1,Rahul,Dravid-10000 <br />
2,Virat,Kohli-20000 <br />
3,MS,Dhoni,27000 <br />
4,Dinesh,Karthik,18000 <br />


**Desired Output**

| ID|First Name  |Last Name  |Salary |
|---|:----------:|:---------:|------:|
|  1|     Rahul  |   Dravid  |  100k |
|  2|     Virat  |    Kohli  |  200k |
|  3|        MS  |    Dhoni  |  270k |
|  4|    Dinesh  |   Karthik |  180k |


**Sol : **

Add an extra line, problem solves - Dividing by 100 makes Salary col to *Big Int* so cast it to integer and then to string then Use Lit function to add *K*.

```scala

package pack
import org.apache.spark.SparkContext
import org.apache.spark.sql.SparkSession
import org.apache.spark.SparkConf
import org.apache.spark.sql.functions._
object sync {
    def main(args: Array[String]): Unit = {

    val conf = new SparkConf().setAppName("first").setMaster("local[*]")
    val sc = new SparkContext(conf)
    sc.setLogLevel("ERROR")

    val spark = SparkSession.builder.getOrCreate()
    import spark.implicits._
      
          val df = spark.read.text("file:///D:/Data_Sets/Senerio/sync.txt")
    df.show(false)

    val odf = df.withColumn("value", regexp_replace(col("value"),"-",","))
      .withColumn("ID",split(col("value"),",").getItem(0))
      .withColumn("First Name",split(col("value"),",").getItem(1))
      .withColumn("Last Name",split(col("value"),",").getItem(2))
      .withColumn("Salary",split(col("value"),",").getItem(3))
      .withColumn("Salary",concat(((col("Salary")/100).cast("Int")).cast("String"),lit("K")))
      .drop("value")
    odf.show()
      
    }
}

  ```
  
 ### Section - 2 : Scala or Python
  
 #### Q1. Create a programme that will show the first 10 Fibonacci sequences with the specified first and second terms as 0 and 1.
    
**Sol : ** 

  ```scala

  package pack
import scala.io.StdIn
object Fibno {
  def main(args:Array[String]):Unit={

    println("Enter the Number of number")
    var n = StdIn.readInt()
    println()
    var a = 0
    var b = 1
    var temp = 0
    print(s"The first $n terms of Fibnoaci sequence are : $a, $b" )
    for(i <- 0 to n)
      {
        temp = a+b
        a = b
        b = temp
        print(", " + temp)

      }

  }

}
  ```
