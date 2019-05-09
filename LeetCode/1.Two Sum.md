# 1. Two Sum

<h3>

Given an array of integers,return indices of the two numbers such that they add up to a specific target.<br>		
You may assume that each input would have exactly one solution, and you may not use the same element twice.

</h3>

## Example:

	Given nums = [2, 7, 11, 15], target = 9,
	
	Because nums[0] + nums[1] = 2 + 7 = 9,
	
	return[0,1]

<br>

```java
package leetcode;

import java.util.HashMap;
import java.util.Map;

public class TwoSum {

	static int[] nums = {2,7,11,15};
	static int target = 9;
	
	public static int[] twoSum(int[] nums, int target)  {
		
		int[] result = new int[2];
		
		Map<Integer,Integer> map = new HashMap<Integer,Integer>();
		
		for(int i=0; i < nums.length; i++) {
			
			if(map.containsKey(target - nums[i])) {
				
					result[1] = i + 1;
					result[0] = map.get(target - nums[i]);
					return result;
			}
			map.put(nums[i], i + 1);
		}
		return result;
	}
	
	public static void main(String[] args)  {
		
		for(int result : TwoSum.twoSum(nums, target)) {
			
			System.out.println(result);
		}
	}
}
```

```cmd
1,
2,
```

<br>

<h3>
	
把 target 值改成 26

</h3>
	
```cmd
3,
4,
```
	
