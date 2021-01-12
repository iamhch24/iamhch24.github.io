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

>InputStreamReader, OutputSreamWriter의 특징

* 사용자가 키보드로 한글을 입력하면 실제 컴퓨터는 먼저 바이트 데이터로 입력받는다. 바이트 데이터를 InputStreamReader 클래스로 전달하여 한글로 조합한 후 프로그램에 전달하는 것이다. 이와 반대로 OutputStreamWriter는 바이트 데이터를 문자로 변경한 후 출력하는 역할을 한다. 


### 객체 직렬화 (Serialization)

* 객체 직렬화 정의 :: 프로그램 실행시 생성되는 인스턴스의 상태를 장치에 저장하거나 네트워크로 전송하는 기능
* 등장 배경 :: 인스턴스의 상태를 다른 프로그램이나 네크워크로 전송해야 할 경우가 발생.
* 자바 객체 직렬화 특징 :: 객체의 상태를 지속시키는 방법을 제공한다. 스트림을 통해 다른 장치나 네트워크에서 사용 가능하게 한다. 객체는 바이트 데이터로 저장되거나 전송된다.

> 자바 객체 직렬화 과정

* java.io.Serializable 인터페이스를 구현한다. 인터페이스를 구현한 클래스의 속성은 모두 직렬화의 대상이 된다. 직렬화 대상에서 제외키시고 싶은 경우에는 transient를 이용한다.
* 스트림 클래스를 이용하여 직렬화 또는 역직렬화한다. ObjectOuputStream의 writeObejct()메서드, ObjectInputStream의 readObject()메서드 이용

> 역직렬화 시 주의할 점
* 역직렬화 시 다운캐스팅하는 클래스 타입은 직렬화 시 사용된 클래스와 일치하는 클래스로 수행해야 한다.

# 13장 네트워크

### 자바에서 네트워크 통신이란?
JVM과 JVM 사이의 통신을 의미한다. JVM이 다른 원격지에 위치하면 일반적인 네트워크 통신과 같지만, 하나의 PC에서 2개의 JVM이 통신을 할 수도 있다.

### 네트워크 통신 구성요소
* IP 주소 + 도메인네임
* 포트 번호 :: 하나의 컴퓨터에서 여러 프로세스를 구분하는 번호. 포트 번호는 0~65535번까지 할당 할 수 있으며, 0~1023까지는 시스템에서 사용함. ex) 80(HTTP), 21(FTP), 23(TELNET)
* 프로토콜 :: 클라이언트와 서버 간의 일정한 방식으로 통신하기 위한 규약이다. 상호간의 접속방식, 데이터 형식, 오류 검출 방식 등을 표준화 한 후 통신한다.

### 자바의 네트워크 통신 구현 기술
* java SE :: 소켓 통신, RMI (Remote Method Invocation)
* java EE :: 웹 기술(JSP&Servlet), Web Service 기술

### 자바 소켓 통신
* 소켓 :: 네트워크 말단 부분을 의미하며, 네트워크 통신 기능을 캡슐화하여 제공한다.

### 클라이언트와 서버 프로그램
* 클라이언트의 기능 (java.net.Socekt 클래스) :: IP주소와 포트 번호로 서버에 서비스를 요청한다. 데이터를 서버에서 수신한다. 자바 Stream 클래스를 이용하여 통신하다.
* 서버 기능 (java.net.ServerSocket 클래스) :: 서버는 항상 실행되어 있어야 한다. 다수의 클라이언트 요청을 동시에 처리한다. 자바 Stream 클래스를 이용하여 통신한다.

>SimpleServer.Java

```Java
package sec13.ex01;

import java.io.*;
import java.net.*;

public class SimpleServer {
	public static void main(String[] args) {

		BufferedWriter bw;
		PrintWriter pw = null;
		OutputStream os;
		ServerSocket serverSocket;
		Socket s1 = null;
		InetAddress ipAddrs = null;
		String connectedClient = null;
		String outMessage = null;
		try {
			serverSocket = new ServerSocket(5434);	// 서버소켓 생성
			System.out.println("서버 실행 중... ");

			while (true) {
			while (true) {
				// 클라이언트의 접속을 인지 시에 accept()메소드를 호출해서 소켓 객체를 생성한다.
				s1 = serverSocket.accept(); // 클라이언트와의 연결된 소켓 객체를 생성

				os = s1.getOutputStream();  // 클라이언트의 OutputStream 객체를 얻는다.
				ipAddrs = s1.getInetAddress();  // 클라이언트의 인터넷 주소를 얻는다.

				connectedClient = ipAddrs.toString();
				bw = new BufferedWriter(new OutputStreamWriter(os));
				pw = new PrintWriter(bw, true);
				pw.println(connectedClient + " 에서 서버에 접속하셨습니다.");
				pw.close();
				s1.close();
			}
		} catch (IOException ie) {
			ie.printStackTrace();
		}
	}
}

```
*위에서 보면 클라이언트와의 연결되어 소켓 객체가 생성된 후 OutputStream 객체를 얻고  OutputStreamWriter --> BufferedWriter --> PrintWiter --> println 순으로 데이터를 전송한다.

>SimpleClient.java

```Java
package sec13.ex01;

import java.io.BufferedReader;
import java.io.InputStream;
import java.io.InputStreamReader;
import java.net.Socket;

public class SimpleClient {
	public static void main(String[] args) {

		InputStream is;
		BufferedReader br;
		String message = null;
		try {
			Socket s1 = new Socket("127.0.0.1", 5434); // 소켓 생성
			is = s1.getInputStream();
			br = new BufferedReader(new InputStreamReader(is));
			message = br.readLine();
			System.out.println(message);
			s1.close();
		} catch (Exception e) {
			e.printStackTrace();
		}
	}

}
```

* 클라이언트 쪽에서는 소캣 생성 후 InputStream 객체를 받고 InputStreamReader --> BufferedReader --> readLine() 으로 데이터를 받는다.

### 객체 직렬화

> Employee.java :: Serializable 인터페이스를 구현한다.

```Java
package sec13.ex02;

import java.io.Serializable;

public class Employee implements Serializable {

	String name;
	String addr;
	String jumin;
	String phone;

	public Employee(String name, String addr, String jumin, String phone) {

		this.name = name;
		this.addr = addr;
		this.jumin = jumin;
		this.phone = phone;
	}
```

> SerServer.java 

```Java
package sec13.ex02;

import java.net.*;
import java.io.*;

public class SerServer {
	public static void main(String args[]) {
		ServerSocket s = null;

		try {
			s = new ServerSocket(5433);
		} catch (IOException e) {
		}

		while (true) {
			try {
				System.out.println("서버 실행 중!!!!");
				Socket s1 = s.accept();
				OutputStream out = s1.getOutputStream();
				ObjectOutputStream dos = new ObjectOutputStream(out); // 객체를 출력할 스트림 생성
				Employee p = new Employee("박지성", "서울시 강남구", "111111-2222222", "123-1234");
				dos.writeObject(p); // 객체를 전송함
				dos.close();
				s1.close();
			} catch (IOException e) {
				e.printStackTrace();
			}
		}
	}
}
```
* 서버쪽에서 소캣 생성 후 outputStream 객체를 받고 ObjectOuputStream (객체 직렬화 스트림)--> writeObject() 로 객체 (Employee)를 전송한다.

> SerClient.java

```Java
package sec13.ex02;

import java.net.*;
import java.io.*;

public class SerClient {
	public static void main(String args[]) {
		try {
			Socket s1 = new Socket("127.0.0.1", 5433);

			InputStream is = s1.getInputStream();
			ObjectInputStream dis = new ObjectInputStream(is);

			Employee p = (Employee) dis.readObject();
			System.out.println("이름: " + p.getName());
			System.out.println("주소: " + p.getAddr());
			System.out.println("주민번호: " + p.getJumin());
			System.out.println("전화번호: " + p.getPhone());

			dis.close();
			s1.close();
		} catch (ConnectException connExc) {
			System.err.println("연결실패.");
		} catch (Exception e) {
			e.printStackTrace();
		}
	}
}
```
* 클라이언트쪽에서는 소캣 생성 후 InputStream 객체를 얻은 후 ObjectInputStream --> readObject() 를 통해 객체 정보를 받는다.


### 채팅 프로그램

> SimpleServer.java

```Java
package sec13.ex03;

import java.net.*;
import java.io.*;

public class SimpleServer {
	public static void main(String args[]) {
		try {
			System.out.println("서비스하기위해 준비중입니다.");
			ServerSocket s = new ServerSocket(5434);
			System.out.println("서버가 동작중입니다.");

			Socket s1 = s.accept(); // 클라이언트의 접속을 허락한다.
			BufferedReader in = new BufferedReader(new InputStreamReader(System.in)); // 키보드로 문자열 입력
			ObjectInputStream ois = new ObjectInputStream(s1.getInputStream()); // 객체입출력 스트림을 생성
			ObjectOutputStream oos = new ObjectOutputStream(s1.getOutputStream());

			oos.writeObject("Simple server에 접속하신걸 환영합니다.!!");
			while (true) {
				System.out.println((String) ois.readObject()); // 클라이언트에서 전송된 데이터를 출력한다.
				System.out.print("<Server> :");
				String temp = in.readLine();
				if (temp.equals("exit")) {
					System.out.println("bye");
					break;
				}
				oos.writeObject("<Server> :" + temp); // 입력한 문자열을 클라이언트로 전송한다.
			}
			oos.close();
			s1.close();
		} catch (ClassNotFoundException eof) {
			System.out.println("Client로 부터 연결이 끊어졌습니다. 종료합니다...");
			System.exit(0);
		} catch (IOException io) {
			io.printStackTrace();
		}
	}
}
```

> SimpleClient.java

```Java
package sec13.ex03;

import java.net.*;
import java.io.*;

public class SimpleClient {
	public static void main(String args[]) throws IOException {
		if (args.length == 0) {
			System.out.println("사용법 : java SimpleClient [server_name]");
			System.out.println("server_name을 입력하지 않으셔서 localhost로 접속을 시도합니다.");
			args = new String[] { "127.0.0.1" };
		}
		try {
			Socket s1 = new Socket(args[0], 5434); // 소켓 객체를 생성한다.
			BufferedReader in = new BufferedReader(new InputStreamReader(System.in)); // 키보드로 문자열을 입력 받는다.
			ObjectOutputStream oos = new ObjectOutputStream(s1.getOutputStream()); // 네트워크로 입,출력을 위해서 객체 입출력 스트림을 생성한다.
			ObjectInputStream ois = new ObjectInputStream(s1.getInputStream());
			System.out.println("접속완료..");
			System.out.println((String) ois.readObject()); // 서버에서 받은 문자열을 출력한다.
			System.out.println("서버에게 먼저 메시지를 보내십시요 !!");

			while (true) {
				System.out.print("<Client> :");
				String temp = in.readLine();
				if (temp.equals("exit")) {
					System.out.println("bye~");
					break;
				}
				oos.writeObject("<Client> :" + temp); // 서버로 입력한 문자열을 보낸다.
				System.out.println((String) ois.readObject());
			}
			ois.close();
			s1.close();
		} catch (ClassNotFoundException eof) {
			System.out.println("Server로 부터 연결이 끊어졌습니다. 종료합니다...");
			System.exit(0);
		} catch (IOException io) {
			io.printStackTrace();
		}
	}
}
```

### 쓰레드를 이용한 채팅 프로그램

>RecvThread.java

```Java
package sec13.ex04;

import java.io.*;
import java.net.*;

public class RecvThread extends Thread {
	InputStream is;
	BufferedReader br_in;
	ServerSocket serverSocket;
	Socket socket = null;
	String inMessage = null;

	public RecvThread(Socket s) {
		this.socket = s;
	}

	public void run() {
		try {
			is = socket.getInputStream();
			br_in = new BufferedReader(new InputStreamReader(is));
			while (true) {
				inMessage = br_in.readLine();
				System.out.println(inMessage);
			}
		} catch (Exception e) {
			e.printStackTrace();
		}
	}
}


```

> SimpleClient.java

```Java
package sec13.ex04;

import java.io.*;
import java.net.*;

public class SimpleServer {
	public static void main(String[] args) {
		BufferedReader br_out;
		BufferedWriter bw;
		PrintWriter pw = null;
		OutputStream os;
		ServerSocket serverSocket;
		Socket s1 = null;
		String outMessage = null;
		try {
			serverSocket = new ServerSocket(5434);
			System.out.println("서버 실행 중...");
			s1 = serverSocket.accept();
			os = s1.getOutputStream();

			// 메시지 수신을 위한 쓰레드를 생성후 실행
			RecvThread rThread = new RecvThread(s1);
			rThread.start();

			br_out = new BufferedReader(new InputStreamReader(System.in));
			bw = new BufferedWriter(new OutputStreamWriter(os));
			pw = new PrintWriter(bw, true); // 자동으로 flush 한다.
			pw.println("server: 접속을 환영합니다.");
			while (true) {
				outMessage = br_out.readLine();
				if (outMessage.equals("exit"))
					break;
				pw.println("server: " + outMessage);
			}
			pw.close();
			s1.close();

			if (rThread.isAlive()) {
				rThread.interrupt();
				rThread = null;
			}
		} catch (SocketException e) {
			System.out.println("클라이언트로 부터 연결이 끊어졌습니다. 종료합니다...");
			System.exit(0);
		} catch (Exception e) {
			e.printStackTrace();
			System.exit(0);
		}
	}
}
```

>SimpleClient.java

```Java
package sec13.ex04;

import java.io.*;
import java.net.*;

public class SimpleClient {
	public static void main(String[] args) {
		OutputStream os;
		BufferedReader br_in;
		BufferedWriter bw = null;
		PrintWriter pw = null;
		String outMessage = null;

		try {
			Socket s1 = new Socket("127.0.0.1", 5434);
			os = s1.getOutputStream();
			// 메시지 수신을 위한 쓰레드를 생성후 실행
			RecvThread rThread = new RecvThread(s1);
			rThread.start();

			br_in = new BufferedReader(new InputStreamReader(System.in));
			bw = new BufferedWriter(new OutputStreamWriter(os));
			pw = new PrintWriter(bw, true); // 자동으로 flush 한다.
			while (true) {
				outMessage = br_in.readLine();
				if (outMessage.equals("exit"))
					break;
				pw.println("client: " + outMessage);

			}
			pw.close();
			s1.close();

			if (rThread.isAlive()) {
				rThread.interrupt();
				rThread = null;
			}

		} catch (SocketException e) {
			System.out.println("서버로 부터 연결이 끊어졌습니다. 종료합니다...");
			System.exit(0);
		} catch (Exception e) {
			e.printStackTrace();
			System.exit(0);
		}
	}

}

```

* 문제가 생긴 것은 통신하면서 한글이 깨지는 현상이다. 어떻게 인코딩을 맞춰줄 수 있을까???


<!--stackedit_data:
eyJoaXN0b3J5IjpbMjIyOTY4MzEzLDg0MzE4OTU5LC0xNjY2Mz
I4MDYyLDMxNTY1MzA0NywyNTc0Mjc2OTgsLTM1NjQ3ODExNiwx
Njc5ODQxMjY0LDE3NDAwMDQyOTgsLTQ0MTg3ODk0NSwtMTM1Nz
I0OTc0MywxODEwNTY4OTkyLC0xNzgzNDY3MDQ3LC0xMTQ3Nzg0
MjM2LC0xMTc4Mjc1NzI1LDE2MzQwODExMjcsNTA0NzE0NDQsMT
k2NzI3ODc3OSwtMTI2NDQ0NDc3M119
-->