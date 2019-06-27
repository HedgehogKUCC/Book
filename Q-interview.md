### 108 / 06 / 27

重點： ＤＲＹ (Don't Repeat Yourself)

從 資料庫 撈兩樣產品 來比對 "產品名稱" 和  "產品價錢"

建置 model (Product)

```java
public class Product
{
	private String name;
	private Integer price;		使用 .equals(Object o) 所以使用包覆類別 (Wrapper Class)
	
	public Product(String name, Integer price)
	{
		this.name = name;
		this.price = price;
	}
	
	public String getName()
	{
		return name;
	}
	
	public Integer getPrice()
	{
		return price;
	}
}
```

<br>

假設從 資料庫 取出的產品

`MysqlTable.java`

```java
public class MysqlTable
{
	public static void main(String[] args)
	{
		// 假設從 資料庫 取出的兩筆產品，使用 new 會給這個物件變數stack，所以 p1 和 p2 各有一個stack空間。
		Product p1 = new Product("p1","1000");
		Product p2 = new Product("p2","1000");
		
		// 使用 ＝＝ 是比較 stack(址)，而 equals 是比較 value(值)。
		Boolean b = p1.getName().equals(p2.getName()) && p1.getPrice().equals(p2.getPrice());
		
		if(b == true)
		{
			System.out.println
			(
				"產品1: " + p1.getName() + "\t價錢: " + p1.getPrice() +
				"\n產品2: " + p2.getName() + "\t價錢: " + p2.getPrice() +
				"\n產品名稱與價錢是否相同: " + b
			);
		}
		else
		{
			System.out.println
			(
				"產品1: " + p1.getName() + "\t價錢: " + p1.getPrice() +
				"\n產品2: " + p2.getName() + "\t價錢: " + p2.getPrice() +
				"\n產品名稱與價錢是否相同: " + b
			);
		}
	}
}
```
