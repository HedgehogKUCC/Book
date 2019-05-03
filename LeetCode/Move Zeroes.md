# 283. Move Zeroes

Given an array **nums**, write a function to move all **0**'s to the end of it while
maintaining the relative order of the non-zero elements.

## Example:

> Input: [0,1,0,3,12]<br>
> Output: [1,3,12,0,0]


## Note:

- You must do this **in-place** without making a copy of the array.
- Minimize the total number of operations.

<br>

```java
package leetcode;

public class MoveZeroes {

	static int[] nums = {0,1,0,3,12};
	
	public static void moveZeroes(int[] nums) {
	
		int pos = 0;
		
		for(int i = 0 ; i < nums.length ; i++) {
		
			if(nums[i] != 0) {
			
				if(i != pos) {
				
					nums[pos] = nums[i];
					nums[i] = 0;
				}
				pos++;
			}
		}
	}
	
	public static void main(String[] args) {
	
		MoveZeroes.moveZeroes(nums);
		
		for(int num : nums) {
		
			System.out.print(num + ",");
		}
	}
}
```
