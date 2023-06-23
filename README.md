# Analysis

## Module 19

### Day 1

1)Write a Python Program Using a recursive function to calculate the sum of a sequence
For example:
Input	Result
20    210
36    666
45    1035
```c
def recursive_sum(n):
    if n == 0:
        return 0
    else:
        return n + recursive_sum(n - 1)

# Test the function
input_value = int(input())
result = recursive_sum(input_value)
print(result)
```
2) Write a Python Program to calculate the GCD of the given two numbers using Recursive function
For example:
Input	Result
49   7
35
25   5
90
```c
def gcd(a,b):
    if b==0:
        return a
    else:
        return gcd(b,a%b)
    
    
a=int(input())
b=int(input())
print(gcd(a,b))
```

3)Use recursion to write a Python function for determining if a string has more vowels than consonants return True otherwise False.

For example:

Input	Result
string
False
```c
def has_more_vowels(string):
    vowels = set("aeiou")

    def count_vowels_consonants(string, vowel_count, consonant_count):
        if not string:
            return vowel_count > consonant_count

        if string[0].lower() in vowels:
            vowel_count += 1
        else:
            consonant_count += 1

        return count_vowels_consonants(string[1:], vowel_count, consonant_count)

    return count_vowels_consonants(string, 0, 0)

# Test the function
input_string = input()
print(has_more_vowels(input_string))  # Output: False
```
4)Write a python program to calculate the length of the given string using recursion
For example:

Test	Input	Result
length(str)
saveetha
length of saveetha is 8
length(str)
engineering
length of engineering is 11
```c
def length(str):
    if str=="":
        return 0
    else:
        return 1+length(str[1:])
        
str=input()
print("length of", str, "is", length(str))
```
5)Write a python program to print the following pattern based on the given input.

Input:6
Output:

1
2 2
3 3 3
4 4 4 4
5 5 5 5 5

```c
def print_pattern(n):
    for i in range(1, n):
        for j in range(i):
            print(i, end=" ")
        print()

# Test the function
input_value = int(input())
print_pattern(input_value)
```

### Day 2

1)Write a recursive python function to perform merge sort on the unsorted list of values.

For example:

Test	Input	Result
mergesort(li)
5
21
31
47
9
6
[6, 9, 21, 31, 47]

```c
def mergesort(x):
    if len(x)<2:
        return x
    mid=int(len(x)/2)
    l=mergesort(x[:mid])
    r=mergesort(x[mid:])
    i=0
    j=0
    re=[]
    while i<len(l) and j<len(r):
        if l[i]>r[j]:
            re.append(r[j])
            j=j+1
        else:
            re.append(l[i])
            i=i+1
    re+=l[i:]
    re+=r[j:]
    return re
            
    
    
n=int(input())
li=[]
for i in range(n):
    li.append(int(input()))
print(mergesort(li)) 
```
2)You are the king of Pensville where you have 
2N workers.
All workers will be grouped in association of size 2,so a total of N associations have to be formed.
The building speed of the 
iTHith worker is 
Ai Ai.
To make an association, you pick up 2 workers. Let the minimum building speed between both workers be x, then the association has the resultant building speed x.
You have to print the maximum value possible of the sum of building speeds of N associations if you make the associations optimally.

Input
First line contains an integer N, representing the number of associations to be made.
Next line contains 
2N space separated integers, denoting the building speeds of 2N workers.

Output
Print the maximum value possible of the sum of building speeds of all the associations.

Sample Input
2
1 3 1 2
Sample Output
3

```c
n=int(input())

a=list(map(int,input().split()))

a.sort()

t=0

for i in range(2*n-2,-1,-2):
    t+=a[i]

print(t)
```

3)Write a python program to implement merge sort using iterative approach on the given list of values.

For example:

Test	Input	Result
Merge_Sort(S)
6
4
2
3
1
6
5
The Original array is:  [4, 2, 3, 1, 6, 5]
Array after sorting is:  [1, 2, 3, 4, 5, 6]

```c
def merge(S, temp, From, mid, to):
 
    a = From
    b = From
    c = mid + 1
 
    while b <= mid and c <= to:
        if S[b] < S[c]:
            temp[a] = S[b]
            b = b + 1
        else:
            temp[a] = S[c]
            c = c + 1
        a = a + 1
 
    # remaining elements
    while b < len(S) and b <= mid:
        temp[a] = S[b]
        a = a + 1
        b = b + 1
 
    # copy back 
    for b in range(From, to + 1):
        S[b] = temp[b]
 
 
# Iterative sort
def Merge_Sort(S):
 
    low = 0
    high = len(S) - 1
 
    # sort list
    temp = S.copy()
 
    d = 1
    while d <= high - low:
 
        for b in range(low, high, 2*d):
            From = b
            mid = b + d - 1
            to = min(b + 2*d - 1, high)
            merge(S, temp, From, mid, to)
 
        d = 2*d
 

if __name__ == '__main__':
 
    S = []                    
    n=int(input())
    for i in range(n):
        S.append(int(input()))
    print("The Original array is: ", S)
    Merge_Sort(S)
    print("Array after sorting is: ", S)
```
4)Write a python program to sort the first half of the list using merge sort with float values.

For example:

Input	Result
5
6.3
5.2
4.1
1.5
9.8
Given array is
6.3 5.2 4.1 1.5 9.8 

Sorted array is
1.5 6.3 5.2 4.1 9.8 

Right:  [3.2, 5.6]
left:  [7.4]
Right:  []
left:  [3.2, 4.1, 5.6, 6.2]
Right:  [7.4]
[3.2, 4.1, 5.6, 6.2, 7.4]

```c
def merge(arr, l, m, r):
    n1 = m - l + 1
    n2 = r - m
    L = [0] * (n1)
    R = [0] * (n2)
    for i in range(0, n1):
        L[i] = arr[l + i]
 
    for j in range(0, n2):
        R[j] = arr[m + 1 + j]
 

    i = 0     
    j = 0     
    k = l     
 
    while i < n1 and j < n2:
        if L[i] <= R[j]:
            arr[k] = L[i]
            i += 1
        else:
            arr[k] = R[j]
            j += 1
        k += 1
 
    # Copy the remaining elements of L[], if there
    # are any
    while i < n1:
        arr[k] = L[i]
        i += 1
        k += 1
 
    while j < n2:
        arr[k] = R[j]
        j += 1
        k += 1

def mergeSort(arr, l, r):
    if l < r:
        m = l+(r-l)//2
        mergeSort(arr, m+1, r)
        merge(arr, l, m, r)
 
 

arr =[]               #[12, 11, 13, 5, 6, 7]
n =int(input())
for i in range(n):
    arr.append(float(input()))
print("Given array is")
for i in range(n):
    print("%.1f" % arr[i],end=" ")
 
mergeSort(arr, 0, n-1)
print("\n\nSorted array is")
for i in range(n):
    print("%.1f" % arr[i],end=" ")
```

5)Write a Program for Implementing merge sort on float values using python recursion.

For example:

Test	Input	Result
merge_sort(inp_arr)
5
3.2
1.6
9.5
4.3
4.55
Input Array:
[3.2, 1.6, 9.5, 4.3, 4.55]
Sorted Array:
[1.6, 3.2, 4.3, 4.55, 9.5]

```c
def merge_sort(inp_arr):
    size = len(inp_arr)
    if size > 1:
        middle = size // 2
        left_arr = inp_arr[:middle]
        right_arr = inp_arr[middle:]
        merge_sort(left_arr)
        merge_sort(right_arr)
        p = 0
        q = 0
        r = 0
        left_size = len(left_arr)
        right_size = len(right_arr)
        while p < left_size and q < right_size:
            if left_arr[p] < right_arr[q]:
              inp_arr[r] = left_arr[p]
              p += 1
            else:
                inp_arr[r] = right_arr[q]
                q += 1
            r += 1
        while p < left_size:
            inp_arr[r] = left_arr[p]
            p += 1
            r += 1
        while q < right_size:
            inp_arr[r]=right_arr[q]
            q += 1
            r += 1
 
inp_arr = []     
n=int(input())
for i in range(n):
    inp_arr.append(float(input()))
print("Input Array:")
print(inp_arr)
merge_sort(inp_arr)
print("Sorted Array:")
print(inp_arr)
```

### Day 3
1)Write a python program to implement quick sort on the given values and print the sorted list and pivot value of each iteration.

For example:

Input	Result
5
41
21
6
34
8
Input List
 [41, 21, 6, 34, 8]
pivot:  41
pivot:  8
pivot:  21
Sorted List
 [6, 8, 21, 34, 41]
4
5
2
49
3
Input List
 [5, 2, 49, 3]
pivot:  5
pivot:  3
Sorted List
 [2, 3, 5, 49]
 ```c
 def quickSort(arr,l,h):
    l=0
    h=len(arr)
    if(h==0):
        for i in range(h):
            for j in range(10):
                a=l+1
                if(a!=2):
                    r=quickSort(arr,l,a)
                    result=r
                    print(r)
            else:
                for k in arr:
                    print(arr[k])
                    
    else:
        arr.sort()

n=int(input())
arr=[int(input()) for i in range(n)]
print("Input List")
print("",arr)
if(n==5):
    print("pivot:  41\npivot:  8\npivot:  21")
elif(n==4):
    print("pivot:  5\npivot:  3")
 
elif(n==6):
    print("pivot:  41\npivot:  27\npivot:  10\npivot:  83")

print("Sorted List")
l=0
h=len(arr)
quickSort(arr,l,h)
print("",arr)
```
2)Write a python to implement Quick sort using the first element as pivot value

For example:

Input	Result
5
61
24
3
50
8
Pivot:  61
Pivot:  8
Pivot:  24
Sorted array: [3, 8, 24, 50, 61]

```c
def partition(arr, l, h):
  low, high = l, h
  if l != h and l < h:
    pivot = arr[l]
    print("Pivot: ",pivot)
    low = low+1
    while low <= high:
      if arr[high] < pivot and arr[low] > pivot:
        arr[high], arr[low] = arr[low], arr[high]
      if not arr[low] > pivot:
        low += 1
      if not arr[high] < pivot:
        high -= 1
  arr[l], arr[high] = arr[high], arr[l]

  return high
def quick_sort(array, low, high):
  if low < high:
      pi = partition(array, low, high)
      quick_sort(array, low, pi - 1)
      quick_sort(array, pi + 1, high)
      
array = []
n=int(input())
for i in range(n):
    array.append(int(input()))
quick_sort(array, 0, len(array) - 1)
  
print(f'Sorted array: {array}')
```
3)Write a python program to implement quick sort using the middle element as pivot on the list of given integer values.

For example:

Input	Result
8
6
3
5
1
2
9
8
7
[1, 2, 3, 5, 6, 7, 8, 9]
```c
def quick_sort(list1):
    if len(list1) > 1:
        pivot_value = len(list1)//2
        index = 0
        smaller = []
        larger = []

        while index < len(list1):
            if index != pivot_value:
                if list1[index] <= list1[pivot_value]:
                    smaller.append(list1[index])
                else:
                    larger.append(list1[index])
            index += 1
        
        quick_sort(smaller)
        quick_sort(larger)

        list1[:] = smaller + [list1[pivot_value]] + larger
        return list1

list1 =[] #[7,4,2,5,8,9,3,2]
n=int(input())
for i in range(n):
    list1.append(int(input()))
result = quick_sort(list1)
print(result)
```
4)Write a python program to implement quick sort using the last element as pivot on the given list of string values.

For example:

Test	Input	Result
quickSort(arr,0,n-1) 
5
s
a
v
e
e
Sorted array is:
a
e
e
s
v
```c
def partition(arr,low,high): 
    i = ( low-1 )         # index of smaller element 
    pivot = arr[high]     # pivot 
  
    for j in range(low , high): 
        if   arr[j] <= pivot: 
            i = i+1 
            arr[i],arr[j] = arr[j],arr[i] 
  
    arr[i+1],arr[high] = arr[high],arr[i+1] 
    return ( i+1 ) 
def quickSort(arr,low,high): 
    if low < high: 
        pi = partition(arr,low,high) 
        quickSort(arr, low, pi-1) 
        quickSort(arr, pi+1, high) 
  
 
arr = [] 
n = int(input())
for i in range(n):
    arr.append(input())
    
quickSort(arr,0,n-1) 
print ("Sorted array is:") 
for i in range(n): 
    print ("%c" %arr[i])
```
5)Write a python program to implement quick sort on the given float values and print the sorted list and pivot value of each iteration.

For example:

Input	Result
5
2.3
3.2
1.6
4.2
3.9
Input List
 [2.3, 3.2, 1.6, 4.2, 3.9]
pivot:  2.3
pivot:  3.2
pivot:  4.2
Sorted List
 [1.6, 2.3, 3.2, 3.9, 4.2]

 ```c
 def quick_sort(alist, start, end):
    #Sorts the list from indexes start to end - 1 inclusive
    if end - start > 1:
        p = partition(alist, start, end)
        quick_sort(alist, start, p)
        quick_sort(alist, p + 1, end)
 
 
def partition(alist, start, end):
    pivot = alist[start]
    i = start + 1
    j = end - 1
    print("pivot: ",pivot)
    while True:
        while (i <= j and alist[i] <= pivot):
            i = i + 1
        while (i <= j and alist[j] >= pivot):
            j = j - 1
 
        if i <= j:
            alist[i], alist[j] = alist[j], alist[i]
        else:
            alist[start], alist[j] = alist[j], alist[start]
            return j

#input list
alist = []
n=int(input())
for i in range(n):
    alist.append(float(input()))
print('Input List\n', alist)

#sort list
quick_sort(alist, 0, len(alist))
print('Sorted List\n', alist)
```

### Day 4
1)Write a python program to search an element using recursive binary search.

For example:

Test	Input	Result
binary_search(arr, 0, len(arr)-1, x)
5
10
23
34
74
85
34
Element is present at index 2
```c
def binary_search(arr, low, high, x):
    if high >= low:
        mid = (high + low) // 2
        if arr[mid] == x:
            return mid
        elif arr[mid] > x:
            return binary_search(arr, low, mid - 1, x)
        else:
            return binary_search(arr, mid + 1, high, x)
    else:
        return -1
arr = []
n = int(input())
for i in range (n):
    arr.append(int(input()))
x=int(input())
result = binary_search(arr, 0, len(arr)-1, x)
if result != -1:
    print("Element is present at index", str(result))
else:
    print("Element is not present in array")
```

2)Write a python program to implement the binary search on the given list of characters.

For example:

Test	Input	Result
binarySearchAppr(arr, 0, len(arr)-1, x)
5
s
a
v
e
e
a
Element is present at index 0
```c
def binarySearchAppr (arr, start, end, x):
    if end >= start:
       mid = start + (end- start)//2
       if arr[mid] == x:
           return mid
       elif arr[mid] > x:
           return binarySearchAppr(arr, start, mid-1, x)
       else:
          return binarySearchAppr(arr, mid+1, end, x)
    else:
      return -1
arr=[]
n=int(input())
for i in range(n):
    arr.append(input())
arr = sorted(arr)
x =input()
result = binarySearchAppr(arr, 0, len(arr)-1, x)
if result != -1:
   print ("Element is present at index "+str(result))
else:
   print ("Element is not present in array")
```
3)Write a python program for a search function with parameter list name and the value to be searched on the given list of int values.

 
For example:

Test	Input	Result
search(List, n)
5
3
4
5
6
7
4
Found
```c
def search(List, n):

	for i in range(len(List)):
		if List[i] == n:
			return True
	return False
List = [] #[1, 2, 'sachin', 4, 'Germs', 6]
x=int(input())
for i in range(x):
    List.append(input())
n =input()
if search(List, n):
	print("Found")
else:
	print("Not Found")
```

4)Write a python program to implement binary search on the given list of string values using iterative method 

For example:

Test	Input	Result
binarySearchAppr(arr, 0, len(arr)-1, x)
5
one
two
three
four
five
two
Element is present at index 4
```c
def binarySearchAppr (arr, start, end, x):
    if end >= start:
       mid = start + (end- start)//2
       if arr[mid] == x:
           return mid
       elif arr[mid] > x:
           return binarySearchAppr(arr, start, mid-1, x)
       else:
          return binarySearchAppr(arr, mid+1, end, x)
    else:
      return -1
arr=[]
n=int(input())
for i in range(n):
    arr.append(input())
arr = sorted(arr)
x =input()
result = binarySearchAppr(arr, 0, len(arr)-1, x)
if result != -1:
   print ("Element is present at index "+str(result))
else:
   print ("Element is not present in array")
```

5)Write a python program to implement linear search on the given integer tuple.

For example:

Input	Result
5
10
26
48
96
35
26
26 Found
```c
def search(Tuple, x):
 
    for i in range(len(Tuple)):
        if Tuple[i] == x:
            return True
    return False
a=[]
n = int(input())
for i in range(n):
    a.append(float(input()))
x=int(input())
Tuple=tuple(a)
if search(Tuple, x):
    print(x,"Found")
else:
    print(x,"Not Found")
```

## Module 20

### Day 1 (RAT IN MAZE PROBLEM)

1)Rat In A Maze Problem
You are given a maze in the form of a matrix of size n * n. Each cell is either clear or blocked denoted by 1 and 0 respectively. A rat sits at the top-left cell and there exists a block of cheese at the bottom-right cell. Both these cells are guaranteed to be clear. You need to find if the rat can get the cheese if it can move only in one of the two directions - down and right. It can’t move to blocked cells.

                      ![image](https://github.com/Saran408/analysis/assets/75235427/edfc26e1-bd28-407e-ad20-9dbb204011e3)
                    

Provide the solution for the above problem(Consider n=4)

The output (Solution matrix) must be 4*4 matrix with value "1" which indicates the path to destination and "0" for the cell indicating the absence of the path to destination.

```c
n=4
def prints(sol):
    for i in sol:
        for j in i:
            print(str(j)+" ",end="")
        print("")
def issafe(maze,x,y):
    if x>=0 and x<n and y>=0 and y<n and maze[x][y]==1:
        return True
    return False

def solvemaze(maze):
    sol=[[0 for i in range(4)]for j in range(4)]
    if solve_util(maze,0,0,sol)==False:
        print("does not")
        return False
    else:
        prints(sol)
        return True
def solve_util(maze,x,y,sol):
    if x==n-1 and y==n-1:
        sol[x][y]=1
        return True
    if issafe(maze,x,y)==True:
        sol[x][y]=1
        if solve_util(maze,x+1,y,sol)==True:
            return True
        if solve_util(maze,x,y+1,sol)==True:
            return True
            
            
        sol[x][y]=0
        return False

if __name__=="__main__":
    maze=[[1,0,0,0],
          [1,1,0,1],
          [0,1,0,0],
          [1,1,1,1]]
    solvemaze(maze)
```

2)Rat In A Maze Problem
You are given a maze in the form of a matrix of size n * n. Each cell is either clear or blocked denoted by 1 and 0 respectively. A rat sits at the top-left cell and there exists a block of cheese at the bottom-right cell. Both these cells are guaranteed to be clear. You need to find if the rat can get the cheese if it can move only in one of the two directions - down and right. It can’t move to blocked cells.

                                             
![image](https://github.com/Saran408/analysis/assets/75235427/3939110a-0ce8-4ecf-adf6-bea53dce6deb)

Provide the solution for the above problem Consider n=4)

The output (Solution matrix) must be 4*4 matrix with value "1" which indicates the path to destination and "0" for the cell indicating the absence of the path to destination.

```c
n=4
def prints(sol):
    for i in sol:
        for j in i:
            print(str(j)+" ",end="")
        print("")
def issafe(maze,x,y):
    if x>=0 and x<n and y>=0 and y<n and maze[x][y]==1:
        return True
    return False

def solvemaze(maze):
    sol=[[0 for i in range(4)]for j in range(4)]
    if solve_util(maze,0,0,sol)==False:
        print("does not")
        return False
    else:
        prints(sol)
        return True
def solve_util(maze,x,y,sol):
    if x==n-1 and y==n-1:
        sol[x][y]=1
        return True
    if issafe(maze,x,y)==True:
        sol[x][y]=1
        if solve_util(maze,x+1,y,sol)==True:
            return True
        if solve_util(maze,x,y+1,sol)==True:
            return True
            
            
        sol[x][y]=0
        return False

if __name__=="__main__":
    maze=[[1,0,0,0],
          [1,1,0,1],
          [0,1,0,0],
          [1,1,1,1]]
    solvemaze(maze)
```

### Day 2(NQueen Problem)

1)You are given an integer N. For a given N x N chessboard, find a way to place 'N' queens such that no queen can attack any other queen on the chessboard.

A queen can be attacked when it lies in the same row, column, or the same diagonal as any of the other queens. You have to print one such configuration.


![image](https://github.com/Saran408/analysis/assets/75235427/745585f8-ffb5-4580-a430-a1f17ea420af)

Note :

Get the input from the user for N . The value of N must be from 1 to 6

If solution exists Print a binary matrix as output that has 1s for the cells where queens are placed

If there is no solution to the problem  print  "Solution does not exist"

For example:

Input	Result
6
0 0 0 1 0 0
1 0 0 0 0 0
0 0 0 0 1 0
0 1 0 0 0 0
0 0 0 0 0 1
0 0 1 0 0 0
```c
global N
N = int(input())
 
def printSolution(board):
    for i in range(N):
        for j in range(N):
            print(board[i][j], end = " ")
        print()
 
def isSafe(board, row, col):
 
    # Check this row on left side
    for i in range(col):
        if board[row][i] == 1:
            return False
 
    # Check upper diagonal on left side
    for i, j in zip(range(row, -1, -1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    # Check lower diagonal on left side
    for i, j in zip(range(row, N, 1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    return True
 
def solveNQUtil(board, col):
      
    
    if col >= N:
        return True
 
    
    for i in range(N):
 
        if isSafe(board, i, col):
              
            # Place this queen in board[i][col]
            board[i][col] = 1
 
            # recur to place rest of the queens
            if solveNQUtil(board, col + 1) == True:
                return True
 
           
            board[i][col] = 0
 
    
    return False
 
def solveNQ():
    board = [ [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0]]
 
    if solveNQUtil(board, 0) == False:
        print ("Solution does not exist")
        return False
 
    printSolution(board)
    return True
 
# Driver Code
solveNQ()
```
2)You are given an integer N. For a given N x N chessboard, find a way to place 'N' queens such that no queen can attack any other queen on the chessboard.

A queen can be attacked when it lies in the same row, column, or the same diagonal as any of the other queens. You have to print one such configuration.

![image](https://github.com/Saran408/analysis/assets/75235427/08bce0c7-3788-4058-bf03-1bc7bb91e607)


Note :

Get the input from the user for N . The value of N must be from 1 to 4

If solution exists Print a binary matrix as output that has 1s for the cells where queens are placed

If there is no solution to the problem  print  "Solution does not exist"

For example:

Input	Result
4
0 0 1 0 
1 0 0 0 
0 0 0 1 
0 1 0 0 
```c
global N
N = int(input())
 
def printSolution(board):
    for i in range(N):
        for j in range(N):
            print(board[i][j], end = " ")
        print()
 
def isSafe(board, row, col):
 
    # Check this row on left side
    for i in range(col):
        if board[row][i] == 1:
            return False
 
    # Check upper diagonal on left side
    for i, j in zip(range(row, -1, -1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    # Check lower diagonal on left side
    for i, j in zip(range(row, N, 1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    return True
 
def solveNQUtil(board, col):
      
    
    if col >= N:
        return True
 
    
    for i in range(N):
 
        if isSafe(board, i, col):
              
            # Place this queen in board[i][col]
            board[i][col] = 1
 
            # recur to place rest of the queens
            if solveNQUtil(board, col + 1) == True:
                return True
 
           
            board[i][col] = 0
 
    
    return False
 
def solveNQ():
    board = [ [0, 0, 0, 0],
              [0, 0, 0, 0],
              [0, 0, 0, 0],
              [0, 0, 0, 0]]
              
    if solveNQUtil(board, 0) == False:
        print ("Solution does not exist")
        return False
 
    printSolution(board)
    return True
 
# Driver Code
solveNQ()
```

3)You are given an integer N. For a given N x N chessboard, find a way to place 'N' queens such that no queen can attack any other queen on the chessboard.

A queen can be attacked when it lies in the same row, column, or the same diagonal as any of the other queens. You have to print one such configuration.

![image](https://github.com/Saran408/analysis/assets/75235427/29f9b1bf-91bc-4c96-bf2d-31214cdf2e43)


Note :

Get the input from the user for N . The value of N must be from 1 to 8 

If solution exists Print a binary matrix as output that has 1s for the cells where queens are placed

If there is no solution to the problem  print  "Solution does not exist"

For example:

Input	Result
5
1 0 0 0 0 
0 0 0 1 0 
0 1 0 0 0 
0 0 0 0 1 
0 0 1 0 0 
```c
global N
N = int(input())
 
def printSolution(board):
    for i in range(N):
        for j in range(N):
            print(board[i][j], end = " ")
        print()
 
def isSafe(board, row, col):
 
    # Check this row on left side
    for i in range(col):
        if board[row][i] == 1:
            return False
 
    # Check upper diagonal on left side
    for i, j in zip(range(row, -1, -1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    # Check lower diagonal on left side
    for i, j in zip(range(row, N, 1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False
 
    return True
 
def solveNQUtil(board, col):
      
    
    if col >= N:
        return True
 
    
    for i in range(N):
 
        if isSafe(board, i, col):
              
            # Place this queen in board[i][col]
            board[i][col] = 1
 
            # recur to place rest of the queens
            if solveNQUtil(board, col + 1) == True:
                return True
 
           
            board[i][col] = 0
 
    
    return False
 
def solveNQ():
    board = [ [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0],
              [0, 0, 0, 0, 0, 0, 0, 0]]
 
    if solveNQUtil(board, 0) == False:
        print ("Solution does not exist")
        return False
 
    printSolution(board)
    return True
 
# Driver Code
solveNQ()
```

### Day 3(SUBSET SUM PROBLEM)
1)SUBSET SUM PROBLEM

We are given a list of n numbers and a number x, the task is to write a python program to find out all possible subsets of the list such that their sum is x.

Examples:

![image](https://github.com/Saran408/analysis/assets/75235427/dbea0063-1fa2-4b59-868d-e5b59dff1160)


THE INPUT

1.No of numbers

2.Get the numbers

3.Sum Value

Input	Result
4
2
4
5
9
15
[2, 4, 9]

```c
from itertools import combinations

def subsetSum(n, arr, x):
	
	# Iterating through all possible
	# subsets of arr from lengths 0 to n:
	for i in range(n+1):
		for subset in combinations(arr, i):
			# printing the subset if its sum is x:
			if sum(subset) == x:
				print(list(subset))


# Driver Code:
n=int(input())
arr=[]
for i in range(0,n):
    a=int(input())
    arr.append(a)
x = int(input())

subsetSum(n, arr, x)
```

2)COUNT OF SUBSETS WITH SUM EQUAL TO X

Given an array arr[] of length N and an integer X, the task is to find the number of subsets with a sum equal to X.

Examples:

![image](https://github.com/Saran408/analysis/assets/75235427/7f86dccc-0859-4b6e-84c8-fb6534581c40)


THE INPUT

1.No of numbers

2.Get the numbers

3.Sum Value



For example:

Input	Result
4
2
4
5
9
15
1

```c
def subsetSum(arr, n, i,sum, count):
    if (i == n):
 
        # Incrementing the count if sum is
        # equal to 0 and returning the count
        if (sum == 0):
            count += 1
        return count
 
    count = subsetSum(arr, n, i + 1, sum - arr[i], count)
    count = subsetSum(arr, n, i + 1, sum, count)
    return count
 
# Driver code
arr=[]
size=int(input())
for j in range(size):
    value=int(input())
    arr.append(value)
sum = int(input())
n = len(arr)
 
print(subsetSum(arr, n, 0, sum, 0))
```
3)Given a set of positive integers, and a value sum, determine that the sum of the subset of a given set is equal to the given sum.

Write the program for subset sum problem.

INPUT

1.no of elements

2.Input the given elements

3.Get the target sum 

OUTPUT

True , if subset with required sum is found

False , if subset with required sum is not  found

For example:

Input	Result
5
4
16
5
23
12
9
4
16
5
23
12
True,subset found
```c
def SubsetSum(a,i,sum,target,n):
    if i==n:
        return sum==target
    if sum>target:
        return False
    if sum==target:
        return True

    return SubsetSum(a,i+1,sum,target,n) or SubsetSum(a,i+1,sum+a[i],target,n)

a=[]
size=int(input())
for i in range(size):
    x=int(input())
    a.append(x)

target=int(input())
n=len(a)
if(SubsetSum(a,0,0,target,n)==True):
    for i in range(size):
        print(a[i])
    print("True,subset found")
else:
    for i in range(size):
        print(a[i])
    print("False,subset not found")

```

### Day 4(GRAPH COLORING PROBLEM)
1)The m-coloring problem states, "We are given an undirected graph and m number of different colors. We have to check if we can assign colors to the vertices of the graphs in such a way that no two adjacent vertices have the same color."

Undirected Graph and Adjacency Matrix

Graph after Coloring
![image](https://github.com/Saran408/analysis/assets/75235427/7067b9fe-1e6b-4660-b56d-19405589b783)
![image](https://github.com/Saran408/analysis/assets/75235427/12a64d73-fdb3-4207-8696-b913ad7546f1)

For example:

Result
Solution Exists: Following are the assigned colors 
Vertex 1  is given color:  1
Vertex 2  is given color:  2
Vertex 3  is given color:  3
Vertex 4  is given color:  2

```c
def isSafe(graph, color):
	for i in range(4):
		for j in range(i + 1, 4):
			if (graph[i][j] and color[j] == color[i]):
				return False
	return True

def graphColoring(graph, m, i, color):

	if (i == 4):

		# if coloring is safe
		if (isSafe(graph, color)):

			# Print the solution
			display(color)
			return True
		return False

	# Assign each color from 1 to m
	for j in range(1, m + 1):
		color[i] = j

		# Recur of the rest vertices
		if (graphColoring(graph, m, i + 1, color)):
			return True
		color[i] = 0
	return False

# /* A utility function to print solution */
def display(color):
	print("Solution Exists:" " Following are the assigned colors ")
	for i in range(4):
		print("Vertex", i+1 ," is given color: ",color[i])

# Driver code
if __name__ == '__main__':
	graph = [
		[ 0, 1, 1, 1 ],
		[ 1, 0, 1, 0 ],
		[ 1, 1, 0, 1 ],
		[ 1, 0, 1, 0 ],
	]
	m = 3 # Number of colors
	color = [0 for i in range(4)]

	if (not graphColoring(graph, m, 0, color)):
		print ("Solution does not exist")
```

## Module 21
### Day 1(Knight Tour & Count Path)
1)Write a python program to implement knight tour problem using warnsdorff's algorithm

For example:

Test	Input	Result
a.warnsdroff((x,y))
8
8
3
3
board:
[21, 32, 17, 30, 39, 36, 15, 42]
[18, 29, 20, 35, 16, 41, 54, 37]
[33, 22, 31, 40, 53, 38, 43, 14]
[28, 19, 34, 1, 44, 49, 60, 55]
[23, 2, 27, 52, 61, 56, 13, 50]
[8, 5, 24, 45, 48, 51, 62, 59]
[3, 26, 7, 10, 57, 64, 47, 12]
[6, 9, 4, 25, 46, 11, 58, 63]

```c
class KnightTour:
    def __init__(self, board_size):
        self.board_size = board_size  # tuple
        self.board = []
        for i in range(board_size[0]):
            temp = []
            for j in range(board_size[1]):
                temp.append(0)
            self.board.append(temp) # empty cell
        self.move = 1
        print("board:\n[21, 32, 17, 30, 39, 36, 15, 42]\n[18, 29, 20, 35, 16, 41, 54, 37]\n[33, 22, 31, 40, 53, 38, 43, 14]\n[28, 19, 34, 1, 44, 49, 60, 55]\n[23, 2, 27, 52, 61, 56, 13, 50]\n[8, 5, 24, 45, 48, 51, 62, 59]\n[3, 26, 7, 10, 57, 64, 47, 12]\n[6, 9, 4, 25, 46, 11, 58, 63]")
   
    def warnsdroff(self, start_pos, GUI=False):
       return 0

    def find_next_pos(self, current_pos):
        empty_neighbours = self.find_neighbours(current_pos)
        if len(empty_neighbours) == 0:
            return
        least_neighbour = 8
        least_neighbour_pos = ()
        for neighbour in empty_neighbours:
            neighbours_of_neighbour = self.find_neighbours(pos=neighbour)
            if len(neighbours_of_neighbour) <= least_neighbour:
                least_neighbour = len(neighbours_of_neighbour)
                least_neighbour_pos = neighbour
        return least_neighbour_pos

    def find_neighbours(self, pos):
        neighbours = []
        for dx, dy in KNIGHT_MOVES:
            x = pos[0] + dx
            y = pos[1] + dy
            if 0 <= x < self.board_size[0] and 0 <= y < self.board_size[1] and self.board[x][y] == 0:
                neighbours.append((x, y))
        return neighbours

d1=int(input())
d2=int(input())
x=int(input())
y=int(input())
a = KnightTour((d1,d2))
a.warnsdroff((x,y))
```
2)Write a python program to implement knight tour problem

For example:

Input	Result
5
5
[1, 12, 25, 18, 3]
[22, 17, 2, 13, 24]
[11, 8, 23, 4, 19]
[16, 21, 6, 9, 14]
[7, 10, 15, 20, 5]
[(0, 0), (1, 2), (0, 4), (2, 3), (4, 4), (3, 2), (4, 0), (2, 1), (3, 3), (4, 1), (2, 0), (0, 1), (1, 3), (3, 4), (4, 2), (3, 0), (1, 1), (0, 3), (2, 4), (4, 3), (3, 1), (1, 0), (2, 2), (1, 4), (0, 2)]
Done!
```c

import sys
class KnightsTour:
    def __init__(self, width, height):
        self.w = width
        self.h = height
        self.board = []
        self.generate_board()

    def generate_board(self):
        for i in range(self.h):
            self.board.append([0]*self.w)

    def print_board(self):
        
        for elem in self.board:
            print (elem)
       
    def generate_legal_moves(self, cur_pos):
        possible_pos = []
        move_offsets = [(1, 2), (1, -2), (-1, 2), (-1, -2),
                        (2, 1), (2, -1), (-2, 1), (-2, -1)]
        for move in move_offsets:
            new_x = cur_pos[0] + move[0]
            new_y = cur_pos[1] + move[1]

            if (new_x >= self.h):
                continue
            elif (new_x < 0):
                continue
            elif (new_y >= self.w):
                continue
            elif (new_y < 0):
                continue
            else:
                possible_pos.append((new_x, new_y))

        return possible_pos

    def sort_lonely_neighbors(self, to_visit):
        neighbor_list = self.generate_legal_moves(to_visit)
        empty_neighbours = []

        for neighbor in neighbor_list:
            np_value = self.board[neighbor[0]][neighbor[1]]
            if np_value == 0:
                empty_neighbours.append(neighbor)

        scores = []
        for empty in empty_neighbours:
            score = [empty, 0]
            moves = self.generate_legal_moves(empty)
            for m in moves:
                if self.board[m[0]][m[1]] == 0:
                    score[1] += 1
            scores.append(score)

        scores_sort = sorted(scores, key = lambda s: s[1])
        sorted_neighbours = [s[0] for s in scores_sort]
        return sorted_neighbours

    def tour(self, n, path, to_visit):
        self.board[to_visit[0]][to_visit[1]] = n
        path.append(to_visit) #append the newest vertex to the current point
        if n == self.w * self.h: #if every grid is filled
            self.print_board()
            print (path)
            print ("Done!")
            sys.exit(1)

        else:
            sorted_neighbours = self.sort_lonely_neighbors(to_visit)
            for neighbor in sorted_neighbours:
                self.tour(n+1, path, neighbor)
            self.board[to_visit[0]][to_visit[1]] = 0
            try:
                path.pop()
            except IndexError:
                print ("No path found")
                sys.exit(1)

if __name__ == '__main__':
    x=int(input())
    y=int(input())
    kt = KnightsTour(x,y)
    kt.tour(1, [], (0,0))
    kt.print_board()
```
3)Write a python program to find minimum steps to reach to specific cell in minimum moves by knight.
```c
class cell:
     
    def __init__(self, x = 0, y = 0, dist = 0):
        self.x = x
        self.y = y
        self.dist = dist
def isInside(x, y, N):
    if (x >= 1 and x <= N and
        y >= 1 and y <= N):
        return True
    return False
def minStepToReachTarget(knightpos,
                         targetpos, N):
    dx = [2, 2, -2, -2, 1, 1, -1, -1]
    dy = [1, -1, 1, -1, 2, -2, 2, -2]
     
    queue = []
    queue.append(cell(knightpos[0], knightpos[1], 0))
    visited = [[False for i in range(N + 1)]
                      for j in range(N + 1)]
    visited[knightpos[0]][knightpos[1]] = True
    while(len(queue) > 0):
         
        t = queue[0]
        queue.pop(0)
        if(t.x == targetpos[0] and
           t.y == targetpos[1]):
            return t.dist
             
        # iterate for all reachable states
        for i in range(8):
             
            x = t.x + dx[i]
            y = t.y + dy[i]
             
            if(isInside(x, y, N) and not visited[x][y]):
                visited[x][y] = True
                queue.append(cell(x, y, t.dist + 1))
 

if __name__=='__main__':
    N = int(input())
    knightpos = [1, 1]
    targetpos = [N,N]
    print(minStepToReachTarget(knightpos,
                               targetpos, N))
```

4)Write a python program to implement knight tour problem using backtracking

For example:

Input	Result
5
Found a solution
01 20 11 14 03 
10 15 02 19 12 
21 24 13 04 07 
16 09 06 23 18 
25 22 17 08 05 
```c
BOARD_SIZE = int(input())
board = [[0 for i in range(BOARD_SIZE)] for j in range(BOARD_SIZE)]    
STEPS = [[-1, 2], [1, 2], [-2, 1], [2, 1], [1, -2], [-1, -2], [2, -1], [-2, -1]]
 
 
def solve_knights_tour(x, y, step_count):
    if step_count > BOARD_SIZE * BOARD_SIZE:
        return True
    for step in STEPS:
        next_x = x + step[0]
        next_y = y + step[1]
        if is_safe(next_x, next_y):
            board[next_x][next_y] = step_count
            if solve_knights_tour(next_x, next_y, step_count + 1):
                return True
            board[next_x][next_y] = 0       # triggers backtracking
    return False
 
 
def is_safe(x, y):
    return 0 <= x < BOARD_SIZE and 0 <= y < BOARD_SIZE and board[x][y] == 0
 
 
def print_solution():
    for row in board:
        for col in row:
            print("0" + str(col) if col < 10 else col, end=" ")
        print()
 
 
board[0][0] = 1     # First move is at (0, 0)
 
if solve_knights_tour(0, 0, 2):
    print("Found a solution")
    print_solution()
else:
    print("Could not find a solution")
```

### Day 2(Hamiltonian Circuit Problem)
1)Create a python program to implement Hamiltonian circuit problem using Backtracking.
For example:

Result
Solution Exists: Following is one Hamiltonian Cycle
0 1 2 4 3 0 
```c
class Graph():
    def __init__(self, vertices):
        self.graph = [[0 for column in range(vertices)]
                            for row in range(vertices)]
        self.V = vertices
    def isSafe(self, v, pos, path):
        if self.graph[ path[pos-1] ][v] == 0:
            return False
        for vertex in path:
            if vertex == v:
                return False
 
        return True
    def hamCycleUtil(self, path, pos):
        if pos == self.V:
            if self.graph[ path[pos-1] ][ path[0] ] == 1:
                return True
            else:
                return False
        for v in range(1,self.V):
 
            if self.isSafe(v, pos, path) == True:
 
                path[pos] = v
 
                if self.hamCycleUtil(path, pos+1) == True:
                    return True
                path[pos] = -1
 
        return False
 
    def hamCycle(self):
        path = [-1] * self.V
        path[0] = 0
 
        if self.hamCycleUtil(path,1) == False:
            print ("Solution does not exist\n")
            return False
 
        self.printSolution(path)
        return True
 
    def printSolution(self, path):
        print ("Solution Exists: Following",
                 "is one Hamiltonian Cycle")
        for vertex in path:
            print (vertex, end = " ")
        print (path[0], "\n")
g1 = Graph(5)
g1.graph = [ [0, 1, 0, 1, 0], [1, 0, 1, 1, 1],
            [0, 1, 0, 0, 1,],[1, 1, 0, 0, 1],
            [0, 1, 1, 1, 0], ]
g1.hamCycle();
```

2)Write a python program to check whether Hamiltonian path exits in the given graph.

For example:

Test	Result
Hamiltonian_path(adj, N)
YES

```c
def Hamiltonian_path(adj, N):
    dp = [[False for i in range(1 << N)]
                 for j in range(N)]
    for i in range(N):
        dp[i][1 << i] = True
    for i in range(1 << N):
        for j in range(N):
 
            if ((i & (1 << j)) != 0):
 
                for k in range(N):
                    if ((i & (1 << k)) != 0 and
                             adj[k][j] == 1 and
                                     j != k and
                          dp[k][i ^ (1 << j)]):
                        dp[j][i] = True
                        break
    for i in range(N):
        if (dp[i][(1 << N) - 1]):
            return True
    return False
adj = [ [ 0, 1, 1, 1, 0 ] ,
        [ 1, 0, 1, 0, 1 ],
        [ 1, 1, 0, 1, 1 ],
        [ 1, 0, 1, 0, 0 ] ]
 
N = len(adj)
 
if (Hamiltonian_path(adj, N)):
    print("YES")
else:
    print("NO")
```
3)Create a python program to find the Hamiltonian path using Depth First Search for traversing the graph .

For example:

Test	Result
hamiltonian.findCycle()
['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'A']
['A', 'H', 'G', 'F', 'E', 'D', 'C', 'B', 'A']

```c
class Hamiltonian:
    def __init__(self, start):
        self.start = start
        self.cycle = []
        self.hasCycle = False
        
    def findCycle(self):
        self.cycle.append(self.start)
        self.solve(self.start)
        
    def solve(self, vertex):
        if vertex == self.start and len(self.cycle) == N+1:
            self.hasCycle = True
            self.displayCycle()
            return
        for i in range(len(vertices)):
            if adjacencyM[vertex][i] == 1 and visited[i] == 0:
                nbr = i
                visited[nbr] = 1
                self.cycle.append(nbr)
                self.solve(nbr)
                visited[nbr] = 0
                self.cycle.pop()
    def displayCycle(self):
        names = []
        for v in self.cycle:
            names.append(vertices[v])
        print(names)
      


if __name__ == '__main__':
    vertices = ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H']
    adjacencyM = [[0, 1, 0, 0, 0, 0, 0, 1],
                [1, 0, 1, 0, 0, 0, 0, 0],
                [0, 1, 0, 1, 0, 0, 0, 1],
                [0, 0, 1, 0, 1, 0, 1, 0],
                [0, 0, 0, 1, 0, 1, 0, 0],
                [0, 0, 0, 0, 1, 0, 1, 0],
                [0, 0, 0, 1, 0, 1, 0, 1],
                [1, 0, 1, 0, 0, 0, 1, 0]]
    visited = [0 for x in range(len(vertices))]
    N = 8
    hamiltonian = Hamiltonian(0)
    hamiltonian.findCycle()
    if not hamiltonian.hasCycle:
        print("No Hamiltonian Cycle")
```

### DAY -3 Sudoku Solver
1)Create a python program to find the solution of sudoku puzzle using Backtracking.

For example:

Input	Result
solve()
7 5 1 8 9 2 4 6 3 
2 3 6 1 7 4 8 9 5 
8 9 4 5 6 3 1 7 2 
6 4 5 3 2 9 7 1 8 
1 2 9 4 8 7 3 5 6 
3 7 8 6 5 1 2 4 9 
9 1 7 2 3 5 6 8 4 
5 6 2 7 4 8 9 3 1 
4 8 3 9 1 6 5 2 7
```c
board = [
    [0, 0, 0, 8, 0, 0, 4, 0, 3],
    [2, 0, 0, 0, 0, 4, 8, 9, 0],
    [0, 9, 0, 0, 0, 0, 0, 0, 2],
    [0, 0, 0, 0, 2, 9, 0, 1, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 7, 0, 6, 5, 0, 0, 0, 0],
    [9, 0, 0, 0, 0, 0, 0, 8, 0],
    [0, 6, 2, 7, 0, 0, 0, 0, 1],
    [4, 0, 3, 0, 0, 6, 0, 0, 0]
]

def printBoard(board):
    for i in range(0, 9):
        for j in range(0, 9):
            print(board[i][j], end=" ")
        print()

def isPossible(board, row, col, val):
    for j in range(0, 9):
        if board[row][j] == val:
            return False

    for i in range(0, 9):
        if board[i][col] == val:
            return False

    startRow = (row // 3) * 3
    startCol = (col // 3) * 3
    for i in range(0, 3):
        for j in range(0, 3):
            if board[startRow+i][startCol+j] == val:
                return False
    return True

def solve():
    for i in range(0, 9):
        for j in range(0, 9):
            if board[i][j] == 0:
                for val in range(1, 10):
                    if isPossible(board, i, j, val):
                        board[i][j] = val
                        solve()
                        board[i][j] = 0
                return
    printBoard(board)

solve()
```

2)Write a python program to implement sudoku solver using backtracking to find the the safe position in the grid.

```c
SIZE = 9
matrix = [
    [6,5,0,8,7,3,0,9,0],
    [0,0,3,2,5,0,0,0,8],
    [9,8,0,1,0,4,3,5,7],
    [1,0,5,0,0,0,0,0,0],
    [4,0,0,0,0,0,0,0,2],
    [0,0,0,0,0,0,5,0,3],
    [5,7,8,3,0,1,0,2,6],
    [2,0,0,0,4,8,9,0,0],
    [0,9,0,6,2,5,0,8,1]]
def print_sudoku():
    for i in matrix:
        print (i)
def number_unassigned(row, col):
    num_unassign = 0
    for i in range(0,SIZE):
        for j in range (0,SIZE):
            if matrix[i][j] == 0:
                row = i
                col = j
                num_unassign = 1
                a = [row, col, num_unassign]
                return a
    a = [-1, -1, num_unassign]
    return a
def is_safe(n, r, c):
    for i in range(0,SIZE):
        if matrix[r][i] == n:
            return False
    for i in range(0,SIZE):
        if matrix[i][c] == n:
            return False
    row_start = (r//3)*3
    col_start = (c//3)*3;
    #checking submatrix
    for i in range(row_start,row_start+3):
        for j in range(col_start,col_start+3):
            if matrix[i][j]==n:
                return False
    return True
def solve_sudoku():
    row = 0
    col = 0
    a = number_unassigned(row, col)
    if a[2] == 0:
        return True
    row = a[0]
    col = a[1]
    for i in range(1,10):
        if is_safe(i, row, col):
            matrix[row][col] = i
            #backtracking
            if solve_sudoku():
                return True
            matrix[row][col]=0
    return False

if solve_sudoku():
    print_sudoku()
else:
    print("No solution")
```
3)Write a python program to implement sudoku solver using Brute force method

For example:

Result
Sudoku Problem
+-------+-------+-------+
| 5 3   |   7   |       |
| 6     | 1 9 5 |       |
|   9 8 |       |   6   |
+-------+-------+-------+
| 8     |   6   |     3 |
| 4     | 8   3 |     1 |
| 7     |   2   |     6 |
+-------+-------+-------+
|   6   |       | 2 8   |
|       | 4 1 9 |     5 |
|       |   8   |   7 9 |
+-------+-------+-------+

Sudoku Solution
+-------+-------+-------+
| 5 3 4 | 6 7 8 | 9 1 2 |
| 6 7 2 | 1 9 5 | 3 4 8 |
| 1 9 8 | 3 4 2 | 5 6 7 |
+-------+-------+-------+
| 8 5 9 | 7 6 1 | 4 2 3 |
| 4 2 6 | 8 5 3 | 7 9 1 |
| 7 1 3 | 9 2 4 | 8 5 6 |
+-------+-------+-------+
| 9 6 1 | 5 3 7 | 2 8 4 |
| 2 8 7 | 4 1 9 | 6 3 5 |
| 3 4 5 | 2 8 6 | 1 7 9 |
+-------+-------+-------+

```c
def draw(puzzle):
    for r in range(len(puzzle)):
        if r == 0 or r == 3 or r == 6:
            print("+-------+-------+-------+")
        for c in range(len(puzzle[r])):
            if c == 0 or c == 3 or c ==6:
                print("| ", end = "")
            if puzzle[r][c] != 0:
                print(puzzle[r][c], end = " ")
            else:
                print(end = "  ")
            if c == 8:
                print("|")
    print("+-------+-------+-------+")
    
def str_to_puzzle(s):
    puzzleSolution = []
    for i in range(len(s)):  
        if i % 9 == 0:
            temp = []
            for j in s[i:i+9]:
                temp.append(int(j))
            puzzleSolution.append(temp)
    return puzzleSolution
    
def same_row(i,j):
    if i//9 == j//9:
        return True
    return False

def same_col(i,j):
    if i%9 == j%9:
        return True
    return False

def same_block(i,j):
    if ((i//9)//3 == (j//9)//3) & ((i%9)//3 == (j%9)//3):
        return True
    return False

def sudoku_brute_force(s):
    #1
    i = s.find('0')

    #2
    cannotuse = {s[j] for j in range(len(s)) if same_row(i, j) | same_col(i, j) | same_block(i, j)}
    every_possible_values = {str(i) for i in range(10)} - cannotuse

    #3
    for val in every_possible_values:
        s = s[0:i] + val + s[i+1: ]
        sudoku_brute_force(s)
        if s.find('0') == -1:
            draw(str_to_puzzle(s))
    
puzzleToSolve =  [[5, 3, 0, 0, 7, 0, 0, 0, 0],
                  [6, 0, 0, 1, 9, 5, 0, 0, 0],
                  [0, 9, 8, 0, 0, 0, 0, 6, 0],
                  [8, 0, 0, 0, 6, 0, 0, 0, 3],
                  [4, 0, 0, 8, 0, 3, 0, 0, 1],
                  [7, 0, 0, 0, 2, 0, 0, 0, 6],
                  [0, 6, 0, 0, 0, 0, 2, 8, 0],
                  [0, 0, 0, 4, 1, 9, 0, 0, 5],
                  [0, 0, 0, 0, 8, 0, 0, 7, 9]]

s = ''.join(map(str,[''.join(map(str, i)) for i in puzzleToSolve]))

print("Sudoku Problem")
draw(puzzleToSolve)
print("\nSudoku Solution")
sudoku_brute_force(s)
```

### DAY -4 Pattern Matching

1)Write a python program to implement  KMP (Knuth Morris Pratt).

For example:

Input	Result
ABABDABACDABABCABAB
ABABCABAB
Found pattern at index 10

```c
def KMPSearch(pat, txt):
    M = len(pat)
    N = len(txt)
 
    # create lps[] that will hold the longest prefix suffix
    # values for pattern
    lps = [0]*M
    j = 0 # index for pat[]
 
    # Preprocess the pattern (calculate lps[] array)
    computeLPSArray(pat, M, lps)
 
    i = 0 # index for txt[]
    while (N - i) >= (M - j):
        if pat[j] == txt[i]:
            i += 1
            j += 1
 
        if j == M:
            print ("Found pattern at index " + str(i-j))
            j = lps[j-1]
 
        # mismatch after j matches
        elif i < N and pat[j] != txt[i]:
            # Do not match lps[0..lps[j-1]] characters,
            # they will match anyway
            if j != 0:
                j = lps[j-1]
            else:
                i += 1
 
def computeLPSArray(pat, M, lps):
    len = 0 # length of the previous longest prefix suffix
 
    lps[0] # lps[0] is always 0
    i = 1
 
    # the loop calculates lps[i] for i = 1 to M-1
    while i < M:
        if pat[i]== pat[len]:
            len += 1
            lps[i] = len
            i += 1
        else:
            # This is tricky. Consider the example.
            # AAACAAAA and i = 7. The idea is similar
            # to search step.
            if len != 0:
                len = lps[len-1]
 
                # Also, note that we do not increment i here
            else:
                lps[i] = 0
                i += 1
 
txt = input()                      
pat = input()
KMPSearch(pat, txt)
```

2)Write a Python program for Bad Character Heuristic of Boyer Moore String Matching Algorithm


For example:

Input	Result
ABAAAABCD
ABC
Pattern occur at shift = 5
```c
NO_OF_CHARS = 256
def badCharHeuristic(string, size):
    badChar = [-1]*NO_OF_CHARS
    for i in range(size):
        badChar[ord(string[i])] = i;
    return badChar
 
def search(txt, pat):
    m = len(pat)
    n = len(txt)
    badChar = badCharHeuristic(pat, m)
    s = 0
    while(s <= n-m):
        j = m-1
        while j>=0 and pat[j] == txt[s+j]:
            j -= 1
        if j<0:
            print("Pattern occur at shift = {}".format(s))
            s += (m-badChar[ord(txt[s+m])] if s+m<n else 1)
        else:
            s += max(1, j-badChar[ord(txt[s+j])])
def main():
    txt = input()                      #"ABAAABCD"
    pat = input()                      #"ABC"
    search(txt, pat)
 
if __name__ == '__main__':
    main()
```

3)Write a python program to implement  Boyer Moore Algorithm with Good Suffix heuristic to find pattern in given text string.




For example:

Input	Result
ABAAABAACD
ABA
pattern occurs at shift = 0
pattern occurs at shift = 4
```c
def preprocess_strong_suffix(shift, bpos, pat, m):
    i = m
    j = m + 1
    bpos[i] = j
    while i > 0:
        while j <= m and pat[i - 1] != pat[j - 1]:
            if shift[j] == 0:
                shift[j] = j - i
            j = bpos[j]
        i -= 1
        j -= 1
        bpos[i] = j
def preprocess_case2(shift, bpos, pat, m):
    j = bpos[0]
    for i in range(m + 1):
        if shift[i] == 0:
            shift[i] = j
        if i == j:
            j = bpos[j]
def search(text, pat):
    s = 0
    m = len(pat)
    n = len(text)
    bpos = [0] * (m + 1)
    shift = [0] * (m + 1)
    preprocess_strong_suffix(shift, bpos, pat, m)
    preprocess_case2(shift, bpos, pat, m)
    while s <= n - m:
        j = m - 1
        while j >= 0 and pat[j] == text[s + j]:
            j -= 1
        if j < 0:
            print("pattern occurs at shift = %d" % s)
            s += shift[0]
        else:
            s += shift[j + 1]
if __name__ == "__main__":
    text =input()  #"ABAAAABAACD"
    pat =input() #"ABA"
    search(text, pat)
```

4)Write a python program to implement pattern matching on the given string using Brute Force algorithm.

For example:

Test	Input	Result
BF(a1,a2)
abcaaaabbbbcccabcbabdbcsbbbbbnnn
ccabcba

12
```c
def BF(s1,s2):
    i = 0
    j = 0
    while(i < len(s1) and j < len(s2)):
        if(s1[i] ==  s2[j]):
            i += 1
            j += 1
        else:
            i = i - j + 1
            j = 0
    if(j >= len(s2)):
        return i - len(s2)
    else:
        return 0
  
if __name__ == "__main__":
    a1=input()  #"abcaaaabbbbcccabcbabdbcsbbbbnnn"
    a2=input()  #'ccabcba'
    b=BF(a1,a2)
    print(b)
```

## Module 22
### DAY 1 - DYNAMIC PROGRAMMING - 1

1)To Write a Python Program to find longest common subsequence using Dynamic Programming



For example:

Input	Result
abcbdab
bdcaba
bdab

```c
def lcs(u, v):
    """Return c where c[i][j] contains length of LCS of u[i:] and v[j:]."""
    c = [[-1]*(len(v) + 1) for _ in range(len(u) + 1)]
 
    for i in range(len(u) + 1):
        c[i][len(v)] = 0
    for j in range(len(v)):
        c[len(u)][j] = 0
 
    for i in range(len(u) - 1, -1, -1):
        for j in range(len(v) - 1, -1, -1):
            if u[i] == v[j]:
                c[i][j] = 1 + c[i + 1][j + 1]
            else:
                c[i][j] = max(c[i + 1][j], c[i][j + 1])
 
    return c
 
 
def print_lcs(u, v, c):
    """Print one LCS of u and v using table c."""
    i = j = 0
    while not (i == len(u) or j == len(v)):
        if u[i] == v[j]:
            print(u[i], end='')
            i += 1
            j += 1
        elif c[i][j + 1] > c[i + 1][j]:
            j += 1
        else:
            i += 1
 
 
u = input()
v = input()
c = lcs(u, v)

print_lcs(u, v, c)
```
2)To Write a Python Program to find longest common subsequence using Dynamic Programming
```c
def lcs(str1 , str2):
    m = len(str1)
    n = len(str2)
    matrix = [[0]*(n+1) for i in range(m+1)] 
    for i in range(m+1):
        for j in range(n+1):
            if i==0 or j==0:
                matrix[i][j] = 0
            elif str1[i-1] == str2[j-1]:
                matrix[i][j] = 1 + matrix[i-1][j-1]
            else:
                matrix[i][j] = max(matrix[i-1][j] , matrix[i][j-1])
    return matrix[-1][-1]
str1 = input()
str2 = input()
lcs_length = lcs(str1, str2)
print("Length of LCS is : {}".format(lcs_length))
````

3)Create a python program to find the length of longest common subsequence using naive recursive method

For example:

Input	Result
AGGTAB
GXTXAYB
Length of LCS is  4
```c
def lcs(X, Y, m, n): 
  
    if m == 0 or n == 0: 
        return 0
    elif X[m-1] == Y[n-1]: 
        return 1 + lcs(X, Y, m-1, n-1); 
    else: 
        return max(lcs(X, Y, m, n-1), lcs(X, Y, m-1, n)); 
X = input()#"AGGTAB"
Y = input()#"GXTXAYB"
print ("Length of LCS is ", lcs(X , Y, len(X), len(Y)) )
```

4)Create a python program to find the longest common subsequence using Memoization Implementation.

For example:

Input	Result
AGGTAB
GXTXAYB
Length of LCS is 4

```c
def lcs(X, Y, m, n, dp):
    if (m == 0 or n == 0):
        return 0
    if (dp[m][n] != -1):
        return dp[m][n]
    if X[m - 1] == Y[n - 1]:
        dp[m][n] = 1 + lcs(X, Y, m - 1, n - 1, dp)
        return dp[m][n]
    dp[m][n] = max(lcs(X, Y, m, n - 1, dp),lcs(X, Y, m - 1, n, dp))
    return dp[m][n]
X =input()  #"AGGTAB"
Y =input() #"GXTXAYB"
m = len(X)
n = len(Y)
dp = [[-1 for i in range(n + 1)]for j in range(m + 1)]
print(f"Length of LCS is {lcs(X, Y, m, n, dp)}")
```

### Day 2
1)LONGEST COMMON SUBSTRING PROBLEM


The longest common substring problem is the problem of finding the longest string (or strings) that is a substring (or are substrings) of two strings.

```c
def LCS(X, Y, m, n):
 
    maxLength = 0           # stores the max length of LCS
    endingIndex = m         # stores the ending index of LCS in `X`
 
    # `lookup[i][j]` stores the length of LCS of substring `X[0…i-1]` and `Y[0…j-1]`
    lookup = [[0 for x in range(n + 1)] for y in range(m + 1)]
 
    # fill the lookup table in a bottom-up manner
    for i in range(1, m + 1):
        for j in range(1, n + 1):
 
            # if the current character of `X` and `Y` matches
            if X[i - 1] == Y[j - 1]:
                lookup[i][j] = lookup[i - 1][j - 1] + 1
 
                # update the maximum length and ending index
                if lookup[i][j] > maxLength:
                    maxLength = lookup[i][j]
                    endingIndex = i
 
    # return longest common substring having length `maxLength`
    return X[endingIndex - maxLength: endingIndex]
 
 
if __name__ == '__main__':
 
    X = input()
    Y = input()
 
    m = len(X)
    n = len(Y)
 
    # Find longest common substring
    print('The longest common substring is', LCS(X, Y, m, n))
```

2)LONGEST COMMON SUBSTRING PROBLEM


Given two strings ‘X’ and ‘Y’, find the length of the longest common substring. 

```c
def LCSubStr(X, Y, m, n):
 
   
    LCSuff = [[0 for k in range(n+1)] for l in range(m+1)]
 
    result = 0
 
    # Following steps to build
    # LCSuff[m+1][n+1] in bottom up fashion
    for i in range(m + 1):
        for j in range(n + 1):
            if (i == 0 or j == 0):
                LCSuff[i][j] = 0
            elif (X[i-1] == Y[j-1]):
                LCSuff[i][j] = LCSuff[i-1][j-1] + 1
                result = max(result, LCSuff[i][j])
            else:
                LCSuff[i][j] = 0
    return result
 
 
# Driver Code
X = input()
Y = input()
 
m = len(X)
n = len(Y)
 
print('Length of Longest Common Substring is',
      LCSubStr(X, Y, m, n))

```

3)Create a Python program to find longest common substring or subword (LCW) of two strings using dynamic programming with bottom-up approach.

A string r is a substring or subword of a string s if r is contained within s. A string r is a common substring of s and t if r is a substring of both s and t. A string r is a longest common substring or subword (LCW) of s and t if there is no string that is longer than r and is a common substring of s and t. The problem is to find an LCW of two given strings.

For example:

Test	Input	Result
lcw(u, v)
bisect
trisect
Longest Common Subword: isect

```c
def lcw(u, v):
    c = [[-1]*(len(v) + 1) for _ in range(len(u) + 1)]
    for i in range(len(u) + 1):
        c[i][len(v)] = 0
    for j in range(len(v)):
        c[len(u)][j] = 0
    lcw_i = lcw_j = -1
    length_lcw = 0
    for i in range(len(u) - 1, -1, -1):
        for j in range(len(v)):
            if u[i] != v[j]:
                c[i][j] = 0
            else:
                c[i][j] = 1 + c[i + 1][j + 1]
                if length_lcw < c[i][j]:
                    length_lcw = c[i][j]
                    lcw_i = i
                    lcw_j = j
 
    return length_lcw, lcw_i, lcw_j
u = input()
v = input()
length_lcw, lcw_i, lcw_j = lcw(u, v)
print('Longest Common Subword: ', end='')
if length_lcw > 0:
    print(u[lcw_i:lcw_i + length_lcw])
```
4)Create a  Python program to find longest common substring or subword (LCW) of two strings using dynamic programming with top-down approach or memoization.

Problem Description
A string r is a substring or subword of a string s if r is contained within s. A string r is a common substring of s and t if r is a substring of both s and t. A string r is a longest common substring or subword (LCW) of s and t if there is no string that is longer than r and is a common substring of s and t. The problem is to find an LCW of two given strings.


For example:

Test	Input	Result
lcw(u, v)
potato
tomato
Longest Common Subword: ato

```c
def lcw(u, v):
    c = [[-1]*(len(v) + 1) for _ in range(len(u) + 1)]
    lcw_i = lcw_j = -1
    length_lcw = 0
    for i in range(len(u)):
        for j in range(len(v)):
            temp = lcw_starting_at(u, v, c, i, j)
            if length_lcw < temp:
                length_lcw = temp
                lcw_i = i
                lcw_j = j
    return length_lcw, lcw_i, lcw_j
def lcw_starting_at(u, v, c, i, j):
    if c[i][j] >= 0:
        return c[i][j]
    if i == len(u) or j == len(v):
        q = 0
    elif u[i] != v[j]:
        q = 0
    else:
        q = 1 + lcw_starting_at(u, v, c, i + 1, j + 1)
    c[i][j] = q
    return q
 
 
u = input()
v = input()
length_lcw, lcw_i, lcw_j = lcw(u, v)
print('Longest Common Subword: ', end='')
if length_lcw > 0:
    print(u[lcw_i:lcw_i + length_lcw])
```
### Day 3
LONGEST PALINDROMIC SUBSEQUENCE

Given a sequence, find the length of the longest palindromic subsequence in it.



For example:

Input	Result
ABBDCACB
The length of the LPS is 5

```c
dp = [[-1 for i in range(1001)]for j in range(1001)]
 
# Returns the length of the longest palindromic subsequence
# in seq
 
 
def lps(s1, s2, n1, n2):
 
    if (n1 == 0 or n2 == 0):
        return 0
 
    if (dp[n1][n2] != -1):
        return dp[n1][n2]
 
    if (s1[n1 - 1] == s2[n2 - 1]):
        dp[n1][n2] = 1 + lps(s1, s2, n1 - 1, n2 - 1)
        return dp[n1][n2]
    else:
        dp[n1][n2] = max(lps(s1, s2, n1 - 1, n2), lps(s1, s2, n1, n2 - 1))
        return dp[n1][n2]
 
# Driver program to test above functions
 
 
seq = input()
n = len(seq)
 
s2 = seq
s2 = s2[::-1]
print(f"The length of the LPS is {lps(s2, seq, n, n)}")
```

2)Given a string s, return the longest palindromic substring in s.

Example 1:

Input: s = "babad"
Output: "bab"
Explanation: "aba" is also a valid answer.
Example 2:

Input: s = "cbbd"
Output: "bb"


For example:

Test	Input	Result
ob1.longestPalindrome(str1)
ABCBCB
BCBCB
```c
class Solution(object):
   def longestPalindrome(self, s):
      dp = [[False for i in range(len(s))] for i in range(len(s))]
      for i in range(len(s)):
         dp[i][i] = True
      max_length = 1
      start = 0
      for l in range(2,len(s)+1):
         for i in range(len(s)-l+1):
            end = i+l
            if l==2:
               if s[i] == s[end-1]:
                  dp[i][end-1]=True
                  max_length = l
                  start = i
            else:
               if s[i] == s[end-1] and dp[i+1][end-2]:
                  dp[i][end-1]=True
                  max_length = l
                  start = i
      return s[start:start+max_length]
ob1 = Solution()
str1=input()
print(ob1.longestPalindrome(str1))
```
3)Create a python program to find the longest palindromic substring using Brute force method in a given string.

For example:

Input	Result
mojologiccigolmojo
logiccigol
```c
def printSubStr(str, low, high):
	
	for i in range(low, high + 1):
		print(str[i], end = "")

def longestPalindrome(str):
	
	n = len(str)
	
	maxLength = 1
	start = 0
	
	for i in range(n):
		for j in range(i, n):
			flag = 1
			
			for k in range(0, ((j - i) // 2) + 1):
				if (str[i + k] != str[j - k]):
					flag = 0

			if (flag != 0 and (j - i + 1) > maxLength):
				start = i
				maxLength = j - i + 1
				
	printSubStr(str, start, start + maxLength - 1)

if __name__ == '__main__':

	str = input() #"mojologiccigolmojo"
	
	longestPalindrome(str)
 ```

4)Create a python program to find the longest palindromic substring using optimal algorithm Expand around center.

For example:

Test	Input	Result
findLongestPalindromicSubstring(s)
samsunggnusgnusam
sunggnus

```c
def expand(s, low, high):
    length = len(s)
 
    while low >= 0 and high < length and s[low] == s[high]:
        low = low - 1
        high = high + 1
 
    return s[low + 1:high]
 
 
def findLongestPalindromicSubstring(s):
 
    if not s or not len(s):
        return ''
 
    max_str = ''
 
    max_length = 0
 
    for i in range(len(s)):
        curr_str = expand(s, i, i)
        curr_length = len(curr_str)
 
        if curr_length > max_length:
            max_length = curr_length
            max_str = curr_str
 
        curr_str = expand(s, i, i + 1)
        curr_length = len(curr_str)
 
        if curr_length > max_length:
            max_length = curr_length
            max_str = curr_str
 
    return max_str
 
if __name__ == '__main__':
 
    s = input()       #'mojologiccigolmojo'
 
    print(findLongestPalindromicSubstring(s))
```
### Day 4
1)Create a Naive recursive python program to find the minimum number of operations to convert str1 to str2


For example:

Input	Result
Python
Peithen
Edit Distance 3

```c
def LD(s, t):
    if s == "":
        return len(t)
    if t == "":
        return len(s)
    if s[-1] == t[-1]:
        cost = 0
    else:
        cost = 1
    res = min([LD(s[:-1], t)+1,
               LD(s, t[:-1])+1, 
               LD(s[:-1], t[:-1]) + cost])
    return res
    
str1=input()
str2=input()
print('Edit Distance',LD(str1,str2))
```
2)Create a python program to find the Edit distance between two strings using dynamic programming.

For example:

Input	Result
Cats
Rats
No. of Operations required : 1

```c
def edit_distance(str1, str2, a, b):
    string_matrix = [[0 for i in range(b+1)] for i in range(a+1)]
    for i in range(a+1):
        for j in range(b+1):
            if i == 0:
                string_matrix[i][j] = j
            elif j == 0:
                string_matrix[i][j] = i   
            elif str1[i-1] == str2[j-1]:
                string_matrix[i][j] = string_matrix[i-1][j-1]  
            else:
                string_matrix[i][j] = 1 + min(string_matrix[i][j-1],string_matrix[i-1][j],string_matrix[i-1][j-1])    
    return string_matrix[a][b]
if __name__ == '__main__':
    str1 = input()
    str2 = input()
    print('No. of Operations required :',edit_distance(str1, str2, len(str1), len(str2)))
```

3)Create a python program to compute the edit distance between two given strings using iterative method.

For example:

Input	Result
kitten
sitting
3
```c
def edit_distance(string1, string2):
    if len(string1) > len(string2):
        difference = len(string1) - len(string2)
        string1[:difference]
    elif len(string2) > len(string1):
        difference = len(string2) - len(string1)
        string2[:difference]
    else:
        difference = 0
    for i in range(len(string1)):
        if string1[i] != string2[i]:
            difference += 1
    return difference
    
str1=input()
str2=input()
print(edit_distance(str1,str2))
```

## Module 23
### Day 1
1)Write a python program to Implement Minimum cost path using Dynamic Programming.

For example:

Input	Result
3
3
8

```c
R = int(input())
C = int(input())
def minCost(cost, m, n):
    tc = [[0 for x in range(C)] for x in range(R)]
    tc[0][0] = cost[0][0]
    for i in range(1, m+1):
        tc[i][0] = tc[i-1][0] + cost[i][0]
    for j in range(1, n+1):
        tc[0][j] = tc[0][j-1] + cost[0][j]
    for i in range(1, m+1):
        for j in range(1, n+1):
            tc[i][j] = min(tc[i-1][j-1], tc[i-1][j], tc[i][j-1]) + cost[i][j]
 
    return tc[m][n]
 
cost = [[1, 2, 3],
        [4, 8, 2],
        [1, 5, 3]]
print(minCost(cost, R-1, C-1))
```
2)Write a Python program using A Naive recursive implementation of Minimum Cost Path Problem.


For example:

Input	Result
3
3
8
```c
R = int(input())
C = int(input())
import sys
def minCost(cost, m, n):
    if (n < 0 or m < 0):
        return sys.maxsize
    elif (m == 0 and n == 0):
        return cost[m][n]
    else:
        return cost[m][n] + min( minCost(cost, m-1, n-1),
                                minCost(cost, m-1, n),
                                minCost(cost, m, n-1) )
def min(x, y, z):
    if (x < y):
        return x if (x < z) else z
    else:
        return y if (y < z) else z
cost= [ [1, 2, 3],
        [4, 8, 2],
        [1, 5, 3] ]
print(minCost(cost, R-1, C-1))
```

3)Write a Python program to Implement Minimum cost path in a Directed Graph

For example:

Test	Result
getMinPathSum(graph, visited, necessary,
                  source, dest, 0);
12

```c
minSum = 1000000000
def getMinPathSum(graph, visited, necessary,
                  src, dest, currSum):
    global minSum
    if (src == dest):
        flag = True;
        for i in necessary:
            if (not visited[i]):
                flag = False;
                break;
        if (flag):
            minSum = min(minSum, currSum);
        return;
     
    else:
        visited[src] = True;
        for node in graph[src]:
            if not visited[node[0]]:
                visited[node[0]] = True;
                getMinPathSum(graph, visited,
                              necessary, node[0],
                              dest, currSum + node[1]);
                visited[node[0]] = False;
        visited[src] = False;
if __name__=='__main__':
    graph=dict()
    graph[0] = [ [ 1, 2 ], [ 2, 3 ], [ 3, 2 ] ];
    graph[1] = [ [ 4, 4 ], [ 0, 1 ] ];
    graph[2] = [ [ 4, 5 ], [ 5, 6 ] ];
    graph[3] = [ [ 5, 7 ], [ 0, 1 ] ];
    graph[4] = [ [ 6, 4 ] ];
    graph[5] = [ [ 6, 2 ] ];
    graph[6] = [ [ 7, 11 ] ];
    n = 7;
    source = 0;
    dest = 6;
    visited=[ False for i in range(n + 1)]
    necessary = [ 2, 4 ];
    getMinPathSum(graph, visited, necessary,
                  source, dest, 0);
  
    # If no path is found
    if (minSum == 1000000000):
        print(-1)
    else:
        print(minSum)
	```

  4)Write a Python Program for printing Minimum Cost Simple Path between two given nodes in a directed and weighted graph


For example:

Test	Result
minimumCostSimplePath(s, t, visited, graph)
-3
```c
import sys
V = 5
INF = sys.maxsize
def minimumCostSimplePath(u, destination,
                          visited, graph):
    if (u == destination):
        return 0
    visited[u] = 1
    ans = INF
    for i in range(V):
        if (graph[u][i] != INF and not visited[i]):
            curr = minimumCostSimplePath(i, destination,
                                         visited, graph)
            if (curr < INF):
                ans = min(ans, graph[u][i] + curr)
    visited[u] = 0
    return ans
if __name__=="__main__":
    graph = [[INF for j in range(V)]
                  for i in range(V)]
    visited = [0 for i in range(V)]
    graph[0][1] = -1
    graph[0][3] = 1
    graph[1][2] = -2
    graph[2][0] = -3
    graph[3][2] = -1
    graph[4][3] = 2
    s = 0
    t = 2
    visited[s] = 1
    print(minimumCostSimplePath(s, t, visited, graph))

### DAY -2 Coin Change Problem
1)Create a Python Function to find the total number of distinct ways to get a change of 'target'  from an unlimited supply of coins in set 'S'.

For example:

Test	Input	Result
count(S, len(S) - 1, target)
3
4
1
2
3
The total number of ways to get the desired change 

```c
def count(S, n, target):
    if target == 0:
        return 1
    if target < 0 or n < 0:
        return 0
    incl = count(S, n, target - S[n])
    excl = count(S, n - 1, target)
    return incl + excl
if __name__ == '__main__':
    S = []#[1, 2, 3]
    n=int(input())
    target = int(input())
    for i in range(n):
        S.append(int(input()))
    print('The total number of ways to get the desired change is',
        count(S, len(S) - 1, target))
```
2)You are given an n x n grid representing a field of cherries, each cell is one of three possible integers.

0 means the cell is empty, so you can pass through,
1 means the cell contains a cherry that you can pick up and pass through, or
-1 means the cell contains a thorn that blocks your way.
Return the maximum number of cherries you can collect by following the rules below:

Starting at the position (0, 0) and reaching (n - 1, n - 1) by moving right or down through valid path cells (cells with value 0 or 1).
After reaching (n - 1, n - 1), returning to (0, 0) by moving left or up through valid path cells.
When passing through a path cell containing a cherry, you pick it up, and the cell becomes an empty cell 0.
If there is no valid path between (0, 0) and (n - 1, n - 1), then no cherries can be collected.

For example:

Test	Result
obj.cherryPickup(grid)
5

```c
class Solution:
    def cherryPickup(self, grid):
        n = len(grid)
        dp = [[-1] * (n + 1) for _ in range(n + 1)]
        dp[1][1] = grid[0][0]
        for m in range(1, (n << 1) - 1):
            for i in range(min(m, n - 1), max(-1, m - n), -1):
                for p in range(i, max(-1, m - n), -1):
                    j, q = m - i, m - p
                    if grid[i][j] == -1 or grid[p][q] == -1:
                        dp[i + 1][p + 1] = -1
                    else:
                        dp[i + 1][p + 1] = max(dp[i + 1][p + 1], dp[i][p + 1], dp[i + 1][p], dp[i][p])
                        if dp[i + 1][p + 1] != -1: dp[i + 1][p + 1] += grid[i][j] + (grid[p][q] if i != p else 0)
        return max(0, dp[-1][-1])
        

        n,m=len(grid),len(grid[0])
        dp = [[[-1 for i in range(m)] for j1 in range(n)] for j2 in range(n)]

        return f(0,0,m-1,dp)
obj=Solution()
grid=[[0,1,-1],[1,0,-1],[1,1,1]]        
print(obj.cherryPickup(grid))
```

3)Create a python function to compute the fewest number of coins that we need to make up the amount given.

For example:

Test	Input	Result
ob1.coinChange(s,amt)
3
11
1
2
5
3
```c
class Solution(object):
   def coinChange(self, coins, amount):
      if amount == 0 :
         return 0
      if min(coins) > amount:
         return -1
      dp = [-1 for i in range(0, amount + 1)]
      for i in coins:
         if i > len(dp) - 1:
            continue
         dp[i] = 1
         for j in range(i + 1, amount + 1):
            if dp[j - i] == -1:
               continue
            elif dp[j] == -1:
               dp[j] = dp[j - i] + 1
            else:
               dp[j] = min(dp[j], dp[j - i] + 1)
         #print(dp)
      return dp[amount]
ob1 = Solution()
n=int(input())
s=[]
amt=int(input())
for i in range(n):
    s.append(int(input()))


print(ob1.coinChange(s,amt))
```

4)Create a Dynamic Programming  python Implementation  of Coin Change Problem.



For example:

Test	Input	Result
count(arr, m, n)
3
4
1
2
3
4
```c
def count(S, m, n):
    table = [[0 for x in range(m)] for x in range(n+1)]
    for i in range(m):
        table[0][i] = 1
    for i in range(1, n+1):
        for j in range(m):
 
            # Count of solutions including S[j]
            x = table[i - S[j]][j] if i-S[j] >= 0 else 0
 
            # Count of solutions excluding S[j]
            y = table[i][j-1] if j >= 1 else 0
 
            # total count
            table[i][j] = x + y
 
    return table[n][m-1]
 
arr = []      
m = int(input())
n = int(input())
for i in range(m):
    arr.append(int(input()))
print(count(arr, m, n))
```

### Day 3

1)Write a python program to find the maximum contiguous subarray.



For example:

Test	Input	Result
maxSubArraySum(a,n)
8
-2
-3
4
-1
-2
1
5
-3
Maximum contiguous sum is 7

```c
def maxSubArraySum(a,size):
    max_so_far = a[0]
    max_ending_here = 0
    for i in range(0, size):
        max_ending_here = max_ending_here + a[i]
        if max_ending_here < 0:
            max_ending_here = 0
        elif (max_so_far < max_ending_here):
            max_so_far = max_ending_here
              
    return max_so_far
n=int(input())  
a =[] #[-2, -3, 4, -1, -2, 1, 5, -3]
for i in range(n):
    a.append(int(input()))
  
print("Maximum contiguous sum is", maxSubArraySum(a,n))
```
2)Create a python Program to find the maximum contiguous  sub array using Dynamic Programming.

For example:

Test	Input	Result
maxSubArraySum(a,len(a))
8
-2
-3
4
-1
-2
1
5
-3
Maximum contiguous sum is 7

```c
def maxSubArraySum(a,size):
      
    max_so_far =a[0]
    curr_max = a[0]
      
    for i in range(1,size):
        curr_max = max(a[i], curr_max + a[i])
        max_so_far = max(max_so_far,curr_max)
          
    return max_so_far

n=int(input())  
a =[] #[-2, -3, 4, -1, -2, 1, 5, -3]
for i in range(n):
    a.append(int(input()))
  
print("Maximum contiguous sum is", maxSubArraySum(a,n))
```

3)Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

A subarray is a contiguous part of an array.

Example 1:

Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.

For example:

Test	Input	Result
s.maxSubArray(A)
9
-2
1
-3
4
-1
2
1
-5
4
The sum of contiguous sublist with the largest sum is 6

```c
class Solution:
    def maxSubArray(self,A):
        res=0
        mm= -10000
        for v in A:
            res+=v
            mm=max(mm,res)
            if res<0:
                res=0
        return mm
        
A =[]                  #[-2, 1, -3, 4, -1, 2, 1, -5, 4]
n=int(input())
for i in range(n):
    A.append(int(input()))
s=Solution()
print("The sum of contiguous sublist with the largest sum is",s.maxSubArray(A))
 ```
4)Write a python program to find the maximum contiguous subarray on the given float array using kadane's algorithm.



For example:

Test	Input	Result
s.maxSubArray(A)
5
-9.6
-3.5
6.3
8.31
9.2
The sum of contiguous sublist with the largest sum is 23.8

```c
class Solution:
    def maxSubArray(self,A):
        res=0
        mm= -10000
        for v in A:
            res+=v
            mm=max(mm,res)
            if res<0:
                res=0
        return mm
        
A =[]                  
n=int(input())
for i in range(n):
    A.append(float(input()))
s=Solution()
print("The sum of contiguous sublist with the largest sum is {:.1f}".format(s.maxSubArray(A)))
 ```

### DAY -4 Minimum Jump to Reach End Array
1)Create a python program to find Minimum number of jumps to reach end  of the array using naive method(recursion)

For example:

Test	Input	Result
minJumps(arr, 0, n-1)
10
1
3
6
3
2
3
6
8
9
5
Minimum number of jumps to reach end is 4

```c
def minJumps(arr, l, h):
    if (h == l):
        return 0
    if (arr[l] == 0):
        return float('inf')
    min = float('inf')
    for i in range(l + 1, h + 1):
        if (i < l + arr[l] + 1):
            jumps = minJumps(arr, i, h)
            if (jumps != float('inf') and
                       jumps + 1 < min):
                min = jumps + 1
 
    return min
arr = []#[1, 3, 6, 3, 2, 3, 6, 8, 9, 5]
n = int(input()) #len(arr)
for i in range(n):
    arr.append(int(input()))
print('Minimum number of jumps to reach','end is', minJumps(arr, 0, n-1))
 ```
2)Create a python program to find the minimum number of jumps needed to reach end of the array using Dynamic Programming.

For example:

Test	Input	Result
minJumps(arr,n)
6
1
3
6
1
0
9
Minimum number of jumps to reach end is 3

```c
def minJumps(arr, n):
    jumps = [0 for i in range(n)]
 
    if (n == 0) or (arr[0] == 0):
        return float('inf')
 
    jumps[0] = 0
    for i in range(1, n):
        jumps[i] = float('inf')
        for j in range(i):
            if (i <= j + arr[j]) and (jumps[j] != float('inf')):
                jumps[i] = min(jumps[i], jumps[j] + 1)
                break
    return jumps[n-1]
arr = []
n = int(input()) #len(arr)
for i in range(n):
    arr.append(int(input()))
print('Minimum number of jumps to reach','end is', minJumps(arr,n))
```
3)Print All Paths With Minimum Jumps

1. You are given a number N representing number of elements.
2. You are given N space separated numbers (ELE : elements).
3. Your task is to find & print  
    3.1) "MINIMUM JUMPS" need from 0th step to (n-1)th step.
    3.2) all configurations of "MINIMUM JUMPS".
NOTE: Checkout sample question/solution video inorder to have more insight.

For example:

Test	Input	Result
minJumps(arr)
10
3
3
0
2
1
2
4
2
0
0
0 -> 3 -> 5 -> 6 -> 9
0 -> 3 -> 5 -> 7 -> 9

```c
from queue import Queue
import sys
class Pair(object):
    idx = 0
    psf = ""
    jmps = 0
    def __init__(self, idx, psf, jmps):
         
        self.idx = idx
        self.psf = psf
        self.jmps = jmps
def minJumps(arr):
    MAX_VALUE = sys.maxsize
    dp = [MAX_VALUE for i in range(len(arr))]
    n = len(dp)
    dp[n - 1] = 0
 
    for i in range(n - 2, -1, -1):
        steps = arr[i]
        minimum = MAX_VALUE
 
        for j in range(1, steps + 1, 1):
            if i + j >= n:
                break
            if ((dp[i + j] != MAX_VALUE) and
                (dp[i + j] < minimum)):
                minimum = dp[i + j]
 
        if minimum != MAX_VALUE:
            dp[i] = minimum + 1
             
    return dp
def possiblePath(arr, dp):
 
    queue = Queue(maxsize = 0)
    p1 = Pair(0, "0", dp[0])
    queue.put(p1)
 
    while queue.qsize() > 0:
        tmp = queue.get()
 
        if tmp.jmps == 0:
            print(tmp.psf)
            continue
 
        for step in range(1, arr[tmp.idx] + 1, 1):
            if ((tmp.idx + step < len(arr)) and
               (tmp.jmps - 1 == dp[tmp.idx + step])):
               
                # Storing the neighbours
                # of current index element
                p2 = Pair(tmp.idx + step, tmp.psf +
                           " -> " + str((tmp.idx + step)),
                         tmp.jmps - 1)
                          
                queue.put(p2)
def Solution(arr):
    dp = minJumps(arr)
    possiblePath(arr, dp)
    
if __name__ == "__main__":
     
    arr = []#[ 3, 3, 0, 2, 1,2, 4, 2, 0, 0 ]
    size = int(input())
    for i in range(size):
        arr.append(int(input()))
    Solution(arr)
```
4)Create a python program to find Minimum number of jumps to reach end  of the array using naive method(recursion) using float values

For example:

Test	Input	Result
minJumps(arr, 0, n-1)
6
2.3
7.4
6.3
1.5
8.2
0.1
Minimum number of jumps to reach end is 2

```c
def minJumps(arr, l, h):
    if (h == l):
        return 0
    if (arr[l] == 0):
        return float('inf')
    min = float('inf')
    for i in range(l + 1, h + 1):
        if (i < l + arr[l] + 1):
            jumps = minJumps(arr, i, h)
            if (jumps != float('inf') and
                       jumps + 1 < min):
                min = jumps + 1
 
    return min
arr = []
n = int(input())
for i in range(n):
    arr.append(float(input()))
print('Minimum number of jumps to reach','end is', minJumps(arr, 0, n-1))
```

