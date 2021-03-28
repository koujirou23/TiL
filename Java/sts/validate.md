コントローラー
```
package sample_sts.controller;

import org.springframework.stereotype.Controller;
import org.springframework.validation.BindingResult;
import org.springframework.validation.annotation.Validated;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.ModelAttribute;
import org.springframework.web.bind.annotation.PostMapping;

import sample_sts.form.UserForm;


@Controller
public class SchooController {

	@GetMapping("/")
	public String index() {
		return "user";
	}

	@PostMapping("input")
	public String input(@Validated @ModelAttribute("user") UserForm userForm,  // バリデーションチェックする方法
						BindingResult bindingResult) {                          // 入力された値を格納する変数 

		System.out.println(userForm.getName());
		System.out.println(userForm.getAge());
		System.out.println(userForm.getMailAddress());

		// 入力チェック結果を確認
		if(bindingResult.hasErrors()) {   // 入力が間違い
			return "input-ng";
		} else {
			return "input-ok";
		}
	}
}
```

バリデーションチェックするform処理
```
package sample.form;

import javax.validation.constraints.Email;
import javax.validation.constraints.NotBlank;
import javax.validation.constraints.Pattern;

/**
 * ユーザ情報のFormクラス
 */
public class UserForm {
	@NotBlank
	private String name;
	@NotBlank
	@Pattern(regexp = "[0-9]*")
	private String age;
	@NotBlank
	@Email
	private String mailAddress;  //多分アドレスは@があるかどうか、正規表現はいらなそう

	/**
	 * コンストラクタ
	 * @param name
	 * @param age
	 * @param mailAddress
	 */
	public UserForm(String name, String age, String mailAddress) {
		this.name = name;
		this.age = age;
		this.mailAddress = mailAddress;
	}
	/**
	 * コンストラクタ
	 */
	public UserForm() {
	}

	/**
	 * @return name
	 */
	public String getName() {
		return name;
	}
	/**
	 * @param name セットする name
	 */
	public void setName(String name) {
		this.name = name;
	}
	/**
	 * @return age
	 */
	public String getAge() {
		return age;
	}
	/**
	 * @param age セットする age
	 */
	public void setAge(String age) {
		this.age = age;
	}
	/**
	 * @return mailAddress
	 */
	public String getMailAddress() {
		return mailAddress;
	}
	/**
	 * @param mailAddress セットする mailAddress
	 */
	public void setMailAddress(String mailAddress) {
		this.mailAddress = mailAddress;
	}
}
```
HTML
```
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<!-- 今回のサンプルで使用しているCSS（bootstrap）の読み込み -->
		<link rel="stylesheet"
			href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.2/css/bootstrap.min.css"
			integrity="sha384-Smlep5jCw/wG7hdkwQ/Z5nLIefveQRIY9nfy6xoR1uRYBtpZgI6339F5dgvm/e9B"
			crossorigin="anonymous">
		<title>user</title>
	</head>
	<body>
		<div class="login align-items-center py-5">
			<div class="container">
				<div class="row">
					<div class="col-md-9 col-lg-8 mx-auto">
						<h3 class="login-heading my-4">ユーザ情報入力</h3>
						<form action="input" name="user" method="post">
							<!-- 氏名 -->
							<div class="form-label-group">
								<label for="name">名前</label>
								<input type="text"
									id="name"
									name="name"
									class="form-control">
							</div>
							<!-- 年齢 -->
							<div class="form-label-group">
								<label for="age">年齢</label>
								<input type="text"
									id="age"
									name="age"
									class="form-control">
							</div>
							<!-- メールアドレス -->
							<div class="form-label-group">
								<label for="mailAddress">メールアドレス</label>
								<input type="text"
									id="mailAddress"
									name="mailAddress"
									class="form-control">
							</div>
							<br>
							<button
								class="btn btn-lg btn-primary btn-block btn-login font-weight-bold mb-2"
								type="submit">確認</button>
						</form>
					</div>
				</div>
			</div>
		</div>
	</body>
</html>
```
