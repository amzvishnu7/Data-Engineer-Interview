## Spark - Senerio Based Interview Question (Data Engineer)

The interviewers at the time of the interview asked the questions that are addressed below. We are not mentioning sources of the questions.


#### Q1. Create a DF by reading the Following table using Spark and Generate the expected Output. 

**Input Table**

|Address                  |
|-------------------------|
|Hyderabad#Telengana###123|
|Bangalore#Karnataka###245|

**Expected Output**

|      City|      State|  ID|
|----------|:---------:|---:|
| Hyderabad| Telengana | 123|
| Bangalore|  Karnataka| 245|

```scala
package pack
import org.apache.spark.SparkContext
import org.apache.spark.sql.SparkSession
import org.apache.spark.SparkConf
import org.apache.spark.sql.functions._

object just {
  def main(args: Array[String]): Unit = {

    val conf = new SparkConf().setAppName("first").setMaster("local[*]")
    val sc = new SparkContext(conf)
    sc.setLogLevel("ERROR")

    val spark = SparkSession.builder.getOrCreate()
    import spark.implicits._

  val df = Seq(("Hyderabad#Telengana###123"), ("Bangalore#Karnataka###245")).toDF("Address")
      df.show(false)
    val df1 = df.withColumn("Address",regexp_replace(col("Address"),"###",","))
      .withColumn("Address",regexp_replace(col("Address"),"#",","))
    df1.show(false)
    val df2 = df1.withColumn("City",split(col("Address"),",").getItem(0))
      .withColumn("State",split(col("Address"),",").getItem(1))
      .withColumn("ID",split(col("Address"),",").getItem(2))
      .drop("Address")

    df2.show()

  }
}

  ```

#### Q2. Create a DF by reading the Following table using Spark and Generate the expected Output. 

**Input Table**

| ID   |      Country_Names     |
|------|-----------------------:|
|101   | India,Pakistan,England |
|101   | INDIA#Pakistan#England |
|102   | Australia#Norway       |

**Expected Table**

| Id|Country_name |
|---|------------:|
|101|     England |
|102|   Australia |
|101|       India |
|102|      Norway |
|101|    Pakistan |




```scala
package pack
import org.apache.spark.SparkContext
import org.apache.spark.sql.SparkSession
import org.apache.spark.SparkConf
import org.apache.spark.sql.functions._
import org.apache.spark.sql.types._
import org.apache.spark.sql._
object testobj {
  def main(args: Array[String]): Unit = {

    val conf = new SparkConf().setAppName("first").setMaster("local[*]")
    val sc = new SparkContext(conf)
    sc.setLogLevel("ERROR")

    val spark = SparkSession.builder.getOrCreate()
    import spark.implicits._

    val df = Seq((101, "India,Pakistan,England"),(101,"INDIA#Pakistan#England"),(102,"Australia#Norway")).toDF("Id","Country_name")
    df.show()

    val odf = df.withColumn("Country_name", regexp_replace(col("Country_name"),"#",","))
      .withColumn("Country_name", split(col("Country_name"),","))
      .withColumn("Country_name",explode(col("Country_name")))
      .withColumn("Country_name",initcap(col("Country_name")))
      .dropDuplicates(Seq("id","Country_name"))


    odf.show()

  }
  }
 ```

