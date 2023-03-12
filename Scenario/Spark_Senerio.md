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


