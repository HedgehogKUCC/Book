# 344. Reverse String

Write a function that reverses a String. The input String is given as an array of characters char[].

Do not [allocate](#chi) extra space for another array, you must do this by **modifying the input array** <font color=blue>in-place</font> with O(1) extra memory.

You may assume all the characters consist of <font color=blue>printable ascii characters.</font>


## Example 1:

> Input: ["h","e","l","l","o"]<br>
> Output : ["o","l","l","e","h"]


## Exanple 2:

> Input: ["H","a","n","n","a","h"]<br>
> Output: ["h","a","n","n","a","H"]

<br>

```java
package leetcode;

public class reverseString {

	static char[] = {'h','e','l','l','o'};
	
	public void recerseString(char[] s) {
	
		for(int i=0 ; i < s.length/2 ; i++) {
			
			char tmp = s[i];
			s[i] = s[s.length-1-i];
			s[s.length-1-i] = tmp;
			
		}
	}
	
	public static void main(String[] args) {
		
		System.out.println(s);
		reverseString r = new reverseString();
		r.reverseString(s);
		System.out.println(s);
		
	}
}
```

```java
package leetcode;

public class reverseString {

	static char[] s = {'h','e','l','l','o'};
	
	public void reverseString(char[] s) {
	
		String str = "";       // Allocate extra space 分配額外空間
		
		for(int i = s.length-1 ; i >= 0 ; i--)     // Add to extra space from rear to front
			str += s[i];                           // 從後向前增加額外空間
			
		for(int i = 0 ; i < s.length ; i++)       // Set reversed 'str' into char array 's'
			s[i] = str.charAt(i);                 // 將設置反轉的字串放進陣列中
	}

	public static void main(String[] args) {
	
		reverseString r = new reverseString();
		r.reverseString(s);
		System.out.println(s);
	}
}
```

```cmd
hello
olleh
```

<h3 id=chi>allocate : 分配</h3>

