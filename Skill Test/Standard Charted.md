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

***Code : ***

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
