### 猛虎出柙 P.604

|Regex|描述|
|:-:|:-:|
|.|任意一個字元|
|*|任意多個字元 (包含0)|
|+|任意多個字元 (不含0)|
|?|任意0個或1個字元|
|-|範圍Range|
|\||分隔樣式|
|^|一行的開頭|
|$|一行的結尾|
|[ ]|在[]中的任意一個字元|
|[^]|非在[]中的任意一個字元|
|{n}|包含前面的字元n個|
|{n,}|包含前面的字元n個以上|
|{n,m}|包含前面的字元n個以上，m個以下。|

<br>

### 以下簡單說明正則運算式之比對樣式及Regex入門使用範例

	".": 任意一個字元
	
	[例1] "ABC." 這個字串可以表示為 "ABCD" 或 "ABC2" ...等
	
	[例2] "A.B" 表示Ａ與Ｂ之間可以有任何一個字元，所以"ACB" 或 "AZB" 皆正確
	
	======================================================================================
	
	"*": 任意多個字元
	
	[例3] "A*B" 表示Ａ與Ｂ之間可以有任意多個字元，所以 "ACB" 或 "AXYZB" 皆正確
	
	======================================================================================
	
	"[]": 在[]中的任意一個字元
	
	[例4] "ABC[XYZ]" 表示在ＡＢＣ字串後面只能是Ｘ或Ｙ或Ｚ其中一個字元。"ABCX"、"ABCY"、"ABCZ" 皆正確
	
	======================================================================================
	
	"-": 範圍 (Range)
	
	[例5] "ABC[A-F]" 表示在ＡＢＣ字串後可以再加入範圍從Ａ到Ｆ中的任意一個字元。
	
	======================================================================================
	
	"|": 分隔樣式的符號
	
	[例6] "ABC[A|ABC|1234]" 只能在ＡＢＣ加入[]內其中一種樣式。"ABCA"、"ABCABC"、"ABC1234"
	
	======================================================================================
	
	"{n,m}": 包含前面的字元n個以上，m個以下。
	
	[例7] "ABC[A-F]{2,3}" 意味著在字串 "ABC" 後面只要再加上 2 ~ 3 個範圍從 A - F 當中的字元就可以。

<br>

註冊範例

```java
    private final String SUCCESS_PATH = "register_success.view";
    private final String ERROR_PATH = "register_error.view";
    
    private final Pattern emailRegex = Pattern.compile(
        "^[_a-z0-9-]+([.][_a-z0-9-]+)*@[a-z0-9-]+([.][a-z0-9-]+)*$");

    private final Pattern passwdRegex = Pattern.compile("^\\w{8,16}$");
    
    private final Pattern usernameRegex = Pattern.compile("^\\w{1,16}$");

    protected void doPost(
            HttpServletRequest request, HttpServletResponse response)
                 throws ServletException, IOException {
        String email = request.getParameter("email");
        String username = request.getParameter("username");
        String password = request.getParameter("password");
        String password2 = request.getParameter("password2");

        List<String> errors = new ArrayList<>(); 
        if (!validateEmail(email)) {
            errors.add("未填寫郵件或格式不正確");
        }
        if(!validateUsername(username)) {
            errors.add("未填寫使用者名稱或格式不正確");
        }
        if (!validatePassword(password, password2)) {
            errors.add("請確認密碼符合格式並再度確認密碼");
        }
        
        String path;
        if(errors.isEmpty()) {
            path = SUCCESS_PATH;
            tryCreateUser(email, username, password);
        } else {
            path = ERROR_PATH;
            request.setAttribute("errors", errors);
        }

        request.getRequestDispatcher(path).forward(request, response);
    }

    private boolean validateEmail(String email) {
        return email != null && emailRegex.matcher(email).find();
    }
    
    private boolean validateUsername(String username) {
        return username != null && usernameRegex.matcher(username).find();
    }

    
    private boolean validatePassword(String password, String password2) {
        return password != null && 
               passwdRegex.matcher(password).find() && 
               password.equals(password2);
    }
```
