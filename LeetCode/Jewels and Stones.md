# 771. Jewels and Stones

<h3>

You're given Strings ***J*** representing the types of stones that are jewels,and ***S*** representing the stones you have.

Each character in ***S*** is a type of stone you have.You want to know how many of the stones you have are also jewels.


The letters in ***J*** are guaranteed distinct, and all characters in ***J*** and ***S*** are letters.Letters are case sensitive, so ***"a"*** is considered a different type of stone from ***"A"*** .

</h3>

<br>

## Example 1:

	Input: J = "aA" , S = "aAAbbbb"
	Output: 3

## Example 2:

	Input: J = "z" , S = "ZZ"
	Output: 0
	
<br>

## Note:

- ***S*** and ***J*** will consist of letters and have length at most 50 .
- The characters in ***J*** are distinct .

<br>

```java
public int numJewelsInStones(String J, String S) {

	int res = 0;
	
	Set setJ = new HashSet();
	
	for(char j : J.toCharArray())  setJ.add(j);
	
	for(char s : S.toCharArray())  if(setJ.contains(s) res++;
	
	return res;
	
}
```

<h3>

java.util.HashSet

boolean		contains( Object o )

Returns true if this set contains the specified element.

</h3>

```java
package leetcode;

import java.util.HashSet;
import java.util.Set;

public class JewelsandStones {
	
	static String J = "aA";
	static String S = "aAAbbbb";

	public static int numJewelsInStones(String J, String S) {
		
		int res = 0;
		
		Set setJ = new HashSet();
		
		for(char j : J.toCharArray()) setJ.add(j);
		
		for(char s : S.toCharArray()) if(setJ.contains(s)) res++;
		
		return res;
	}
	
	public static void main(String[] args) {
		
		System.out.println(JewelsandStones.numJewelsInStones(J, S));
			
	}
}
```

```cmd
3
```

<br>

<h3>
Compile Fail

java.lang.String

boolean		contains( CharSequence s )

Returns true if and only if this String contains the specified ***sequence*** of char values.

</h3>