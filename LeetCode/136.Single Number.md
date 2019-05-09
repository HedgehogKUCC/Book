# 136. Single Number

<h3>

Given a non-empty array of integers, every element appears twice except for one. 

Find that single one.

</h3>

## Note:

- Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory ?

<br>

## Example 1:

	Input: [2,2,1]
	Output: 1
	
<br>

## Example 2:

	Input: [4,1,2,1,2]
	Output: 4

<br>

<h3>

Known that A XOR A = 0 and the XOR operator is commutative, the solution will be very straightforward.

</h3>

```java
public int singleNumber(int[] nums) {

	int result = 0;
	
	for(int i=0; i < nums.length; i++) {
	
		result ^= nums[i];
	}
	return result;
}
```

```java
public int singleNumber(int[] nums) {

	int result = 0;
	
	for(int num : nums) {
	
		result ^= num;
	}
	return result;
}
```
