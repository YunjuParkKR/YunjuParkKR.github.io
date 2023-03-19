---
layout: single
title: "🐧 OS 🐧 LAMP 구축 - Apache 컴파일 설치 방법 (v.2.4.37)"
categories: OS
tag: [블로그, 코딩, 깃허브, 깃허브블로그, 포스트, 운영체제, OS, 가상머신, virtualbox, 리눅스, linux, rockylinux, 로키리눅스, LAMP, APM, Apache, 아파치]
toc: true
toc_sticky: true
toc_label: 목차
published: true
---

**[OS]** LAPM 구축 - 

지난번 설치한 Rocky Linux에서 LAMP 환경을 구축해볼 것이다.

이번 포스트에서는 Apache 2.4.37 버전을 컴파일 설치(소스 설치) 방법으로 설치해볼 것이다.

소스 설치 방법이 yum, dnf 등을 이용한 설치 방법보다 번거로워서 그런지 설치 방법에 관한 글이 상대적으로 적던데,

이 글이 필요한 사람들에게 도움이 된다면 좋겠다.

나의 설치환경은 Rocky Linux v.9.1(VirtualBox로 실행) 이다.

🔻 VirtualBox 설치방법

<https://yunjuparkkr.github.io/os/virtualbox/>

🔻 Rocky Linux v.9.1 설치방법

<https://yunjuparkkr.github.io/os/RockyLinux/#rocky-linux-91-%EC%84%A4%EC%B9%98%EB%B0%A9%EB%B2%95-91-%EB%B2%84%EC%A0%84>


## LAMP 환경 구축

### LAMP이란?

LAMP 스택이란 Linux(Operating System), Apache(HTTP Server), Mysql(Database), Php(스크립트 언어)의 앞 글자를 딴 것으로, 웹 애플리케이션을 빌드하는 데 사용하는 무료 오픈소스 소프트웨어의 묶음, 개발 환경이라고 생각하면 된다.

웹 서버로 Apache를 사용하느나 Nginx를 사용하느냐에 따라 LAMP, AEMP로 부르기도 하며(E - Nginx Server), MySQL이 아닌 MariaDB를 사용하기도 한다.

또한, Linux를 빼고 APM(Apache, Php, Mysql)이라고 부르기도 한다.

- <strong>L</strong>inux - 리눅스 운영체제
- <strong>A(또는 E)</strong>pache(Nginx) - 아파치(또는 Nginx) 웹서버
- <strong>M</strong>ySQL 또는 MariaDB - 데이터베이스 관리 시스템
- <strong>P</strong>HP 또는 Perl 또는 Python - 스크립트/프로그래밍 언어

이 조합이 전형적으로 많이 쓰이게 되었고, 이것이 변형되어 다른 조합들도 생겨났다. LAPM의 변종에는 WAMP, WIMP, MAMP, SAMP, FAMP, iAMP 등이 있다.


## Apache 설치(v.2.4.7)

Rocky Linux에서 작업할 거니까, VirtualBox를 실행하고 저번에 설치했던 Rocky Linux를 켠다.


### 1. 필요한 유틸리티 설치
 
yum을 이용하여 아파치 설치 및 실행에 필요한 유틸리티들을 먼저 설치해주자.

(이런 유틸리티들은 어느 경로에서 설치하든 무관한 것 같아서 그냥 루트경로에서 설치해줬다)

최종적으로 아래 명령어로 설치했다.

<strong>yum -y install wget cmake ncurses-devel libtool libtool-ltdl expat-devel pcre-devel openssl-devel gcc gcc-c++ autoconf</strong>

![image](https://user-images.githubusercontent.com/112684409/226160364-cb0ecb88-36e8-4d91-bdfb-0e7b59b2d3ba.png)

설치가 잘 되었다.


* 참고 - yum 에서 다운로드 가능한 패키지 검색 방법: yum list 패키지이름

아래 예시처럼 *yum list 패키지이름* 을 치고 엔터를 누르면 yum으로 다운로드 받을 수 있는 패키지들의 목록을 확인할 수 있다.

![image](https://user-images.githubusercontent.com/112684409/226160163-47a7af72-00b0-40c5-a820-34d77bd827f9.png)

* 참고 - yum 명령어 옵션 y
- y: 다음 나올 선택지에 대해 모두 yes 처리(yum install 시 y 옵션을 주면 설치하시겠습니까? 등의 물음에 모두 자동으로 y 한다.)


### 2.  아파치 패키지 설치

아파치 설치 시 설치해야 하는 패키지에는 4종류가 있다. 

apr, apr-util, pcre, httpd 이렇게 4가지를 받아야 하는데, 각각 wget으로 웹서버에 접속하여 tar 파일을 다운로드 받은 다음 압축을 해제하고 설치해줄 것이다.

유틸리티 말고, 앞으로 설치할 패키지(아파치, MySQL, PHP)들은 모두 /usr/local/src 경로에 설치해주도록 하겠다.

위에서는 그냥 root 경로에 있었는데, cd 명령어로 아파치 패키지를 설치할 디렉토리로 이동해준다.

![image](https://user-images.githubusercontent.com/112684409/226160506-449f9918-ad9f-47ab-99cf-8edbba094c99.png)


#### apr-1.6.5 설치

아래 명령으로 apr tar파일을 다운로드 받는다.

<strong>wget http://mirror.apache-kr.org/apr/apr-1.6.5.tar.gz</strong>

![image](https://user-images.githubusercontent.com/112684409/226160529-57f0dd19-70b3-44d4-ac62-21c2221ea3e2.png)

아래 명령으로 tar 파일을 압축 해제한다.

<strong>tar zxvf apr-1.6.5.tar.gz</strong>

![image](https://user-images.githubusercontent.com/112684409/226160786-6e7f0a8d-f9c8-4e67-8353-d4d06f3b8ade.png)

디렉토리를 이동해서

<strong>cd apr-1.6.5</strong>

아래 명령으로 빌드 환경을 구축한다

<strong>./configure --prefix=/usr/local/apr</strong>

<strong>make</strong>

아래 명령으로 설치한다

<strong>make install</strong>


apr 1.6.5버전 설치 완료.


#### apr-util-1.6.3 설치

다시 /usr/local/src 디렉토리로 이동해서

<strong>cd ..</strong>

아래 명령으로 apr-util 1.6.3버전 설치

<strong>wget http://mirror.apache-kr.org/apr/apr-util-1.6.3.tar.gz</strong>

아래 명령으로 압축 풀고

<strong>tar zxvf apr-util-1.6.3.tar.gz</strong>

디렉토리를 이동해서

<strong>cd apr-util-1.6.3</strong>

아래 명령으로 빌드 환경을 구축한다

<strong>./configure --prefix=/usr/local/apr-util --with-apr=/usr/local/apr</strong>

<strong>make</strong>

아래 명령으로 설치한다

<strong>make install</strong>


#### pcre-8.45 설치

아래 명령으로 pcre 8.45버전 패키지를 다운로드

<strong>wget https://sourceforge.net/projects/pcre/files/pcre/8.45/pcre-8.45.tar.gz/download</strong>

아래 명령으로 압축 풀기

<strong>tar zxvf pcre-8.45.tar.gz</strong>

디렉토리를 이동해서

<strong>cd pcre-8.45</strong>

아래 명령으로 빌드 환경을 구축한다

<strong>./configure --prefix=/usr/local/pcre</strong>

<strong>make</strong>

아래 명령으로 설치한다

<strong>make install</strong>


#### httpd-2.4.56 설치

다시 /usr/local/src 디렉토리로 이동해서

<strong>cd ..</strong>

아래 명령으로 httpd 2.4.56버전 패키지를 다운로드

<strong>wget https://downloads.apache.org/httpd/httpd-2.4.56.tar.gz</strong>

아래 명령으로 압축 풀기

<strong>tar zxvf httpd-2.4.56.tar.gz</strong>

디렉토리를 이동해서

<strong>cd httpd-2.4.56</strong>

아래 명령으로 빌드 환경을 구축한다

<strong>./configure --prefix=/usr/local/apache --with-apr=/usr/local/apr --with-apr-util=/usr/local/apr-util --with-pcre=/usr/local/pcre --enable-mods-shared=all --enable-so --enable-rewirte --enable-auth-digest</strong>

(make에 몇 분 걸림)

<strong>make</strong>

아래 명령으로 설치한다

<strong>make install</strong>


설치 완료!


### 3. 아파치 설정파일 수정

httpd.conf 파일은 아파치의 주요 설정 내용이 작성되어있는 파일이다. 이 파일을 조금 수정할 것이다.

우선 파일이 위치한 경로를 찾아보자.

cd

find / -name httpd.conf

![image](https://user-images.githubusercontent.com/112684409/226162581-7b11ac61-8996-416a-90e7-6cb881bc2136.png)

위 ./configure 과정에서 --prefix에 경로 설정을 /usr/local/apache 로 잘 해주었다면

/usr/local/apache/conf/httpd.conf 이 httpd.conf 파일의 경로로 확인될 것이다.

vi 편집기로 파일을 열어보자.

vi /usr/local/apache/conf/httpd.conf

![image](https://user-images.githubusercontent.com/112684409/226162645-6efd2325-e5da-4cdc-886d-825489828190.png)

vi 파일을 열면 기본은 읽기모드 같은 모드로 열린다.

a 를 눌러 편집모드로 전환하고

ServerName 부분을 찾아 (/ 또는 ? 를 입력하면 키워드로 검색 가능, 검색 결과에서 n을 누르면 다음 검색 결과로 이동, N을 누르면 이전 검색 결과로 이동)

![image](https://user-images.githubusercontent.com/112684409/226162795-2b53d8ed-36ca-481e-b982-185ac84dd65f.png)

ServerName localhost:80 으로 변경해주고

(# 표시는 주석 표시이므로, 나는 기존에 주석처리 되어있던 부분은 그냥 두고 아랫줄에 추가해줬다)

![image](https://user-images.githubusercontent.com/112684409/226162951-f33a47de-ca2f-4873-ab8f-6a319f7eee79.png)


그 다음, Require all denied 로 되어있는 부분을 Require all granted 로 수정

![image](https://user-images.githubusercontent.com/112684409/226163089-0c721951-2e91-48e5-8605-5ecff4e26a03.png)

(참고로, 편집기 읽기모드에서 :set number 를 입력하면 라인 넘버가 보인다)

esc를 눌러 편집모드에서 빠져나오고

:w 를 눌러 파일 저장

:q 를 눌러 편집기를 종료한다.



### 4. 아파치 실행

아파치 시작

/usr/local/apache/bin/httpd -k start

아파치 확인

ps -ef | grep httpd


curl localhost

위 명령을 입력한 결과

<html><body><h1>It works!</h1></body></html>

이렇게 뜨면 설치완료.


아파치 중지

/usr/local/apache/bin/httpd stop



끝!!! 

<br />
<br />

다음 포스팅에서는 이어서 MySQL을 설치해보겠습니다~~ 😉


------------------------------------------------------------

## 부가설명

### Apache란?


### MySQL이란?


### Php란?


🛠 추후 작성 예정... 🛠


------------------------------------------------------------

👨‍🏫 참고자료

- [LAMP 스택이란 무엇인가요?](https://aws.amazon.com/ko/what-is/lamp-stack/)
- [위키백과 - LAMP](https://ko.wikipedia.org/wiki/LAMP_(%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4_%EB%B2%88%EB%93%A4))
- <>
- <http://mirror.apache-kr.org/>
- <https://sourceforge.net/projects/pcre/files/pcre/8.45/>
- <>


🙂 내용 중 잘못된 부분이 있을 경우 알려주시면 감사 드리겠습니다. 


