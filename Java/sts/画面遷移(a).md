ファイルの階層
```
src-main-java-com.example.demo-Application.java
        |
        L com.example.demo.controller - TopController
        |                             L NewController
        |
        L resources-static
                   L templates - top.html
                               L form - new.html
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

top.html(簡単に書いた)
```
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<meta charset="UTF-8" />
<title>toppage</title>
<body>
<h1>toppage</h1>
<a href = "new.html" th:href = "@{/form/new}">newpageへ</a>
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
