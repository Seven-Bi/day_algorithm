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
---
![Upstream vs Origin](https://raw.githubusercontent.com/Seven-Bi/day_algorithm/Img/note_2.PNG)

---
<pre><code>
def swap(array, i, j):
    if i != j: # <- 2
        array[i], array[j] = array[j], array[i]

def permutate(array, start):
    if start == len(array): # <- 3
    	# <- 5
        return

    for index in range(start, len(array)):
        swap(array, index, start) # 
        permutate(array, start+1) #  <- 1
        # here will block until return from previous recursive function
        swap(array, index, start) # <- 4 array, that's why the algorithm called backtracking
</code></pre>

For example, start from code line `<- 1`, we have [1, 2, 3] and start=1 passed in to permutate() then divide by swap -> [2, 1, 3] and all itself again, for the time being, we have array [2, 1, 3], index=0 and start=2 => next round (`horizentally`), we hit the code line `<- 1` again ready for next round, then array swaped again now is [3, 2, 1] because of index is still 0 but start was 2. Move forward it will call itself again but with start+1 will be 3 which will be hit the code line `<- 3` then return, cool one round finish, let's have a quick look.

- [1, 2, 3]	[2, 1, 3]	[3, 2, 1]

At this moment, it finally meet the code line `<- 4` it has been blocked a whole round (`horizentally`), in this line we reset the `start` to 0 and `array` (assume you already know why these values still keep same) which gives a chance to go over all possibilities with different fixed `prefix` which is `index` in same data resource `array`.

In this case, the line `<- 5` it is the gap for us to take the combines.



