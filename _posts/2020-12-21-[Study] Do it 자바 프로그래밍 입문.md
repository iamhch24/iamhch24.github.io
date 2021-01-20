---
title: "[Study] Do it 자바프로그래밍 입문"
categories:
    - dev
tags:
    - dev
    - java
toc: true

---

# 1장 자바 프로그래밍 시작하기

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

* 다형성의 완성은 오버라이드

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

### 객체 정렬하기

* Comparable 인터페이스 구현시 
compareTe() 오버라이딩
```Java
public int compareTo(object o){
	if( o instanceof Member ){
		Memeber member = (Member) o;
		if(this.memberID > member.memberID) return 1;
		else if(this.memberID == member.memberID) return 0;
		else return -1;
	}
	return -1;
}
```
*`Comparable` 인터페이스의 `compareTo()` 메서드를 통해 인자로 넘어온 같은 타입의 다른 객체와 대소 비교가 가능합니다. 메서드를 호출하는 객체가 인자로 넘어온 객체보다 작을 경우에는 음수를 리턴하고, 크기가 동일하다면 0, 클 경우에는 양수를 리턴해야합니다.

⇒ Sort() 가능해짐
참고 :: https://www.daleseo.com/java-comparable-comparator/


# 13장 내부클래스, 람다식, 스트림

### 내부클래스를 사용하는 이유
1 은닉화 효과가 있음. 내부적으로 구현되기 때문에 외부에서는 볼 수가 없음. 노출이 안됨
2 주로 자바 화면에서 사용자가 발생시킨 이벤트를 처리하는 이벤트 핸들러로 사용함 (익명 내부 클래스)
3 마치 외부 클래스를 상속해서 내부 클래스에서 확장하듯이 사용함. -- 약간 싱글턴 느낌이 남

### 내부 클래스 종류와 생성 방법
* 인스턴스 내부 클래스 :: 외부 클래스를 먼저 만든 후 내부 클래스 생성됨
* 정적 내부 클래스 :: 외부 클래스와 무관하게 생성됨
* 지역 내부 클래스 :: 메서드를 호출할 때 생성됨
* 익명 내부 클래스 :: 메서드를 호출할 때 생성되거나, 인터페이스 타입 변수에 대입할 때 new 예약어를 사용하여 생성됨


### 자바 람다식 :: 클래스 개념 때문에 어쩔 수 없이 인터페이스로 미리 선언되어야 사용할 수 있음
그럼에도 자바에서 람다식을 사용하는 이유는 함수형 프로그래밍이 원본을 수정하지 않고, 원본을 보존하기 때문에 독립성이 보존되고 이를 기반으로 병렬처리가 가능함. 

* str -> { System.out.println(str); }    // 한 문장이라도 리턴이 없는 경우는 {} 을 생략X
* (x,y) -> { System.out.println(x+y);} // 매개변수가 2개 이상이면 ()를 생략X
* (x,y) -> x + y    // x+y 반환 == 리턴이 하나인 경우 { return  ;} 가 함께 생략 가능 
* MyNumber max = (x,y) -> (x>y) ? x: y;  // 왼쪽에 인터페이스 인스턴스를 받는 경우 마지막에 ;로 문장의 끝을 표현함. 이 경우도 { return ; } 생략된 케이스
* 인터페이스 선언에서 람다식이 이름이 없기 때문에 람다식 하나에 인터페이스 하나가 매칭되어야 함. 그래서 @FunctionalInterface 애노테이션을 선언해 주어 하나의 인터페이스 내에 람다식 여러개 선언되면 에러를 보여주게 함.

```Java
@FunctionalInterface
interface  Calc {  // 함수형 인터페이스의 선언
	public  int  min(int  x,  int  y);
}

public  class  Lambda02 {
	public  static  void  main(String[]  args){
		Calc  minNum  =  (x, y)  ->  x  <  y  ?  x  :  y;  // 추상 메소드의 구현
		System.out.println(minNum.min(3,  4)); // 함수형 인터페이스의 사용
	}
}

```

* 인터페이스를 다른 파일로 선언해 줄 수 있으나 위 코드 처럼 내부 파일에 생성하는 것이 더 편해 보임

참고 :: http://www.tcpschool.com/java/java_lambda_concept

* 람다식의 장점 --- 코드가 한결 줄어든다 + 기존의 메서드가 하나인 인터페이스는 람다로 구현해서 곧바로 실행가능함.

```Java
new  Thread(new  Runnable() {
	public  void  run() {
	System.out.println("전통적인 방식의 일회용 스레드 생성");
}
}).start();

new  Thread(()->{
	System.out.println("람다 표현식을 사용한 일회용 스레드 생성");
}).start();
```

> 실습 
* 기존 방식 :: 인터페이스 - 클래스 구현으로 메서드를 실행하려면 1) StringConcat 인터페이스 선언 + 2) 인터페이스 구현한 클래스 StringConcatImpl 생성 --> 메서드 실행 가능 
* 람다식 :: 인터페이스를 실제 받아 클래스로 구현하여 new 생성자 부분을 람다함수로 처리 하여 코드를 확실히 줄일 수 있음

```Java
package lambda;

public class StringConcatTest {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		String s1 = "Hello";
		String s2 = "World";
		StringConcat concat = (s,v) -> System.out.println(s+", "+v); // new 생성자 대신 람다식으로 메서드를 구현한다. 중간 단계 생략하는 효과 --> 마치 변수화된 것처럼 보임 == 당장 실행되는 것이 아니라서 람다함수를 다른 곳의 변수처럼 던져질 수 있음.
		concat.makeString(s1,s2); // 여기서 람다함수가 실제 실행이 됨
	}
	
	@FunctionalInterface
	public interface StringConcat{
		public void makeString(String s1, String s2);
	}
}
```
* 코딩의 인식을 편하게 위해 람다를 쓸 때 _s 처럼 언더바를 표기하기도 한다.

> 스레드 예제에서 람다식 사용
```Java
package lambda;

public class Runnable_Ex {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Runnable run = () -> {
			for(int i=0; i<10;i++) {
				System.out.println("a " + i);
				try {
					Thread.sleep(1000);
				}catch(InterruptedException e) {
					e.printStackTrace();
				}
				
			}
		};
		Thread thread = new Thread(run);  // 스레드 생성자 안에 매개변수 Runnable 넣어줌 :: Thread(runnable r)
		thread.start();
		
		Thread thread2 = new Thread(() -> {
			for(int i=0; i<10;i++) {
				System.out.println("b " + i);
				try {
					Thread.sleep(1000);
				}catch(InterruptedException e) {
					e.printStackTrace();
				}
				
			}
		} );
		thread2.start();
		
		new Thread(() -> {
			for(int i=0; i<10;i++) {
				System.out.println("c " + i);
				try {
					Thread.sleep(1000);
				}catch(InterruptedException e) {
					e.printStackTrace();
				}
				
			}
		} ).start();
	
		
		for(int i=0;i<10;i++) {
			System.out.println("main " + i);
			try {
				Thread.sleep(1000);
			}catch(InterruptedException e) {
				e.printStackTrace();
			}
		}
	}
}

```

* 위의 코드에서 람다식이 가능한 이유는 Runnable 인터페이스의 메서드가 run() 하나 밖에 없기 때문이다. // void run();

> 아래는 Runnable 인터페이스 정의이다.

```Java
package java.lang;
@FunctionalInterface
public interface Runnable {
    /**
     * When an object implementing interface {@code Runnable} is used
     * to create a thread, starting the thread causes the object's
     * {@code run} method to be called in that separately executing
     * thread.
     * <p>
     * The general contract of the method {@code run} is that it may
     * take any action whatsoever.
     *
     * @see     java.lang.Thread#run()
     */
    public abstract void run();
}

```

* 모나드 monad 기법 :: 함수형 기법 = 람다식, 다른 언어에서는 클로우저 라고 도 함.

#### 람다식 인터페이스 5개

* (1) Consumer 인터페이스 :: (소비형) :: 들어가는 것은 있는데 나오는 게 없는 구조 :: accept()
* (1-1) BiConsumer 인터페이스 :: (소비형) :: 인풋 2개 아웃풋 0개 :: accept() 로 호출
* (2) Supplier 인터페이스 :: (공급형) :: 인풋 0, 아웃풋 1개 :: get() 로 호출
* (3) Function 인터페이스 :: (함수형) :: 인풋 1, 아웃풋 1개 :: apply() 로 호출
* (3-2) BiFunction 인터페이스 :: (함수형) :: 인풋 2, 아웃풋 1개 :: apply() 로 호출
* (4) UnaryOperator 인터페이스 :: (오퍼레이터형) :: 인풋 1, 아웃풋 1개 -- 같은 타입 :: apply()로 호출
* (4-1) BiOperator 인터페이스 :: (오퍼레이터형) :: 인풋 2, 아웃풋 1개 -- 같은 타입 :: apply()로 호출
* (5) Predicate 인터페이스 :: (예언형) :: 인풋 1, 리턴값은 boolean, 매개값을 조사하고 true/false를 리턴 :: test()로 호출
* (5-1) BiPredicate 인터페이스 :: (예언형) :: 인풋 2, 리턴 boolean :: test()로 호출

* `Comparator`
보통 객체간 우선순위를 비교할때 Comparable 인터페이스를 사용하는데 그때 그때 적용할 로직을 1회성으로 구현하는데 많이 사용했습니다. Comparator는 간단하게 Comparable 인터페이스를 대신해 사용할 수 있습니다.
```
Comparator<String> c = (str1, str2) -> str1.compareTo(str2);
int result = c.compare("xxx", "yyy");  //-1
```
(참고 :: https://dinfree.com/blog/2019/03/27/javafp-1.html)

>실습

```Java
package lambda;

import java.util.function.BiConsumer;
import java.util.function.BiFunction;
import java.util.function.BinaryOperator;
import java.util.function.Consumer;
import java.util.function.Function;
import java.util.function.Supplier;
import java.util.function.UnaryOperator;

public class ConsumerRunnable {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Consumer<String> consumer = t -> System.out.println(t+" Java 8"); 
		consumer.accept("Hello");
		BiConsumer<String,String> biconsumer = (t,v) -> System.out.println(t+v);
		biconsumer.accept("Hello"," Java 8");
		BiConsumer<Integer,Integer> biconsumer2 = (t,v) -> System.out.println(t+v);
		biconsumer2.accept(100,500);
		
		Supplier<String> supplier = () -> "Hello Java 8"; 
		System.out.println(supplier.get());
		
		Supplier<Integer> supplier2 = () -> {
			int random_number = (int)(Math.random() * 6) +1;
			return random_number;
		};
		System.out.println("주사위의 번호는 "+ supplier2.get());
		
		Function<String,String> function = (_s) -> "Hello "+_s;
		System.out.println(function.apply("Java 8"));
		
		BiFunction<Integer,Integer, Integer> bifunction = (t,u) -> {
			Integer sum = t +u;
			return sum;
		};
		System.out.println(bifunction.apply(100,500));
		
		UnaryOperator<Integer> unaryoperator = (_t) -> { 
			return _t + 500;
		};
		System.out.println(unaryoperator.apply(100));
		
		BinaryOperator<String> binaryoperator = (t, u) ->{
			return t+u;
		};
		System.out.println(binaryoperator.apply("Hello", " Java 8"));
		
		System.out.println(function1.apply(100_000));

		Predicate<Integer> predicate = (t) -> t > 10;
		System.out.println(predicate.test(100));
		
		BiPredicate<Integer, Integer> bipredicate = (t,u) -> t>u;
		System.out.println(bipredicate.test(-100,-90));
	}
	private static Function<Integer, String> function1 = (t) -> {
		return t.toString();
	};
}
```

> Predicate 의 and, or 처리

```Java
package lambda;
import java.util.function.Predicate;

public class Predicate_Run {
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Predicate<Integer> predicate1 = (t) -> t%2 ==0;	// 2의 배수
		Predicate<Integer> predicate2 = (t) -> t%3 ==0;	// 3의 배수
		
		Predicate<Integer> predicate1and2 = predicate1.and(predicate2);	// 2이면서 3의 배수
		System.out.println(predicate1and2.test(33));  	// false
		
		Predicate<Integer> predicate1or2 = predicate1.or(predicate2);	// 2의 배수 이거나 3의 배수
		System.out.println(predicate1or2.test(33));		// true
	}
}
```

> Consumer를 합성함수처럼 호출하기 :: andThen()사용 -- 요녀석은 인터페이스의 default 메서드로 구현되어 있음.

```Java
package lambda;
import java.util.function.Consumer;

public class Consumer_Run {
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Consumer<Member> consumer1 = (_s)->{
			System.out.println(_s.getName());
		};
		Consumer<Member> consumer2 = (_s)->{
			System.out.println(_s.getId());
		};
		Consumer<Member> consumer2_1 = consumer1.andThen(consumer2); // consumer2을 하고 consumer1를 실행 (합성함수 처럼)
		consumer2_1.accept(new Member("Karl","1234"));
	}
}
```
> 콜백함수

⇒ 람다식으로 인해 함수를 변수처럼 사용할 수 있어서 함수를 던질 수 있다. 이렇게 던져진 함수를 콜백 함수라고 한다.

### 스트림 클래스 :: 원본 값을 수정하지 않는다.

Arrays 클래스
메서드 
public static <T> Stream<T> stream(T[] array) {
        return stream(array, 0, array.length);
}

* 스트램 생성 방법
각 데이터 타입 객체에서 stream 메서드 호출

* 스트림 생성 + 중간 연산 (map, filter, sorted) + 최종 연산(forEach, sum, reduce ...)

* 최종연산 :: forEach, sum, count, max, min, average

> 실습

```Java
package stream;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.Iterator;
import java.util.List;
import java.util.stream.Stream;

public class StreamEx_Run {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int[] array1 = {1,2,3,4,5,6,7};
		for(int i : array1) {
			System.out.print(i+" ");
		}
		System.out.println();
		
		Arrays
		.stream(array1)		// int[] 는 객체가 아니고 stream을 생성할 수 없기에 Arrays객체를 이용함
		.forEach(it->System.out.print(it+" "));
		System.out.println();
		
		Arrays
		.stream(array1)
		.filter(s->s>3).forEach(it->System.out.print(it+" "));
		System.out.println();
		
		System.out.println(Arrays.stream(array1).max().orElse(0)); // orElse(0)은 null값을 0으로 -- null check optional 넣어줌
		
		List<String> list = Arrays.asList("홍길동","신용권","김자바");  // List :: Collection 중 하나
		Stream<String> stream = list.stream();
		Long count_number = list.stream().count();
		Long count_number2 = stream.count();
		System.out.println(count_number);
		System.out.println(count_number2);
		
		ArrayList<String> list2 = new ArrayList<>();
		list2.add("홍길동");
		list2.add("신용권");
		list2.add("김자바");
		Iterator<String> iterator = list2.iterator();
		
		while(iterator.hasNext()) {
			System.out.println(iterator.next());
		}

	}

}

```

> #### java.util.Arrays 클래스

* Arrays 클래스에는 배열을 다루기 위한 다양한 메소드가 포함되어 있습니다.
* Arrays 클래스의 모든 메소드는 클래스 메소드(static method)이므로, 객체를 생성하지 않고도 바로 사용할 수 있습니다.
* 이 클래스는 java.util 패키지에 포함되므로, 반드시 import 문으로 java.util 패키지를 불러오고 나서 사용해야 합니다.

> Optional 자바 :: `Optional`은 많은 사람들이 우리(자바 언어 설계자)에게 기대했던 범용적인 `Maybe` 타입과는 다르다. **라이브러리 메서드가 반환할 결과값이 ‘없음’을 명백하게 표현할 필요가 있는 곳에서 제한적으로 사용할 수 있는 메커니즘을 제공하는 것이  `Optional`을 만든 의도**였다.
> 참고 :: http://homoefficio.github.io/2019/10/03/Java-Optional-%EB%B0%94%EB%A5%B4%EA%B2%8C-%EC%93%B0%EA%B8%B0/

> Arrays.asList()
일반 배열을 ArrayList로 변환한다.  
```List<String> list = Arrays.asList(arr);  ```
Arrays.asList()는 Arrays의 private 정적 클래스인 ArrayList를 리턴한다.  **java.util.ArrayList 클래스와는 다른 클래스**이다.  
java.util.Arrays.ArrayList 클래스는 set(), get(), contains() 메서드를 가지고 있지만  **원소를 추가하는 메서드는 가지고 있지 않기 때문에 사이즈를 바꿀 수 없다.**
만약 **진짜 ArrayList를 받기 위해서는 다음과 같이 변환하면 된다.**  
ArrayList 생성자는 **java.util.Arrays.ArrayList의  상위(super) 클래스인 Collection Type  
도 받아들일 수 있다.**
```List<String> list = new ArrayList<String>(Arrays.asList(arr));```
 참고 :: https://m.blog.naver.com/roropoly1/221140156345


#### 중개 연산 메서드 요약:
* filter() :: 해당 스트림에서 주어진 조건(predicate)에 맞는 요소만으로 구성된 새로운 스트림을 반환.
* map() :: 해당 스트림의 요소들을 주어 함수에 인수로 전달하여, 그 반환 값으로 이루어진 새로운 스트림을 반환함
* flatMap() :: 해당 스트림의 요소가 배열일 경우, 배열의 각 요소를 주어진 함수에 인수로 전달하여, 그 반환값으로 이루어진 새로운 스트림을 반환한다.
* distinct() :: 해당 스트림에서 중복된 요소가 제거된 새로운 스트림을 반환함. 내부적으로 Object 클래스의 equals() 메서드를 사용함.
* limit() :: 해당 스트림에서 전달된 개수만큼의 요소만으로 이루어진 새로운 스트림을 반환
* peek() :: 결과 스트림으로부터 각 요소를 소모하여 추가로 명시된 동작(action)을 수행하여 새로운 스트림을 생성하여 반환 -- 디버깅용으로 많이 쓰임
* skip() :: 해당 스트림의 첫 번째 요소부터 전달된 개수만큼의 요소를 제외한 나머지 요소만으로 이루어진 새로운 스트림을 반환함.
* sorted() :: 해당 스트림을 주어진 비교자(comparator)를 이용하여 정렬함. 비교자를 전달하지 않으면 영문 사전 순(natural order)으로 정렬함.
참고 :: https://blog.naver.com/ddk94/222156069191

#### 최종 연산 메서드 요약 :
* forEach() :: 요소의 출력
* reduce() :: 요소의 소모 :: 누적연산 -- reduce() 메서드는 첫 번째와 두 번째 요소를 가지고 연산을 수행한 뒤, 그 결과와 세 번째 요소를 가지고 또다시 연산을 수행한다. 이런 식으로 해당 스트림의 첫 번째 요소와 연산을 시작하며, 그 결과와 두 번째 요소를 가지고 계속해서 연상을 수행하게 된다.
* findFirst(), findAny() :: 요소의 검색 -- findFirst()와 findAny() 메서드는 해당 스트림에서 첫 번째 요소를 참조하는 Optional 객체를 반환한다. 두 메서드 모두 비어 있는 스트림에서는 비어있는 Optional 객체를 반환한다.
* anyMatch(), allMatch(), noneMatch() :: 요소의 검사 -- 해당 스트림의 요소 중에서 특정 조건을 만족하는 요소가 있는지, 아니면 모두 만족하거나 모두 만족하지 않는지를 다음 anyMatch(), allMatch(); noneMatch() 메서드들을 이용하여 확인할 수 있다. 세 메서드 모두 인수로 Predicate 객체를 전달받으며, 요소의 검사 결과는 boolean 값으로 반환한다.
anyMatch(): 해당 스트림의 일부 요소가 특정 조건을 만족할 경우에 true를 반환.
allMatch(): 해당 스트림의 모든 요소가 특정 조건을 만족할 경우 true를 반환.
noneMatch(): 해당 스트림의 모든 요소가 특정 조건을 만족하지 않을 경우에 true를 반환.
* count(), min(), max() :: 요소의 통계 -- count() 메서드는 해당 스트림의 요소의 총개수를 long 탕비의 값으로 반환한다. max()와 min() 메서드는 스트림의 해당 요소들 중 가장 큰 값과 가장 작은 값을 가지는 요소를 참조할 수 있다. 이때 반환되는 값은 Optional 객체로 반환된다.
* sum(), average() :: 요소의 연산 -- IntStream이나 DoubleStream과 가 은 기본 타입 스트림에는 해당 스트림의 모든 요소에 대한 합과 평균을 구할 수 있는 sum()과 average() 메서드가 각각 정의되어 있다. 이때 average() 메서드는 각 기본 타입으로 래핑 된 Optional 객체를 반환한다.
* collect() :: 요소의 수집 -- collect() 메서드는 인수로 전달되는 Collectors 객체에 구현된 방법대로 스트림의 요소를 수집한다. 또한, Collectors 클래스에는 미리 정의된 다양한 방법이 클래스 메서드로 정의되어 있다. 이 외에도 사용자가 직접 Collector 인터페이스를 구현하여 자신만의 수집 방법을 정의하는 것도 가능하다.
toArray(), toCollection(), toList(), toSet(), toMap() :: 스트림을 배열이나 컬렉션으로 변환
counting(), maxBy(), minBy(), summingInt(), averagingInt() :: 요소의 통계와 연산 메서드와 같은 동작을 수행
reducing(), joining() :: 요소의 소모와 같은 동작을 수행
groupingBy(), partitioningBy() :: 요소의 그룹화와 분할
참고 :: https://blog.naver.com/ddk94/222157757762

>실습

```Java
package stream;
import java.util.Arrays;
import java.util.List;

public class ReduceTest {
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		List<String> greetings = Arrays.asList("안녕하세요","Hello","Good Morning","반갑습니다");
		String result = greetings.stream().reduce("", (s1,s2)->{
			if(s1.getBytes().length >= s2.getBytes().length) return s1;
			else return s2;			
		});
		System.out.println(result);
		String result2 = greetings.stream().reduce("", (s1,s2)->{System.out.println(s1);return s1+" "+s2;});
		System.out.println(result2);
	}
}
```

> 연습문제 Q7

```Java
package stream;
import java.util.ArrayList;
import java.util.List;

class Book {
	private String name;
	private int price;
	
	public Book(String name, int price) {
		this.name = name;
		this.setPrice(price);
	}
	public int getPrice() {
		return price;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public void setPrice(int price) {
		this.price = price;
	}
}

public class Q7 {
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		List<Book> bookList = new ArrayList<>();
		
		bookList.add(new Book("자바",25_000));
		bookList.add(new Book("파이썬",15_000));
		bookList.add(new Book("안드로이드",30_000));
		
		int total = bookList.stream().mapToInt(c->c.getPrice()).sum();
		System.out.println("== 모든 책의 가격의 합 ==");
		System.out.printf("    %d 만원",(int)total/10000);
		System.out.println();
		System.out.println();
		System.out.println("== 2만원 이상인 책 리스트 =="); 
		bookList.stream().filter(c->c.getPrice() >= 20_000).map(s->s.getName()).forEach(it -> System.out.println("    "+it));
	}

}

```


# 스레드

> 싱글스레드인 경우

```Java
package threads;

import java.awt.Toolkit;

public class BeepPrintRun {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Toolkit toolkit = Toolkit.getDefaultToolkit();
		for(int i=0;i<5;i++) {
			toolkit.beep();
			System.out.println("띵소리");
			try {
				Thread.sleep(500);
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
		for(int i=0;i<5;i++) {
			System.out.println("띵문자");
			try {
				Thread.sleep(500);
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
			
		}
	}

}
```

> 스레드로 구현 ( main 스레드와 BeepTask 스레드가 구동, 스택이 2개가 됨)

```Java
package threads;

public class BeepPrintRun {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Thread thread = new Thread(new BeepTask());
		thread.start();
		
		for(int i=0;i<5;i++) {
			System.out.println("띵문자");
			try {
				Thread.sleep(500);
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}		
		}
	}
}
```

```Java
package threads;
import java.awt.Toolkit;
public class BeepTask implements Runnable {
	@Override
	public void run() {
		// TODO Auto-generated method stub
		Toolkit toolkit = Toolkit.getDefaultToolkit();
		for(int i=0;i<5;i++) {
			toolkit.beep();
			System.out.println("띵소리");
			try {
				Thread.sleep(500);
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}
}

```

⇒ 

```Java

package threads;

import java.awt.Toolkit;

public class BeepPrintRun {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		
//		Thread thread = new Thread(new BeepTask());
//		thread.start();

		Thread thread = new Thread(new Runnable() {
			@Override
			public void run() {
				// TODO Auto-generated method stub
				Toolkit toolkit = Toolkit.getDefaultToolkit();
				for(int i=0;i<5;i++) {
					toolkit.beep();
					System.out.println("띵소리");
					try {
						Thread.sleep(500);
					} catch (InterruptedException e) {
						// TODO Auto-generated catch block
						e.printStackTrace();
					}
				}
			}
		} );
		thread.start();
		
		for(int i=0;i<5;i++) {
			System.out.println("띵문자");
			try {
				Thread.sleep(500);
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
			
		}
	}

}
```
 
⇒ 

```Java
package threads;
import java.awt.Toolkit;
public class BeepPrintRun {
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		
		new Thread(() -> {
				Toolkit toolkit = Toolkit.getDefaultToolkit();
				for(int i=0;i<5;i++) {
					toolkit.beep();
					System.out.println("띵소리");
					try {
						Thread.sleep(500);
					} catch (InterruptedException e) {
						// TODO Auto-generated catch block
						e.printStackTrace();
					}
				}
			}
		} ).start();
		
		for(int i=0;i<5;i++) {
			System.out.println("띵문자");
			try {
				Thread.sleep(500);
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
			
		}
	}
}
```


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3Mjc2NzUwMDgsLTgzMTQ4ODg2OSwtMT
g2OTY3MjU0MCwtNDg1Mjk1OTc5LDU1NzIzNDAsMTQzMDY1ODkx
OCwtMTg4MzIxNjMwMCwtMTA0NjUxODM5NywtMTYyMjY2MzY5OS
wtNjU0NzQyOTI1LDExMjkyMzg0MjksNzE0MzU1OTM3LDE1MDMy
NjQ4NjMsLTQwMDk2OTE2OSwxMDMzMTMwNDUxLC0zNzA2MjQyNi
wtMzg3NDU5NjkyLDE2NDExNzYsNDkwMjAyMjA2LDE3MjQyNjM1
MTddfQ==
-->