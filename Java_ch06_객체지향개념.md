# ch06 객체지향개념

---

### ch6-2~4

```java
[클래스와 객체]
	클래스 정의 : 객체를 정의해 놓은 것.
	클래스 용도 : 객체 생성하는데 사용.

	객체 정의 : 실제로 존재하는 것. (사물 or 개념)
	객체 용도 : 객체가 가지고 있는 기능과 속성에 따라 다름

	Ex) 클래스 - 객체 관계
		제품 설계도 - 제품
		TV 설계도 - TV

[객체의 구성요소]
	실제 세계를 컴퓨터에 어떻게 넣는가? -> 분석, 관찰 -> SW화(코드로 만들기) 시키기

	다음 형태로 생깁니다.
	객체 = 속성(변수) + 기능(메서드)

ex)
class Tv {
	// 속성
	String color;   // 색상
	boolean power;  // 전원 on/off
	int channel;    // 채널

	// 메서드
	void power() {  
		power = !power;
	}
	void channelUp() {
		channel++;
	}
	void channelDown() {
		channel--;
	}
}

[객체와 인스턴스]
	객체 : 모든 인스턴스를 대표하는 일반적 용어.
	인스턴스 : 특정 클래스로부터 생성된 객체 (ex.Tv 인스턴스)

클래스 --------------> 인스턴스(객체)
(설계도)	(인스턴스화)    (제품)

Q. 클래스(설계도)는 왜 필요합니까?
-> 객체(제품)를 생성하기 위해서

Q. 객체(설계도)는 왜 필요합니까?
-> 객체(제품)를 사용하기 위해서

Q. 객체를 사용한다는 것은?
-> 객체가 가진 속성과 기능을 사용하려고
```

### ch6-5

```java
[하나의 소스파일에 여러 클래스 작성]

Hello2.java
	- public class Hello2
	- class Hello3
	: 하나의 소스파일에는 하나의 public class 만 존재합니다.
	: 하나의 소스파일에는 하나의 클래스만 작성하는 것이 바람직합니다.
	: 소스파일 이름은 public class 이름과 일치해야 합니다.

Hello2.java
	- class Hello2
	- class Hello3
	: public class가 없으면 파일명을 'Hello2.java', 'Hello3.java' 둘다 가능합니다.

잘못된 예시)
Hello2.java
	- public class Hello2
	- public class Hello3 
	: public class 2개라서 잘못됨

Hello3.java
	- public class Hello2
	- class Hello3
	: public class 명이랑 소스파일 명이랑 다름

hello2.java
	- public class Hello2
	- class Hello3
	: 대소문자 정확하게 해야합니다.
```

### ch6-6~7

```java
[객체의 생성과 사용]

[객체 생성]

클래스명 변수명;
변수명 = new 클래스명();

ex)
Tv t;
t = new Tv();

ex)짧게 작성
Tv t = new Tv();

[객체 사용]

t.channel = 7;  // 변수 사용
t.channelUp();  // 메서드 사용(호출)
System.out.println("현재 채널은" + t.channel + "입니다.");

좀 더 자세히 알아보면

Tv t;            // Tv클래스 타입의 참조변수 't'를 선언
t = new Tv();    // Tv인스턴스 생성 후, 생성된 Tv인스턴스의 주소를 t에 저장

t.channel = 7;   // Tv인스턴스의 멤버변수 channel의 값을 7로 한다.
t.channelDown(); // Tv인스턴스의 메서드 channelDown()을 호출

예제)
Tv t1 = new Tv();
Tv t2 = new Tv();
t1.channel = 7;
t2.channel = 6;  // 각 객체마다 저장공간이 생깁니다.
System.out.println(t1.channel);  // 7
System.out.println(t2.channel);  // 6
t2 = t1;  // 참조변수 t1의 값을 t2에 저장합니다.
// t2가 참조하는 객체대신 t1이 참조하는 객체로 바뀝니다
// 그러면 기존의 t2가 참조하는 객체 데이터는 어디로? -> 가비지 컬렉터(청소부)가 주기적으로 처리합니다.
System.out.println(t1.channel);  // 7
System.out.println(t2.channel);  // 7
```

### ch6-8

```java
[객체 배열]

객체 배열 == 참조변수 배열

Tv tv1, tv2, tv3 을 객체 배열로 만들면?

Tv[] tvArr = new Tv[3];  // 객체 배열 생성
tvArr[0] = new Tv();
tvArr[1] = new Tv();
tvArr[2] = new Tv();

// 여기서 중요한것! 객체 배열만 생성하고 객체를 생성 안하면 안됩니다.

-> 간단하게 만들면

Tv[] tvArr = { new Tv(), new Tv(), new Tv() };

로 줄일 수 있습니다. 

```

### ch6-9~10

```java
[클래스 정의]

클래스 == 데이터 + 함수

변수 : 하나의 데이터를 저장할 수 있는 공간
배열 : 같은 종류(타입)의 여러 데이터를 하나로 저장할 수 있는 공간
구조체 : 서로 관련된 여러 데이터(종류 관계X)를 하나로 저장할 수 있는 공간
클래스 : 서로 관련된 데이터와 함수(메서드)의 결합(구조체 + 함수)

클래스는 다음과 같이 설명 가능합니다.
	- 설계도
	- 데이터 + 함수의 결합체
	- 사용자 정의 타입(원하는 타입을 직접 만들 수 있습니다)

ex) 시간을 다루는 타입?
int hour;   // 시간
int minute; // 분
int second; // 초
// 비객체지향적인 코드

한번에 묶어서 관리할 수 있을까?

class Time {
	int hour;
	int minute;
	int second;
}

Time t = new Time(); // 객체지향적인 코드
```

### ch6-11

```java
[선언위치에 따른 변수의 종류]

class Variables {
	// 클래스 영역
	int iv;          // 인스턴스 변수
	static int cv;   // 클래스 변수(static 변수, 공유 변수)

	void method() {
		// 메서드 영역
		int lv = 0;    // 지역 변수
	}
}

- 클래스 영역에는 '선언문'만 가능합니다.
	ex) 변수선언 등
- 선언문의 순서는 상관 없습니다.
	(하지만 일반적으로 앞단에 작성)

# 언제 생성되는가?
클래스 변수 : 클래스가 메모리에 올라갈 때
인스턴스 변수 : 인스턴스(객체)가 생성되었을 때
지역 변수 : 변수 선언문이 수행되었을 때 (메서드 종료시 자동 제거)

# 클래스가 메모리에 올라갈 때는 언제를 말하는걸까? 
-> 클래스가 필요할 때
-> 객체를 만들 때

객체는 iv(인스턴스) 변수 묶음
참조변수가 없어지면 -> 가비지 콜렉터로
```