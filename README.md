Merge Intervals
On this page we will learn to create a Python Program to Merge Intervals.

In this problem we have to merge all possible overlapping intervals and print them.

Input : [ [1, 3], [2, 6], [8, 10], [15, 18], [18, 20] ]
Output : [ [1, 6], [8, 10], [15, 20] ]
Explanation : In this [1,3] and [2,6] are overlapping so we’ll merge then and replace with [1,6]. [8,10] will remain same as it is not overlapping with any interval. Again as we can see [15,18] is overlapping with [18,20] there for it will be replaced by [15,20]. 
Merge Intervals in Python

Algorithm
Start
Sort the given array in Ascending order
Initialize a variable i with value zero
Run a loop while i less then l – 1 (length of array – 1)
For each iteration check if starting point or ending point of any two consecutive intervals is same then increment the value of i by 1, skip for this iteration with keyword (continue)
Initialize an empty array a
Use a for loop to iterate from arr[i][0] to 1 + arr[i+1][1] and for each iteration append it to a
Use  a for loop to iterate between arr[i][0] to 1 + arr[i+1][1] using variable n
If the variable n is in array a then initialize a list name new_pair having value minimum of arr[i][0] and arr[i+1][0] to index zero , maximum of arr[i][1] and arr[i+1][1] at index one
Assign the value of new_pair to arr[i] and arr[i+1] both
Set the value of i to zero and break the for loop
Increment the value of i by 1
Create a new array ans and append all the distinct element of arr to ans
Print ans
Python Program to Merge Intervals
Python Code
Run
def merge(arr, l):
    arr.sort()
    i = 0
    while i < l - 1:
        if arr[i][0] == arr[i + 1][0] and arr[i][1] == arr[i + 1][1]:
            i += 1
            continue
        a = []
        for n in range(arr[i][0], 1 + arr[i][1]):
            a.append(n)
        for n in range(arr[i + 1][0], 1 + arr[i + 1][1]):
            if n in a:
                new_pair = [min(arr[i][0], arr[i + 1][0]), max(arr[i][1], arr[i + 1][1])]
                arr[i] = new_pair
                arr[i + 1] = new_pair
                i = 0
                break
        i += 1
    ans = []
    for i in arr:
        if i not in ans:
            ans.append(i)
    return ans


arr = [[1, 3], [2, 6], [8, 10], [15, 18], [18, 20]]
l = len(arr)
print(merge(arr, l))
Output :
