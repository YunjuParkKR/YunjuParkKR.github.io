---
layout: single
title: "✨ "
categories: blog
tag: [블로그, 코딩, 자바, Java, BufferedReader, Scanner, Java.io, 입출력]
toc: true
toc_sticky: true
toc_label: 목차
---

**[Java]** Java의 입출력 방법

Java의 BufferedReader에 대하여 알아보자.


## BufferedReader, BufferedWriter란
버퍼를 사용하여 읽기와 쓰기를 하는 함수.
버퍼를 사용하는 입력은 키보드의 입력이 있을 시 한 문자씩 버퍼로 전송한 뒤, 버퍼가 가득 차거나 개행 문자가 나타나면 버퍼의 내용을 한 번에 프로그램에 전달한다. 
속도가 빠르고 버퍼 사이즈가 Scanner보다 크기 때문에 많은 입력을 필요로 할 경우에 사용하면 좋다.
BufferedReader는 개행문자만 경계로 인식하며, 입력받은 데이터는 String 타입이 된다.



## BufferedReader와 Scanner 비교

| BufferedReader |    Scanner    |
| -------------- | ------------- |
| - | 지원하는 메소드가 비교적 많음  |
| 입력받은 문자는 String타입으로 고정됨 | int, char, String 등 다양한 타입 입력 가능  |
| 입력받은 데이터를 원하는 타입으로 가공하는 작업이 필요할 수 있음 | 입력받은 데이터를 따로 가공할 필요가 없어 편리함  |
| 버퍼 사이즈 8192char | 버퍼 사이즈 1024char |
| 개행문자만 경계로 인식함 | 띄어쓰기와 개행문자를 경계로 인식함  |
| 속도가 비교적 빠름 | 속도가 비교적 느림  |
| 동기화가 되므로 멀티쓰레드 환경에서 안전함 | 동기화가 되지 않으므로 멀티쓰레드 환경에서 안전하지 않음  |
| 입력 시 한 문자씩 버퍼로 전송한 뒤, 버퍼가 가득 차거나 개행 문자가 나타나면 버퍼의 내용을 한 번에 프로그램에 전달 | 입력 시 즉시 그 내용을 프로그램에 전달  |



## BufferedReader 사용법

아래와 같이 선언하여 사용함.

```java
BufferedFeader br = new BufferedReader(new InputStreamReader(System.in)); // 이와 같이 선언하여 사용
String str = br.readLine(); // 입력은 readLine();이라ㅡㄴ 메소드 사용. 입력 내용을 str이라는 이름의 변수에 저장
int i = Integer.parseInt(br.readLine()); // 입력받은 내용을 int 타입으로 변환하고 싶을 때.
```

이처럼, String 타입이 아닌 다른 타입으로 입력 내용을 저장하려면 반드시 형변환을 해줘야 한다.
또한, 예외처리를 반드시 필요로 한다.


### 예외처리 방법
1) readLine() 마다 try ~ catch 문으로 감싸주기
2) throws IOException 사용 


### 데이터 가공 방법
- 입력받은 데이터를 공백 단위로 나누고자 하는 경우
  1) StringTokenizer 사용
     ```java
     BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
     StringTokenizer st = new StringTokenizer(br.readLine());
     int n = Integer.parseInt(st.nextToken());
     int m = Integer.parseInt(st.nextToken());
     // 입력받은 데이터를 공백을 단위로 구분하여 순서대로 호출 가능
     ```
  2) String.split() 메소드 사용
     ```java
     String arr[] = s.split(" ");
     // 입력받은 데이털르 공백 단위로 끊어 배열에 저장
     ```



## BufferedReader의 주요 메소드

- read() : 한 글자만 읽어 정수형으로 반환함. 반환값 타입은 int.
- readLine() : 입력 내용 한 줄을 읽음. 반환값 타입은 String.
- ready() : 입력 스트림이 사용할 준비가 되었는지 확인하는 메소드. 반환값 타입은 boolean이며, 반환값이 1일 경우 사용 준비 완료되었다는 뜻.
- mark(int, readAheadLimit) : 스트림의 현재 위치를 마킹함. 반환값은 없음(void).
- close() : 입력 스트림을 닫고 사용이 끝난 자원을 반환. 반환값은 없음(void).



## BufferedWriter

내용 추가 예정... ~~
