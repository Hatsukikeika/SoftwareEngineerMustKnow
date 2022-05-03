#### Binary Search - O(log n)

__Note:__ 

 * Looking for First occurance is pretty much same as Looking for the Last occurance, the only difference is that ```if``` condition ```>=``` and ```>```. And also the ```if(val == target) ``` for the First occurance is located at the right part of the list while it is located at the left part for Last occurance.

 * Use ```l + (r - l) / 2``` instead of ```(l + r) / 2``` to prevent overflow.

**Looking for target element**

```java
int l = 0, r = arr.length - 1;
while(l <= r){
	int mid = l + (r - l) / 2;
	int val = arr[mid];
	if(val == target) return mid;
	if(val < target) r = mid - 1;
	else l = mid + 1;
}
```

**Looking for First occurance**

```java
int l = 0, r = arr.length - 1, oc = -1;
while(l <= r){
	int mid = l + (r - l) / 2;
	if(val >= target) {
		if(val == target) oc = mid;
		r = mid - 1;
	} else {
		l = mid + 1;
	}
}
```
**Looking for Last occurance**

```java
int l = 0, r = arr.length - 1, oc = -1;
while(l <= r){
	int mid = l + (r - l) / 2;
	if(val > target) {
		r = mid - 1;
	} else {
		if(val == target) oc = mid;
		l = mid + 1;
	}
}
```

**Looking for closest/range**

```java
int l = 0, r = arr.length - 1, oc = -1;
while(l < r - 1){
	int mid = l + (r - l) / 2;
	if(val > target) {
		r = mid;
	} else {
		l = mid;
	}
}

```