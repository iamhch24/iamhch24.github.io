---
title: "[Study] Do it 자바프로그래밍 입문"
categories:
    - dev
tags:
    - dev
    - java
toc: true

---

## 1장 자바 프로그래밍 시작하기

* Java SE 1.8 설치
* 이클립스 설치

* 패키지 : 폴더 개념
* Entry Point : 시작점 :: static void main()
* print 함수 ::  System.out.println();
* () : 연산자 = 함수호출할 때 그곳으로 가라는 뜻, () 앞은 주소
  () : 연산자 = 계산식에서는 우선순위 부여
* 문자열 " " 사용
* ctrl+/ :: 주석처리
* 코드창의 글자 크기 설정 :: window>preference>General>Appearance>Colors and Fonts>Basic>Text Font>Edit 

	/*  */ 주석처리
	/** 해서 엔터를 치면 javadoc이 실행됨 : 설명문 달기
	
> src 폴더에서 .java 실행을 하면 bin 폴더에 .class 바이트 코드가 생성됨

```java
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		System.out.println("안녕 자바 \n");
	}
```

> public :: 공개, 오픈되어 있음 
> static :: 정적
> void :: 리턴값이 없음
> 자바는 무조건 클래스가 있어야 함. 모든게 클래스 안에 있어야함. 또 클래스 안에 메서드가 있어야 함.
> first class : 클래스가 가장 높음 
> 클래스 밖에 코드를 쓰면 안됨
> main()은 하나 이상 있어야 실행이 됨. :: runable class
> main()이 없으면 :: 순수클래스, 실행이 안됨

# 2장 변수와 자료형

변수의 선언과 함께 초기화를 해 준다.
선언 후 곧바로 호출(사용) 시 에러가 뜨도록 되어 있음

덧셈을 할 경우 초기화 값은 0
곱셈을 할 경우 초기화 값은 1
문자열 초기화 ""


> 컴파일 타임 상수

```Java
	final int MAX_NUM = 100;
```

> 런타임 상수

```Java
	final int ADD_NUM = add();
```

* 문자 타입 char (2바이트) 
* 정수 타입 int (4바이트) 기본형
* 실수 타입 double (8바이트) 기본형
* long을 넘어가면 숫자는 문자열로 받아서 처리한다.
* 런타임 환경에서 에러 나는 것보다 컴파일 에러가 훨씬 나음.
* 연산자(리턴값 있음, 순위중요) -> 표현식 vs 선언식
* 과거 값을 사용하고 싶을 때
num = num +1 :: 자기 자신이 들어가야 함
* shift 연산자 :: 비트수를 움직임

> 한글입력

```Java
public static void main(String[] args) throws Exception {
	byte[] str_buffer = new byte[1024];
	int value2 = System.in.read(str_buffer);
	String str = new String(str_buffer);
	System.out.println(str);
}
```
>크리스마스 트리
```Java
package loopeaxample;

public class ChristmasTree {

	public static void main(String[] args) throws Exception {
		// TODO Auto-generated method stub
		String star ="*";
		String line ="";
		for(int i= 1;i<=5;i++) {
			line ="";
			for(int j=0;j<=5-i;j++) {
				line += "  ";
			}
			System.out.println(line+star+line);
			star += " * *";
			
		}
		for(int z= 1;z<=3;z++) {
			System.out.println("         | |");
		}	
	}
}

```

# 5장 클래스와 객체

new 연사자는 heap에 메모리 할당해 줌
지역 변수는 stack에 메모리 생김
전역 변수, static 변수는 data 영역에 메모리 생김

* main() 함수를 포함한 실행 클래스를 따로 만든다

* public get/set 메서드를 사용하여 캡슐화 함.

>접근제어자
public : 외부 클래스 어디에서나 접근 가능
protected : 상속한 경우, 같은 패키지 내부에서만 접근 가능
없는 경우 : default, 같은 패키지 내부에서만 접근 가능
private : 같은 클래스 내부에서만 접근 가능

# 6장 클래스와 객체 2
* this : 자신의 메모리를 가리키는 this 

* static 변수 : 클래스에서 공통으로 사용하는 변수를 'static'변수로 선언함. static 변수는 프로그램이 실행되어 메모리에 올라갔을 때 딱 한번 메모리 공간이 할당되고 그 값은 모든 인스턴스가 공유함. 클래스에 기반한 변수라고 해서 클래스 변수라고도 함.

* 클래스 메서드 : static 변수를 위한 메서드

>싱글톤 패턴 디자인
1단계 : 생성자를 private으로 만들기
2단계 : 클래스 내부에 static으로 유일한 인스턴스 생성하기
3단계 : 외부에서 참조할 수 있는 public 메서드 만들기
4단계 : 실제로 사용하는 코드 만들기

자신의 객체를 리턴하고 싶을 때
```Java
Person returnItSelf(){
	return this;
}
```

```Java
5_000 // 5000의 숫자를 천단위자릿수 표시할 수 잇다.
```
클래스 안에서 
클래스 타입의 변수를 갖고 있으면 결합도가 높음 
그러나 매개변수(파라미터) 형태로 받아서 사용하는 인젝션 타입이 결합도를 낮추고 효율성이 더 높음.

결합도가 높으면 하나를 수정할 때 영향이 많이 해당 부분을 전부 수정해줘야 해서 유지보수가 어려움.

--> 의존성 주입이라는 개념 정리 필요

# 7장 배열과 ArrayList

```Java
final int INDEX = 10;
int[] studentIDs = new int[INDEX];
```
>다차원 배열

```Java
int[][] arr = new int[5][5];
for (int i=0; i<arr.length; i++ ) {
	for (int j=0;j<arr[i].length;j++){
		System.out.println(arr[i][j]);
	}
	System.out.println( );
}
```

>ArrayList 사용

```Java
ArrayList<Book> library = new ArrayList<Book>();
library.add(new Book("태백산맥","조정래"));
library.add(new Book("데미안","헤르만 헤세"));
library.add(new Book("어떻게 살 것인가","유시민"));
library.add(new Book("토지","박경리"));
library.add(new Book("어린왕자","생택쥐페리"));
for(Book book : library) {
	book.showBookInfo();
}
```

>향상된 for 구문

```Java
String[] strArray = {"Java","Android","C","JavaScript","Python"};
for(String lang : strArrary){
	System.out.println(lang);
}
```

* "제네릭 자료형"이라고 함. 어떤 값이 하나의 참조 자료형이 아닌 여러 참조 자료형을 사용할 수 있도록 프로그래밍하는 것을 "제네릭 프로그래밍"이라고 함.

# 9장 추상클래스
생성자를 만드는 것이 가능하지만 객체 인스턴스 생성은 불가능
추상 메서드는 바디가 없음. 상속을 받은 하위 객체에서 메서드 body를 구현함.
사용하는 이유 : 공통의 프로젝트를 시행시 먼저 디자인하는 부분으로 추상클래스를 선언하고 구현하는 것은 상속 받아 구체적인 body를 구현함
추상클래스에서 자식의 오버라이딩 개념을 implement라고 표현함
추상 메서드 선언시 파라미터 이름까지 써 줘야 함.
private이 되면 안됨. public 으로 정의
abstract 예약어를 추가해야 함.


> 추상클래스를 현업에서 사용하는 방법

```Java
(왼쪽) 추상클래스 = new 추상클래스의 자식 ();
```

> 추상클래스 vs 인터페이스

추상클래스도 클래스이기에 상속이 1개만 가능
인터페이스는 다중 상속이 가능함 (연결도 느슨함)
이와 같은 이유로 현업에서는 인터페이스를 더 많이 사용함.
클래스 다이어그램에서 클래스는 실선, 인터페이스는 점선으로 그림
인터페이스는 생성자 자체를 못 만듦.

> 이름 명명 규칙
인터페이스도 클래스 처럼 대문자로 시작하기에 구별을 위해
끝에 -able, -ible 을 붙여서 인터페이스임을 암묵적으로 명시함


> 프로그램 실행 중지

```Java
System.exit(0); // 정상 종료
System.exit(1); // 비정상 종료
```

# 11 기본 클래스

>String 클래스 정보 가져오기

```Java
package classex;

import java.lang.reflect.Constructor;
import java.lang.reflect.Field;
import java.lang.reflect.Method;

public class StringClassTest {
	public static void main(String[] args) throws ClassNotFoundException {
		Class strClass = Class.forName("java.lang.String");
		Constructor[] cons = strClass.getConstructors();
		
		for(Constructor c : cons) {
			System.out.println(c);
		}
		Field[] fields = strClass.getFields();
		for(Field f : fields) {
			System.out.println(f);
		}
		Method[] methods = strClass.getMethods();
				
		for(Method m : methods) {
			System.out.println(m);
		}
	}
}

```

# 12장 컬렉션 프레임워크

### 제네릭 <T>

> <T extends 클래스제한 >

* 제네릭 타입에서 오는 타입을 제한하기 위해 T 뒤에 extends를 설정해 준다.
* 책에서는 추상 클래스를 부모로 하는 클래스들로 제한하기 위해 extends 다음에 추상클래스로 제한해주는 것을 추천하는데
* 인터페이스 가능여부 설명이 없어서 직접 사용을 해 보니 인터페이스도 사용하는데 문제가 없었다.

```Java
package generics;
public class GenericPrinter<T extends Materialible> {
	private T material;
	public T getMaterial() {
		return material;
	}
	public void setMaterial(T material) {
		this.material = material;
	}
	public String toString() {
		return material.toString();
	}
}

package generics;
public interface Materialible {
	public void doPrinting();
	public String toString();
}

package generics;
public class GenericPrinterTest {
	public static void main(String[] args) {
		GenericPrinter<Powder> generic1 = new GenericPrinter<>();
		generic1.setMaterial(new Powder());
		System.out.println(generic1.getMaterial());
		GenericPrinter<Plastic> generic2 = new GenericPrinter<>();
		generic2.setMaterial(new Plastic());
		System.out.println(generic2.getMaterial());	
	}
}

package generics;
public class Powder implements Materialible{
	public void doPrinting() {
		System.out.println("Powder 재료로 출력합니다.");	
	}
	public String toString() {
		return "재료는 Powder 입니다.";
	}	
}

package generics;
public class Plastic implements Materialible{
	public void doPrinting() {
		System.out.println("Plastic 재료로 출력합니다.");
	}
	public String toString() {
		return "재료는 Plastic 입니다.";	
	}	
}
```

* 제네릭 메서드 :: 메서드 단위에서도 <T> 를 선언하는 것처럼 제네릭을 사용할 수 있음.
[참고1] https://velog.io/@eversong/Effective-Java-30.-%EC%9D%B4%EC%99%95%EC%9D%B4%EB%A9%B4-%EC%A0%9C%EB%84%A4%EB%A6%AD-%EB%A9%94%EC%84%9C%EB%93%9C%EB%A1%9C-%EB%A7%8C%EB%93%A4%EB%9D%BC
[참고2] https://limkydev.tistory.com/59


### 컬렉션 프레임 워크 = 자료구조(java.util.*)

컬렉션 프레임 워크에서는 Iterator 형태로 반환하여 처리할 수도 있다.

```Java
	ArrayList<Member> member = new ArrayList<>();
	member.add(new Member(1,"Karl"));
	member.add(new Member(2,"Brian"));
	Iterator<Member> iterator = member.iterator();
	while(iterator.hasNext()) {
		System.out.println(iterator.next().getMemberName());
	}
```
* Iterator는 thread 환경에서 강함, 
* Iterator는 내부적으로 index가 있기 때문에 한번 수행이 다 되면 마지막을 가리키고 있어서 다시 쓰려면 다시 초기화 해줘야 한다.




<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYyMDY1MTc4MSwyMTM4MjMxMzg0LDIwNj
czNzU5NzQsMTcxNTI1MTU3NSwyNDI4NTcxNTMsLTEwNzQ2MTUw
MDksLTE4MDMzNzcxNjIsLTExMDQwNjA2NjcsLTE3MzA0NDQyNj
YsLTEyNTExNDk0MSwtOTczMzc3MDAwLDIwMzA0Nzg1MiwxNjUx
NDQ4NDcwLDExNjk4NTIyMyw1MjU4MTU1NDAsMTMzODQ2OTE0NC
w4MTAwNjkyMDUsMTM5NDUyNjg1OCwtMjQxOTcxMDIxLDEwNjIw
MzczNTVdfQ==
-->