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

```java
package leetcode;

public class MoveZeroes {

	static int[] nums = {0,1,0,3,12};

	public static void moveZeroes(int[] nums) {

		if(nums == null || nums.length == 0) return;
	
		int insertPos = 0;
	
		for(int num : nums) {
	
			if(num != 0)
				nums[insertPos++] = num;
		}
	
		while(insertPos < nums.length) {
	
			nums[insertPos++] = 0;
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

<br>

<h3>

insertPos++

理解 x++ 和 ++x 的不同

才能解出答案

</h3>

<br>

```java
if( 1 != 0 )
	nums[0] = 1 ;
	insertPos = 1 ;

if( 3 != 0 )
	nums[1] = 3 ;
	insertPos = 2 ;
	
if( 12 != 0 )
	nums[2] = 12 ;
	insertPos = 3 ;
	
while( 3 < 5 )
	nums[3] = 0 ;
	insertPos = 4 ;
	
while( 4 < 5 )
	nums[4] = 0 ;
	insertPos = 5 ;
```