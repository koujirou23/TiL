
###### Entityクラスとは?
データベースから取得した値をEntityクラスにつめる
```
public class Membar{
  // フィールド
  private int id; 
  private String name;
  private String email;
  
  // メソっど
  // constructor
  // getter and setter
 
 ```
 
### sample
```
package entity;

public class Member {
	
	// フィールド
	private int id;
	private String name;
	private String email;
	
	// コンストラクタ(ソースから自動作成できる)
	
	public Member() {}

	public Member(int id, String name, String email) {
		this.id = id;
		this.name = name;
		this.email = email;
	}

	// setter and getter(ソースから自動作成できる)
	
	public int getId() {
		return id;
	}

	public void setId(int id) {
		this.id = id;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public String getEmail() {
		return email;
	}

	public void setEmail(String email) {
		this.email = email;
	};
}
```
