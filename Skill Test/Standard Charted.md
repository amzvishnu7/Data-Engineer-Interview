## Standard Chartered - Skill Test 

#### Q1. Write a program to determine if a number n is happy.
- A happy number is a number defined by the following process:
- Starting with any positive integer, replace the number by the sum of the squares of its digits.
- Repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1.
- Those numbers for which this process ends in 1 are happy.
- Return true if n is a happy number, and false if not..

**Example 1:**
- *Input:* n = 19
- *Output:* true

**Explanation:**

- $1^2+9^2 = 82$
- $8^2+2^2 = 68$
- $6^2 +8^2 = 100$
- $1^2+0^2+0^2 = 1$

**Example 2:**

- *Input:* n=2
- *Output:* false

***Code :***

This Question We are using Scala

```scala
package pack

import scala.io.StdIn
import scala.collection.mutable

object scalastdy {
	def main(args:Array[String]):Unit= {
		
		println("Enter the Number : ")
		var n = StdIn.readInt()
		
		var sum = 0
		var rem = 0
		var sq = 0
		var numbers = mutable.Set[Int]()
		
		while (sum != 1) {
			while (n > 0) {
				rem = n % 10
				sq = rem * rem
				sum = sum + sq
				n = n / 10
			}
			if (numbers.contains(sum)) {
				println("false")
				return
			}
			numbers += sum
			n = sum
			sum = (if (sum == 1) 1 else 0)
			println(n)
		}
		println("true")
	}	
}
```

#### Q2. There are Rs.2000, Rs.500, Rs.200 and Rs.100 denominations available in ATM. Write a program to find out the denominations for a given user amount such that ATM has to dispense minimum number of notes. 

**Example:** 
- *Input :*  3100 
- *Output :*  Rs.  $2000 \rightarrow 1$, Rs. $500 \rightarrow 2$, Rs. $100 \rightarrow 1$ 

***Code :***

This Question We are using Scala

```scala
package pack
	import scala.io.StdIn
	object scalafun {
		
		def main(args:Array[String]):Unit={
			val l = List(2000,500,200,100)
			var n = StdIn.readInt()
			
			for(i<- 0 to 5)
			{
				if(n>=100) {
					var tq = n / l(i)
					var tr = n % l(i)
					println("Rs " + l(i) + " --- >" + tq)
					n = tr
				}
				else if((n>0) && (n<100)) {
					println(n + " Not avaliable")
					return
				}
			}
			
		}
		
	}

```

#### Q3. There are $n$ cars going to the same destination along a one-lane road. The destination is target miles away.

- You are given two integer array position and speed, both of length $n$, where $position[i]$ is the position of the $i^{th}$ car and $speed[i]$ is the speed of the $i^{th}$ car (in miles per hour).
- A car can never pass another car ahead of it, but it can catch up to it and drive bumper to bumper at the same speed.
- The faster car will slow down to match the slower car's speed. The distance between these two cars is ignored (i.e., they are assumed to have the same position).
- A car fleet is some non-empty set of cars driving at the same position and same speed. Note that a single car is also a car fleet.
-  If a car catches up to a car fleet right at the destination point, it will still be considered as one car fleet.
