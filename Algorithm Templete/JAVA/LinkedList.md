#### LinkedList

This is mainly for common LinkedList operations.

**swap**
```Java
/*
 * [1, 2, 3, 4, 5]
 * First Part = [1, 2, 3] Second Part[4, 5]
 * After swap [4, 5, 1, 2, 3]
 */
EndOfSecondPart.next=dummy.next;
dummy.next=EndOfFirstPart.next;
EndOfFirstPart.next=null;
```

**reverse in range**
```Java
//If the range is the entire linkedlist, this will be null since that next of last element is null.
ListNode nextOfTheLastNodeInRange; 
ListNode prevNode;
ListNode currentNode = firstNodeInRange;
//Caution!!!nextNode is same as the currentNode before entering the whileloop.
ListNode nextNode = currentNode;

While(nextNode != nextOfTheLastNodeInRange){
	nextNode = currentNode.next;
	currentNode.next = prevNode;
	prevNode = currentNode;
	currentNode = nextNode;
}

//this prevNode is the new HEAD node.
return prevNode;

```