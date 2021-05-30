# Basic questions

Here I write about standard basic questions that everyone should know how to solve.

## 1. FizzBuzz  
The golden standard. Given $n$, print all numbers between $1$ and $n$ included.
However, we have three conditions: if the number is multiple of $15$, print Fizzbuzz,
if it is a multiple of $5$, print $Fizz$ and if it is a multiple of $3$ print $Buzz$.

```python
def FizzBuzz(n):
  for i in range(1,n+1):
    if i % 3 == 0 and i % 5 == 0:
      print(FizzBuzz)
    elif i % 3 == 0:
      print(Fizz)
    elif i % 5 == 0:
      print(Buzz)
    else:
      print(i)
```
