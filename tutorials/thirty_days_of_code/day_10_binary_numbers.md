## Day-10: Binary Numbers
### Objective 
Today, we're working with binary numbers. Check out the [Tutorial](https://www.hackerrank.com/challenges/30-hello-world/tutorial) tab for learning materials and an instructional video!

### Task 
Given a base-**10** integer, *n*, convert it to binary (base-**2**). Then find and print the base-**10** integer denoting the maximum number of consecutive **1**'s in *n*'s binary representation.

### Input Format
A single integer, *n*.

### Constraints
+ 1 <= *n* <= 10^6  

### Output Format
Print a single base-**10** integer denoting the maximum number of consecutive **1**'s in the binary representation of *n*.

### Sample Input 1
```python
5
```

### Sample Output 1
```python
1
```

### Sample Input 2
```python
13
```

### Sample Output 2
```python
2
```

### Explanation
*Sample Case 1:*  
The binary representation of **5** is **101**, so the maximum number of consecutive **1**'s is **1**.  

*Sample Case 2:*  
The binary representation of **13** is **1101**, so the maximum number of consecutive **1**'s is **2**.

### Submitted Code
```python
#!/bin/python

import sys


# Convert input to binary
n = int(raw_input().strip())
binary = ''
while n:
	binary = str(n % 2) + binary
	n = n / 2

# Count 1s
count = 0
carry = 0

for i in range(len(binary)):
	if binary[i] == '1':
		count += 1
	else: 
		if count > carry:
			carry = count
		count = 0
        
print count if count > carry else carry
```