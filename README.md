# HexSoftwares_Project_Game-of-Tic-Tac-Toe-
I am currently working on my third project as an Intern Python Programmer at Hex Software, where I am developing a Python-based Tic-Tac-Toe game."

#Amukelani Celest Charzen 
#Hex Sofeware POROJECT 1 FIBONACCI GENERATOR 

#Mytake on generating the Fibonacci series in Python is with a slightly different approach. I’ve added features like user-defined input validation,
#a generator-based approach for memory efficiency,and a creative way of representing the series. 

# 1. Basic Recursive Approach with Memoization
# This approach avoids redundant calculations using a cache (dictionary).
def fibonacci_recursive(n, memo={}):
    if n in memo:
        return memo[n]
    
    if n <= 1:
        return n
     
    memo[n] = fibonacci_recursive(n - 1, memo) + fibonacci_recursive(n - 2, memo)
    return memo[n]

#Example of Basic Recursive Approach with MemoizationUser input
terms = int(input("Enter the number of Fibonacci terms: "))
print("Fibonacci Series:")
for i in range(terms):
    print(fibonacci_recursive(i), end=" ")

# 2. Generator-Based Fibonacci Series (Memory Efficient)
#Using Python generators, we calculate Fibonacci numbers lazily, which is memory efficient.
def fibonacci_generator():
    a, b = 0, 1
    while True:  
        yield a
        a, b = b, a + b
 
n = int(input("Enter the number of Fibonacci terms: "))
print("Fibonacci Series:")
fib_gen = fibonacci_generator()
for _ in range(n):
    print(next(fib_gen), end=" ")

# 3. Matrix Exponentiation Approach (Optimized for Large n)
#This approach computes the n-th Fibonacci number using matrix multiplication, reducing the time complexity to O(log n).
import numpy as np

def matrix_fibonacci(n):
    def matrix_mult(A, B):
        return np.dot(A, B).astype(int)

    def power(F, n):
        if n == 1:
            return F
        if n % 2 == 0:
            half_power = power(F, n // 2)
            return matrix_mult(half_power, half_power)
        else:
            return matrix_mult(F, power(F, n - 1))

    F = np.array([[1, 1], [1, 0]])
    if n == 0:
        return 0
    result = power(F, n - 1)
    return result[0][0]

n = int(input("Enter the term you want in the Fibonacci series: "))
print(f"The {n}-th Fibonacci number is: {matrix_fibonacci(n)}")


