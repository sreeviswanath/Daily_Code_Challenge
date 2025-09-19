# 🚀 Daily_Code_Challenge_Solutions

This repository contains my solutions to advanced technical training daily problems.  
Each problem includes the **question** and my **Python solution**.

---

## 1. 19/09/2025  
**Question:**  
<Problem Statement
You are given an integer n and a maximum iteration limit k.
Define the process:

1. Reverse the digits of n.
2. Add this reversed number to n.
3. Check if the result is a palindrome.
4. If not, repeat the process with the new number.

If a palindrome appears within k iterations, return the number of iterations and the
palindrome.
If no palindrome appears after k iterations, return [-1, -1] (indicating that n is a Lychrel
candidate under this limit).
Example 1
Input:
n = 89, k = 30
Process:
89 + 98 = 187
187 + 781 = 968
968 + 869 = 1837

...
after 24 iterations → 8813200023188 (palindrome)
Output:
[24, 8813200023188]>  

**Code (Python):**
```python
def check(n,k,max):
  if k<=max:
    temp=int(str(n)[::-1])
    sum=n+temp
    rev_sum=int(str(sum)[::-1])
    if rev_sum==sum:
      k+=1
      return(sum,k,max)
    else:
      k+=1
      return check(sum,k,max)
  else:
    return([-1,-1,-1])
num=int(input("Enter a number:"))
max=int(input("Enter max iteration:"))
k=0
total,iter,max_val=check(num,k,max)
print([iter,total])
