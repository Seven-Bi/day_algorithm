#### Largest time
> Given an array of 4 digits, return the largest 24 hour time that can be made.
> The smallest 24 hour time is `00:00`, and the largest is `23:59`.  Starting from `00:00`, a time is larger if more time has elapsed since midnight.
> Return the answer as a string of length 5.  If no valid time can be made, return an empty string.

###### Constraints:
- arr.length == 4
- 0 <= arr[i] <= 9
---

###### Another solution - Backtracking

So instead of built-in funciton used with the preivous solution, there is another way to solve this problem backtracking.
The algorithm follows the idea 'divide and conquer' it will divide problems into sub-problems until can not be divided,
then conque each one backforwads.
so below the image will make a lot sense:

![Upstream vs Origin](https://raw.githubusercontent.com/Seven-Bi/day_algorithm/master/Img/note_2.png)

---
<pre><code>
def swap(array, i, j):
    if i != j: 
        array[i], array[j] = array[j], array[i]

def permutate(array, start): # <- 1
    if start == len(array):  
        # <- 5
        return
    for index in range(start, len(array)): # <- 2
        swap(array, index, start) # <- 3
        permutate(array, start+1) # <- 4
        swap(array, index, start) # <- 6
</code></pre>


The algorithm process will be:
    1 -> 2 -> 3 -> 4
    ...
    1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 2
    ...

Basically it will go down to the bottom then take the item at that level(horizentally) then iterate it until all the items visited. Next will track back upper level by revise `start` variable.
