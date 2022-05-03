#### Sliding Window - O(n)

The idea of Sliding Window is dynamically getting the optimized answer.

When the condition is not met, we keep update the track and moving the right pointer to see if the condition can be met.

When condition is met, we keep moving left pointer to narrow the window and see if the result can be optimized.

**General templete**

```java
int l = 0, r = 0, sum = 0;
while(r < arr.length){
	T object = arr[r++];
	//If there is only one possible solution
	if(Solution == true) return ans;
	//If look for the largest/smallest, and so far the condition is met, shrink from left
	if(Condition >= true && If more Conditions) l++;
	Update the ans with newest result.
}
```
