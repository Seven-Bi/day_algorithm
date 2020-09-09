
#### Largest time
> Given an array of 4 digits, return the largest 24 hour time that can be made.
> The smallest 24 hour time is `00:00`, and the largest is `23:59`.  Starting from `00:00`, a time is larger if more time has elapsed since midnight.
> Return the answer as a string of length 5.  If no valid time can be made, return an empty string.

###### Constraints:
- arr.length == 4
- 0 <= arr[i] <= 9
---

###### idea of solution:

nice to have built-in func to get things easier
> for h, i, j, k in itertools.permutations(l):

filter requried info
> hour = h * 10 + i
> minute = j * 10 + k
> more filters can come through if needed

think about the base unit we calculate the time
> max_time = max(max_time, hour * 60 + minute)

last thing - get data in format 
> return "{:02d}:{:02d}".format(max_time // 60, max_time % 60)
