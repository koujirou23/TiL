
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

### interface
今はよくわからない
```
package service;

import java.util.ArrayList;

import entity.Member;

public interface MemberService {
	
	String greet(int i);
	
	int sumOf(int x, int y);
	
	ArrayList<Member> getAll();  // shift ctrl o でインポートできる
}
```
lmpl  
データベースとのやりとり？   
今回は使用してないけど  
```
package service;

import java.util.ArrayList;

import entity.Member;

public class MemberServiceImpl implements MemberService {

	@Override
	public String greet(int i) {
		String[] greetings = {"Good Morning", "Hello", "Good Evening"};
		return greetings[i];
	}

	@Override
	public ArrayList<Member> getAll() {
		ArrayList<Member> list = new ArrayList<>();
		Member mem1 = new Member(1, "Linda", "lind@example.com");
		Member mem2 = new Member(2, "James", "james@example.com");
		list.add(mem1);
		list.add(mem2);
		
		return list;
	}

	@Override
	public int sumOf(int x, int y) {
		int sum = 0;
		for(int i  = x; i <= y; i++) {
			sum += i;
		}
		return sum;
	}

}
```

main  
処理を書く
```
package demo;

import java.util.ArrayList;

import entity.Member;
import service.MemberServiceImpl;

public class Main {

	public static void main(String[] args) {					// 実行するメソッドなので
		MemberServiceImpl service = new MemberServiceImpl();   // インスタンス生成
		System.out.println(service.greet(2));
		
		System.out.println(service.getAll());
		ArrayList<Member> list = service.getAll();			                                 // Member list から値を取得するため　entityのmemberをimportする　
		for(Member mem : list) {														    // 拡張for文 取り出す値を先に記述
			System.out.println(mem.getId() + "," + mem.getName() + "," + mem.getEmail());  // 出力
		}
		
		System.out.println(service.sumOf(3, 5));
				
	}

}
```
