### Overlap Questions (Origin Leetcode 370. Range Addition)

#### This question can be re-phrase to:
Given multiple intervals and the costs of these intervals, build an array that can visualize the cost curve.

**E.g.**
Given following data
* Interval #1: Cost 3, Range [1:4]
* Interval #2: Cost 1, Range [3:5]
* Interval #3: Cost 2, Range [7:8]

The Visualized array is [0, 3, 3, 4, 4, 1, 0, 2, 2], here is they way to map the intervals onto the array:

1. Extend the array size by one (will need this later): 
[0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
2. Mark the index with cost cumulatively where each interval starts: 
[0, 3, 0, 1, 0, 0, 0, 2, 0, 0]
3. Mark the index with negative cost cumulative where each interval ends (end of range + 1): 
[0, 3, 0, 1, 0, -3, -1, 2, 0, -2]
4. Updata all element by cumulative sum：
[0, 3, 3, 4, 4, 1, 0, 2, 2, 0]
5. Exclude the last element of the array (Roll back the step 1.)
[0, 3, 3, 4, 4, 1, 0, 2, 2]

**Apply this idea to other scenario, e.g.** [Car Pooling leetcode 1094](https://leetcode.com/problems/car-pooling/)

You are given the integer capacity and an array trips where ```trips[i] = [numPassengers, from, to]``` indicates that the ith trip has ```numPassengers``` passengers and the locations to pick them up and drop them off are ```from``` and ```to``` respectively. The locations are given as the number of kilometers due east from the car's initial location.

Return true if it is possible to pick up and drop off all passengers for all the given trips, or false otherwise.

Let's say the ```trips[]``` contains the same data we used above, and the capacity of the car is 3.

Since the numbers in the mapping array are 0,1,2,3,4 and 4 is larger than 3, in this case it should return ```false```.

**Apply this idea to other scenario, e.g.** [Google OA 2019 found on leetcode discussion board](https://leetcode.com/discuss/interview-question/356520)

There are n guests who are invited to a party. The k-th guest will attend the party at time ```S[k]``` and leave the party at time ```E[k]```.

Given an integer array S and an integer array E, both of length n, return an integer denoting the minimum number of chairs you need such that everyone attending the party can sit down.

Input: ```S = [1, 2, 6, 5, 3], E = [5, 5, 7, 6, 8]```

We can build intervals from S and E, they are [1,5], [2,5], [6,7], [5,6], [3,8], since that each person only need 1 chair, the cost is a constant 1.

Do the algorithm *Note that in this case, the guest leave at ```E[k]``` not after ```E[k]```, so no need to extend the end by 1:
[0, 1, 1, 1, 0, -1, -1, -1, -1] &rarr; [0, 1, 2, 3, 3, 2, 1, 0]

We can see the max number of guests in the party at the same moment is 3, so at least 3 chairs are needed.
