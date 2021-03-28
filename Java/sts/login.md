```
package sample.controller;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestParam;


@Controller  // コントローラーですよ宣言
public class SampleController {
	
	@GetMapping("/") // アクセスしたときに表示するファイル
	public String index() {
		return "index";
	}
	
	@PostMapping("login") // postを受け取ったときの動作
	public String login(@RequestParam("loginId") String loginId,  // htmlのname属性と揃える
						@RequestParam("loginPassword") String loginPassword) {
		
    // 簡単なログインチェック
		if ("aaaa".equals(loginId) && "aaaa".equals(loginPassword)) {
			return "login-ok";
		} else {
			return "login-ng";
		}
	}
}
```
