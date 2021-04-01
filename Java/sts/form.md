controller
```
package sample_thymeleaf.controller;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.ModelAttribute;
import org.springframework.web.bind.annotation.PostMapping;

import sample_thymeleaf.form.UserForm;

@Controller
public class SampleController {

	/**
	 * トップページへのリクエスト
	 * @return user.htmlのパス
	 */
	@GetMapping("/")
	public String index() {
		// user.htmlのパスを返却する
		return "user";
	}
	/**
	 * 入力処理リクエスト
	 * @param 	ユーザ情報
	 * @return 結果画面のパス
	 */
	@PostMapping("input")
	public String input(@ModelAttribute UserForm userForm) {	// formオブジェクトを使用するとき（引き渡すときだけ) @ModelAttribute
		return "user-input";									                  // 入力された情報をuserFormにいれる
	}
}
```
form
```
package sample_thymeleaf.form;

public class UserForm {
	private String name;
	private String age;
	private String mailAddress;

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

html
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
						<form action="input" method="post">
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
html(入力された値を受け取り表示する確認画面
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
						<!-- 氏名 -->
						 // Formクラスのオブジェクトを使用するなどの意味 (th:object) コントローラー側と合わせる(userForm)
						<ul class="list-group list-group-flush" th:object="${userForm}">   
							<li class="list-group-item">
								名前：<span th:text="*{name}"></span>
							</li>
							<li class="list-group-item">
								年齢：<span th:text="*{age}"></span>
							</li>
							<li class="list-group-item">
								メールアドレス：<span th:text="*{mailAddress}"></span>
							</li>
						</ul>
					</div>
				</div>
				<a class="btn btn-block" href="/">戻る</a>
			</div>
		</div>
	</body>
</html>
```
