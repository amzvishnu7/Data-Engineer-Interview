## Senerio Based Questions

The interviewers at the time of the interview asked the questions that are addressed below. We are not mentioning a company name or sources of the questions.

#### Q1. Write a Scala programme need to find the length and based on length print the string ascending order, if 2 string has same length need to print based on albhabatical order.

**Input :**

val string=Seq( "xelome Welcome to STRING. protein interaction Networks funcional Enrichment Analysis") 

**Sol** :

```scala

object MyClass {
    
    def main(args: Array[String]) {
        val s = Seq("xelome Welcome to STRING. protein interaction Networks functional Enrichment Analysis")
        
        println(s)
        
        val str = s.flatMap(_.split(" "))
        
        println(str)
        
        val out = str.sortWith(_ < _)
        .sortBy(_.toLowerCase)
        .sortWith(_.length < _.length)
        
        println(out)
        out.foreach(println)

        
    }
}
```

**Output :**

List(xelome, Welcome, to, STRING., protein, interaction, Networks, functional, Enrichment, Analysis) <br />

to <br />
xelome <br />
protein <br />
STRING. <br />
Welcome <br />
Analysis <br />
Networks <br />
Enrichment <br />
functional <br />
interaction <br />

