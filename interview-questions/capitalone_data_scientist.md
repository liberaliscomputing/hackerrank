### CapitalOne - Data Scientist

#### Coin Flipping  
**Q1**.  
Given two integers M and N separated by spaces on STDIN, output to STDOUT the number of distinct ways to flip exactly N heads on M coin flips.  

For example, on the input:  

`3 2`  

your program should output (since you could have HHT, HTH, or THH):  

`3`  

**A1**.  
```python
# Enter your code here. Read input from STDIN. Print output to STDOUT.

# Define a factorail function
def factorial(num):
	if num <= 1:
		return 1
	return num * factorial(num - 1)

# Read in STDIN as a tuple, converting string to integer
m, n = map(int, raw_input().strip().split())

# Print the result
print factorial(m) / (factorial(m - n) * factorial(n))
```  

#### Sorting Sorted Words  

**Q2**.  
Given a sentence on STDIN:  

1. Strip all non-alphabetic characters  
2. Convert all letters to lowercase  
3. Sort all of the letters within each word  
4. Sort the sorted words within the sentence and eliminate duplicates  
5. Output to STDOUT the list from Step 4 with words separated by spaces  

For example, given the input:  

`I may opt for a top yam for Amy, May, and Tommy.`  

your program should print:  

`a adn amy for I mmoty opt`  

**A2**.  
```python
# Enter your code here. Read input from STDIN. Print output to STDOUT

# Import the regular expression module
import re


# Define an alphabetic-charcter rule
regex = re.compile('[^a-zA-Z]')

# Read in STDIN
sentence = raw_input()

# Remove all non-alphabetic characters, lower-casing the words
words = [regex.sub('', word).lower() for word in sentence.strip().split()]

# Sort all of the letters within each word
words = [''.join(sorted(word)) for word in words]

# Sort the sorted words and eliminate duplicates
words = sorted(set(words))

# Print the result
print ' '.join(words)
```  

#### Fun with Collatz  

**Q3**.  
The Collatz conjecture defines a function f(n) = n / 2 if n is even or 3 * n + 1 if n is odd. By repeating this function, it is conjectured that all numbers eventually reach 1. Given two integers N and K separated by a space or STDIN, apply the function f to the value N a total of K times and print STDOUT the resulting value.  

For example, on the input:  

`111 5`  

the value at each step should go from 111 to 334 to 167 to 502 to 251 to 754, and your program should print:  

`754`  

**A3**.  
```python
# Enter your code here. Read input from STDIN. Print output to STDOUT
# Define a Collatz conjecture function
def collatz_conjecture(number):
	if number % 2 == 0:
		return number / 2
	return 3 * number + 1

# Read in STDIN as a tuple, converting string to integer
n, k = map(int, raw_input().strip().split())

# Execute the function for k times
for _ in range(k):
    n = collatz_conjecture(n)

# Print the result
print n
```  

#### Manual Logistic Regression  
**Q4**.  
Write a program that reads a set of logistic coefficients separated by spaces (with the last coefficient corresponding to the intercept), a newline character, and a row of data to be scored using the given model also separated by spaces. Using the logistic function f(x) = 1 / (1 + e^-x), compute the model’s output and print it to STDOUT rounded to exactly 3 decimal places.  

For example, given the input:  
```
1.5 2 -1 -2.5 3
2 -1 2 0.5
```  

your program should print:  

`0.679`

and given:  

```
1 1
-1
```  

your program should print:  

`0.500`  

**A4**.  
```python
# Enter your code here. Read input from STDIN. Print output to STDOUT

# Import the math module to use the exponential function
import math


# Define a sigmoid function
def sigmoid(x):
	return 1 / (1 + math.exp(-x))

# Read in coefficients as a tuple, converting string to float
coefficients = map(float, raw_input().strip().split())

# Read in data points as a tuple, converting string to float
data = map(float, raw_input().strip().split())

# Set an initial value of linear function
prediction = 0

# Calculate the linear function, using coefficients and data
prediction = sum(c * d for c, d in zip(coefficients, data))

# Add constant theta0 to prediction
prediction += coefficients[-1]

# Conduct logistic regression
result = sigmoid(prediction)

# Print the result to the nearest thousandth
print '%.3f' % result
```