ファイルの階層
```
src-main-java-com.example.demo-Application.java
        |
        L com.example.demo.controller - TopController
        |                             L NewController
	|			      L UserController
        |
        L resources-static
                   L templates - top.html
                               L form - new.html
			       L user - user.html
``` 


TopController
```
package com.example.demo.controller;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;


@Controller
public class TopController {

	@GetMapping("/")
	public String top() {
		return "top";
	}
}

```

NewController
```
package com.example.demo.controller;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
//import org.springframework.web.servlet.ModelAndView;

@Controller
public class NewController {
	
	@RequestMapping("form/new")
	public String newPage() {
		return "/form/new";
	}
	
}
```
UserController
```
package com.example.demo.controller;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller
public class UserController {
	
	@RequestMapping("user/user")
	public String newPage() {
		return "/user/user";
	}
}
```

top.html(簡単に書いた)
```
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<meta charset="UTF-8" />
<title>toppage</title>
<body>
<h1>toppage</h1>
<a href = "new.html" th:href = "@{/form/new}">newpageへ</a>
<a href = "user.html" th:href = "@{/user/user}">userpageへ</a>
</body>
</html>
```

new.html(簡単に書いた)
```
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<meta charset="UTF-8" />
<title>toppage</title>
<body>
<h1>new</h1>
</body>
</html>
```

user.html
```
<h1>user</h1>
```
