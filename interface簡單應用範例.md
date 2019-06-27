### 使用 interface 定義 車 的品牌和售價

```java
publuc interface Car
{
	String getName();
	int getPrice();
}
```

<br>

一台 BMW

```java
public class BMW
{
	@Override
	public String getName()
	{
		return "BMW";
	}
	
	@Override
	public int getPrice()
	{
		return 100000;
	}
}
```

<br>

一台 BENZ

```java
public class BENZ
{
	@Override
	public String getName()
	{
		return "BENZ";
	}
	
	@Override
	public int getPrice()
	{
		return 200000;
	}
}
```

<br>

賣車的商店

```java
public class CarShop 
{
	//商店營收
	private static int money = 0;
	
	public static int getMoney()
	{
		return money;
	}
	
	//賣車
	public void sellCar(Car car)
	{
		System.out.println("車品牌: " + car.getName() + "\t車售價: " + car.getPrice());
		
		money += car.getprice();
	}
	
	public static void main(String[] args)
	{
		//建立一間賣車商店
		CarShop cs = new CarShop();
		
		//賣了一台 BMW
		cs.sellCar(new BMW());
		cs.sellCar(new BENZ());
		
		System.out.println("商店總營收: " + CarShop.money);
	}
}
```
