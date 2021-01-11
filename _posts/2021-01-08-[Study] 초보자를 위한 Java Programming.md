---
title: "[Study] 초보자를 위한 Java Programming"
categories:
    - dev
tags:
    - dev
    - java 
toc: true

---

# [Study] 초보자를 위한 Java Programming

# 11장 쓰레드

* 프로세스 :: CPU가 실행 중인 프로그램(명령어) : 구성요소 = 명령어+데이터
* 멀티 프로그래밍 :: 하나의 CPU가 여러 프로그램을 동시에 실행하는 것
* 멀티 프로세싱 :: 2개 이상의 CPU에 의해 여러 개의 프로그램이 동시에 실행되는 것
* 멀티 태스킹 :: 멀티 프로그래밍과 비슷한 개념으로, 여러 개의 task를 동시에 실행하는 것
* 스레드 :: 프로세스 내에서 실행되는 세부 실행 단위
* 멀티 스레드 :: 하나의 프로세스에 내에서 여러 개의 스레드가 병행 처리되는 것
* 싱글 스레드 :: 여러 스레드가 순차적으로 실행되는 것
* 스레드의 장점 :: 코드의 재사용성과 데이터 공유가 가능하다
* 스레드의 단점 :: 여러 스레드가 동시 실행 시 공유 자원에 대해 동기화를 해주어야 한다.
* CPU 스케줄링 :: 운영체제가 작업을 처리하기 위해 각 프로세스에 CPU를 적절히 할당하는 정책
* CPU 스케줄링 종류 : 선점 (우선순위) vs 비선점 (끝까지 기다림)
* 스레드 스케줄링 :: 멀티 스레드가 동작할 때 어떤 스레드를 먼저 수행할 것인지를 결정하는 작업 / 자바는 우선순위가 높은 스레드가 먼저 실행되는 선점형 스케줄링 방식을 사용함.
* 자바 스레드 특징 :: 우선권 스케줄링 , 스레드는 각 상태를 거치면서 실행한다. 멀티 스레드로 동작한다.
* 자바에서 스레드 생성 방법 :: 1) Thread 클래스 이용 2) Runnable 인터페이스 이용 (Runnable 이 Thread를 상속함)
 
>사용자가 정의 스레드를 만드는 방법

```Java
class 클래스명 extends Thread{
	public void run(){
	//스레드 실행시 실행 명령문
	...
	}
}
```
 ⇒ 보통 Runnable 인터페이스를 이요하는 이유는 자바는 단일 상속만 허용하므로 클래스가 다른 클래스를 상속받는 경우에는 Thread 클래스를 상속받지 못함.

```Java
public class 클래스명 implements Runnable{
	public void run(){
		...
	}
}
```

> 쓰레드가 가지는 여러가지 상태 
* Runnable 상태 :: 스레드가 실행하기 위한 준비상태
* Running 상태 :: 스레드 스케줄러에 의해 선택된 스레드를 실행하는 상태
* Blocked 상태 :: 스레드가 작업을 완수하지 못하고 잠시 작업을 멈추는 상태

>스레드 실행 과정
1. start() 호출
2. 스레드가 실행을 준비한다
3. 스케줄러에 의해 스레드 호출(run() 호출)
4. 스레드 실행
5. 스레드가 완료하지 못하고 대기 상태로 전환( sleep(), yield(), join() 호출)
6. 대기 상태에서 다시 준비 상태로 전환

> sleep() 메서드
* sleep(long millis) :: 현재 실행중인 스레드의 실행을 지정 시간만큼 중지시킨다. 이는 우선순위가 낮은 스레드가 기아 상태에 빠지는 것을 방지할 수 있음.
* 호출방법 :: Thread.sleep(1/000초); //주어진 시간 동안 대기 상태에서 머문다.

>yield() 메서드
* 현재 실행하는 스레드가 다른 스레드를 실행하도록 실행을 중지한다.
* 호출방법 :: Thread.yield(); // 실행 중인 스레드가 호출한다.

>join() 메서드
* 대기 중인 스레드가 join 메서드를 호출한다. 호출 시 실행 중인 스레드는 대기 상태로 가고, 호출한 메서드가 실행된다. 호출한 메서도가 종료되면 대기 중인 스레드가 다시 실행된다.
* 호출방법 :: Thread.join();  // 대기 중인 스레드가 호출하여 실행 중인 스레드를 대기 상태로 만든다.


>자바 동기화 방식 :: lock을 이용하여 동기화 수행함

```Java
public synchronized void m(){
	...
} // 메서드 전체가 동기화됨

public void m(){
	synchronized (공유 객체){
	...
	}
} // 일부만 동기화
```

* Busy/Wait 방법 :: 성능을 떨어뜨림
* Lock/Sleep 방법 :: Object 클래스의 wait()와 notify()을 이용하여 동기화 성능을 향상시킴


# 12장 자바 I/O

> 자바 스트림 :: 자바의 입출력을 도와주는 매개체

* 자바 스트림은 자바 애플리케이션의 입장에서 데이터가 입력 / 출력해 주는 매개체와 같은 역할을 한다. 
* 개발자는 각 장치에 해당하는 스트림의 사용방법만 알면 된다. 
* 입출력 기능뿐만 아니라 뒤에 배우는 대부분의 기능을 이러한 방식으로 세부적인 기능을 샙슐화시키면서 개발자에게는 해당 기능을 수행하는 클래스(API)를 제공하여 작업을 쉽게 할 수 있게 한다. 
* 즉, 자바에서는 각 장치마다 데이터 입출력을 담당하는 스트림 클래스를 제공한다.

> 스트림 클래스 특징

* 단방향이다. (InputStream, OutputStream)
* FIFO (First In First Out) 이다. 
* 같은 용도의 스트림끼리는 연결이 가능하다

> 처리하는 데이터 타입 2가지 :: byte 타입 + char 타입

* byte 데이터 :: 동영상, 이미지, 사운 등 멀티미디어 데이터 / 8bit 단위 입출력
* char 데이터 :: 일반적인 문자 데이터, 2byte 단위 입출력

> 데이터 종류에 따른 스트림 클래스 분류

* byte 데이터 :: (입력) InputStream  + (출력) OutputStream
* char 데이터 :: (입력) Reader + (출력) Writer

> 데이터 처리 순서에 따른 분류 2가지 :: Node 스트림 계열 + Filter 스트림 계열

* Node 스트림 계열 :: 단순한 입출력 작업, 장치에 직접적으로 연결 -- InputStream, FileReader, ...
* Filter 스트림 계열 :: 입력 데이터, 출력 데이터를 가공함. 효율적 입출력 가능 -- ex) InputSteamReader, BufferedReader, ObjectInputStream, ...
⇒ Node 계열 스트림은 장치로부터 데이터를 입력받기에 바빠서 다른 작업을 할 수 없다. 그래서 Node 스트림으로 받은 데이터를 다른 Filter 계열 스트림으로 전달하여 입력 데이터를 가공한다.


> 자바 표준 입출력 스트림 :: java.lang.System 클래스

* 표준 입력 :: 키보드 System.in
* 표준 출력 :: 모니터 System.out
* 표준 오류 출력 :: System.err

>InputStream 클래스 :: java.io.InputSteam :: byte 데이터를 입력받는데 필요한 스트림 클래스들의 최상위

* java.io.FileInputStream :: 파일에서 byte 데이터를 읽을 수 잇는 기능을 제공한다. 파일이 존재하지 않으면 FileNotFoundException을 발생시킨다.
* java.io.BufferedInputStream :: 입력받은 데이터를 buffer에 저장한 후 가공할 수 있다.
* java.io.DataInputStream :: 기본형 데이터를 입력받을 때 사용함

>OutputStream 클래스 :: java.io.OutputStream :: byte 데이터를 출력하는 스트림 클래스의 최상위 추상 클래스

* java.io.FileOutputStream :: 데이터를 파일로 출력하는 기능을 하는 클래스
* java.io.BufferedOutputStream :: 출력 데이터를 일단 buffer에 저장한 후 가공한다. flussh 기능을 이용하여 버퍼에 채워지지 않더라도 출력할 수 있다.
* java.io.PrintStream :: 모든 데이터를 화면에 출력해주는 print(), println()을 정의한다.

> Reader :: java.io.Reader :: 문자(char) 입력을 받는데 사용되는 스트림 클래스의 최상위 추상 클래스. Char(2byte)단위로 입력받는다

* java.io.FileReader :: 파일에서 데이터를 읽을 수 있는 기능을 제공한다. char 단위로 읽는다. 파일이 존재하지 않으면 FileNotFoundException예외가 발생한다. 글자 깨짐이 없다.
* java.io.BufferedReader :: 데이터를 버퍼로 읽어 들여 여러 가지 처리를 할 수 있다. readLine() 메서드를 이용하여 데이터의 개행문자 (/r/n)을 인식을 인식할 수 있다. 행 단위로 처리 시 많이 사용한다.

> Writer :: java.io.Writer :: char 단위로 출력하는데 사용되는 스트림클래스의 최상위 추상 클래스

* java.io.FileWrite :: 파일에 데이터를 출력하는 기능을 제공하는 스트림 클래스, char 단위로 출력. 출력 대상 파일이 존재하지 않으면 새로 생성함. 생성자 호출 시 인자로 덮어 쓰기 또는 내용 추가를 선택할 수 있다.
* java.io.BufferedWriter :: 버퍼링을 통한 char 단위 쓰기를 할 수 있는 필터 스트림 클래스 한 줄 단위로 출력할 수 있는 newLine()이 제공된다.
* java.io.PrintWriter :: 특정 형식으로 문자를 출력하는 스트림이다. 바이트 출력 스트림과 문자 출력 스트림에 모두 사용 가능하다. 자동 flush 기능을 제공한다.





<!--stackedit_data:
eyJoaXN0b3J5IjpbNzM2NjkxMzMyLC0xMzU3MjQ5NzQzLDE4MT
A1Njg5OTIsLTE3ODM0NjcwNDcsLTExNDc3ODQyMzYsLTExNzgy
NzU3MjUsMTYzNDA4MTEyNyw1MDQ3MTQ0NCwxOTY3Mjc4Nzc5LC
0xMjY0NDQ0NzczXX0=
-->