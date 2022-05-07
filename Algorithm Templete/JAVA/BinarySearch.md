### Binary Search - O(log n)

#### Looking for target element

```java
while(l <= r){
	int mid = l + (r - l) / 2;
	int val = list[mid];
	if(val == target) return mid;
	if(val < target) r = mid - 1;
	else l = mid + 1;
}
```

__Note:__ 
 * Use ```l + (r - l) / 2``` instead of ```(l + r) / 2``` to prevent overflow.

#### Looking for First occurance

```java
while(l < r){
    int mid = l + (r - l) / 2;
    if(list[mid] >= target){
        r = mid;
    } else {
        l = mid + 1; //index of l is the result
    }
}
```

__Note:__ 
 * If the ```target``` is not in the list, the index ```l``` will point to the first occurance of the next element that is bigger than ```target```
 * If the ```target``` is not in the list **AND** there is no next bigger element, the index ```l``` should equal to ```list.length```
 * It is fine to use this template to do the same task as **Looking for target element** but make sure that ```l != list.length && list[l] == target``` before returning the result.


#### Looking for Last occurance

```java
while(l < r){
    int mid = l + (r - l + 1) / 2;
    if(list[mid] <= target){
        l = mid;
    }else{
        r = mid - 1; //index of r is the result
    }
}
```

__Note:__ 
 * If the ```target``` is not in the list, the index ```r``` will point to the last occurance of the next element that is smaller than ```target```
 * If the ```target``` is not in the list **AND** there is no next smaller element, the index ```r``` should equal to ```-1```
 * It is fine to use this template to do the same task just like **Looking for target element** but make sure that ```r != -1 && list[r] == target``` before returning the result.
 * Looking for First occurance is pretty much same as Looking for the Last occurance, but be careful when looking for the last occurance, we need to use ```l + (r - l + 1) / 2``` to avoid the infinity loop.

#### Looking for closest/range

```java
while(l < r - 1){
	int mid = l + (r - l) / 2;
	if(val > target) {
		r = mid;
	} else {
		l = mid;
	}
}

```
**No Note for this template yet**