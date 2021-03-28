コントローラー
```
package sample_sts3.controller;

import javax.servlet.http.HttpSession;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.validation.BindingResult;
import org.springframework.validation.annotation.Validated;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.ModelAttribute;
import org.springframework.web.bind.annotation.PostMapping;

import sample_sts3.form.LoginForm;


@Controller
public class SchooController {

	@Autowired
	HttpSession session;

	/**
	 * トップページの表示<br>
	 * ログイン済みの場合はログアウト画面を表示
	 * @return
	 */
	@GetMapping("/")
	public String index() {
		// ログイン状態のチェック
		String login = (String)session.getAttribute("login");
		if ("ok".equals(login)) {
			return "logout";
		} else {
			return "index";
		}
	}
	/**
	 * ログイン処理
	 * @param loginForm	ログインForm
	 * @param bindingResult	入力チェック結果
	 * @return	処理結果ページのパス
	 */
	@PostMapping("login")
	public String login(@Validated @ModelAttribute("loginForm") LoginForm loginForm,
						BindingResult bindingResult) {
		// 入力チェック
		if (bindingResult.hasErrors()) {
			return "login-ng";
		}

		// IDとパスワードのチェック
		if ("aaaa".equals(loginForm.getLoginId()) &&
			"aaaa".equals(loginForm.getLoginPassword())) {
			session.setAttribute("login", "ok");
			return "login-ok";
		} else {
			return "login-ng";
		}
	}
	/**
	 * ログアウト処理
	 * @return
	 */
	@GetMapping("logout")
	public String logout() {
		session.invalidate();
		return "index";
	}
}
```
form
```
package sample_sts3.form;

import javax.validation.constraints.NotNull;
/**
 * ログイン用Form
 */
public class LoginForm {
	@NotNull
	private String loginId;
	@NotNull
	private String loginPassword;
	/**
	 * @return loginId
	 */
	public String getLoginId() {
		return loginId;
	}
	/**
	 * @param loginId セットする loginId
	 */
	public void setLoginId(String loginId) {
		this.loginId = loginId;
	}
	/**
	 * @return loginPassword
	 */
	public String getLoginPassword() {
		return loginPassword;
	}
	/**
	 * @param loginPassword セットする loginPassword
	 */
	public void setLoginPassword(String loginPassword) {
		this.loginPassword = loginPassword;
	}
}
```
