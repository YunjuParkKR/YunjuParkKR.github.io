---
layout: single
title: "🐧 OS 🐧 VirtualBox에 Rocky Linux 설치방법 "
categories: OS
tag: [블로그, 코딩, 깃허브, 깃허브블로그, 포스트, 운영체제, OS, 가상머신, virtualbox, 리눅스, linux, rockylinux, 로키리눅스]
toc: true
toc_sticky: true
toc_label: 목차
published: true
---

**[OS]** Rocky Linux의 개념과 설치방법

이번 포스트에서는 지난번 설치한 VirtualBox에 Rocky Linux를 설치해볼 것이다.

나의 설치환경은 Windows10, Oracle VirtualBox 이다.

🔻 VirtualBox 설치방법

<https://yunjuparkkr.github.io/os/virtualbox/>


## Linux

### Linux(리눅스)란?

UNIX 클론 계열 오픈소스 프리웨어 운영 체제로, 누구나 무료로 사용할 수 있으며, 자유롭게 수정 및 배포, 상업적 이용까지 가능한 운영체제이다.

(처음에 리누스 토발즈라는 핀란드 대학생이 취미로 만든 거라고 하는데 정말정말... 대단하다...)

안정화된 UNIX 운영체제를 기반으로 하기 때문에 Linux 또한 안정적이라고 하며, 기본적으로는 필수 기능만을 제공하고 나머지 기능은 필요시 선택적으로 사용할 수 있다. 

기본 기능만을 제공하기 때문에, 사용자가 Linux를 사용하기 위해서는 Linux 커널을 다운로드 받아 컴파일하고, 필요한 각종 패키지를 모두 따로 다운로드 받아서 설치해줘야 한다고 한다. 이는 매우 번거로울 것이다.


따라서 많은 단체에서 Linux를 자체적으로 패키지화하여 만들어냈다. 

그렇게, 지금까지 Ubuntu Linux, CentOS Linux, Rocky Linux, RedHat Linux, Oracle Linux, Fedora Linux, Kali Linux, Suse Linux, Debian CNU Linux, Arch Linux, PCLinuxOS, Vector Linux 등 수많은 배포판이 탄생했다.

이 중 많이 사용되는 배포판은 Debian GNU Linux, Ubuntu Linux, RedHat Linux, CentOS 라고 한다.


리눅스의 장단점, 그리고 각 배포판의 특징과 장단점 등은 다음에 알아보기로 하고, 오늘은 내가 설치할 Rocky Linux에 대해 정리해볼 것이다.



## Rocky Linux

### Rocky Linux란?

전세계에서 큰 점유율을 차지하고 있던 CentOS가 CentOS Stream으로 전환되어 독립적인 배포판으로 개발될 것임이 발표되었다.

CentOS는 RedHat의 기능을 DownStream하여 무상으로 사용할 수 있는 리눅스였으나, CentOS 8부터 Uptream으로 전환되어, 테스트베드같은 존재로 변화하여 보안성이 떨어졌고, 앞으로는 무료 OS에서 제외될 예정이라고 한다. 

(CentOS 7의 지원 기간은 2024년 6월 30일까지, CentOS 8의 지원 기간은 2021년 12월 31일까지)


이에, CentOS를 대체하기 위해 CentOS 프로젝트의 공동설립자 중 한 명이 나와 다른 설립자와 새롭게 만든 배포판이 Rocky Linux이다. 

2021년 11월에 발표되었고, 엔터프라이즈급 리눅스와 동일한 것을 누구나 무료로 사용할 수 있도록 하여, 현재 거대 IT기업들의 지지를 받으며 입지를 차지하고 있다고 한다.


Rocky Linux의 버전은 8.0(Green Obsidian / RHEL 8 기반)에서 시작하여, 현재 9.1(Blue Onyx / RHEL 9 기반) 까지 배포되었다.


성능적으로 이슈가 없다면, 앞으로 Rocky Linux도 Ubuntu와 함께 높은 점유율을 차지할 수 있지 않을까~ 😏



### 최소 시스템 요구사항

- RAM 2GB 이상
- harddisk 20GB 이상
- 2 CPU / vCPUs


### Rocky Linux 9.1 설치방법 (9.1 버전)

1. iso파일 다운로드
 
아래 주소로 접속하여 필요한 버전을 다운로드 받는다. 

<https://rockylinux.org/ko/download>

나는 x86_64 아키텍처의 Minimal ISO를 다운로드 받았다. 용량 애껴...

내 컴퓨터의 CPU가 인텔 기반이기 때문에 x86_64를 다운받았고, ARM64 기반이라면 ARM64 파일을 다운받으면 된다.

dvd는 전체 페키지가 들어있는 약 10GB 이하의 파일이고, 

minimal은 CLI(서버용으로 만들어진 가벼운 버전으로 그래픽인터페이스가 없음) 버전인 1.5GB짜리 파일이다. 

최소한으로 필요한 것들만 받기 위해 Minimal 버전을 받은 것이다. 

![image](https://user-images.githubusercontent.com/112684409/224479382-567f8f6a-7bbf-44ff-ae0f-a4648d4b57b2.png)


(그런데... ?? 1.5기가짜리 zip파일인데 다운로드 받는 데에 6시간 걸린다고 뜨는 거 실화인지...? 😭)

다운로드 속도가 느린 데에는 여러 원인이 있을 수 있겠지만... 컴퓨터나 네트워크에 특별한 문제가 없다면 아래 방법을 사용하면 되겠다.


공식 사이트 외에 Rocky Linux를 다운로드 받을 수 있는 미러사이트들이 있다. 다운로드 시간을 단축하고 싶다면 아래 사이트를 활용하자.

[Rocky Linux Mirror List 사이트] (https://mirrors.rockylinux.org/mirrormanager/mirrors/Rocky)

위 링크에 접속하면 나오는 사이트들 중 한국 미러 사이트는 YJSoft와 AniGil Linux Archive가 있다고 한다.

둘 중 아무 사이트에나 들어가서 필요한 파일을 다운받으면 된다.


아래와 같이 다운로드 되었다.

![image](https://user-images.githubusercontent.com/112684409/224488690-e52a1450-7238-4b66-93fe-55afd29d7e7b.png)


2. VirtualBox를 실행하여 가상머신(Virtual Machine, VM) 생성

<details>
  <summary>🤦‍♀️ 첫 번째 실패 기록</summary>

  VirtualBox에서 새로만들기를 클릭하여 새로운 VM 생성

  ![image](https://user-images.githubusercontent.com/112684409/224488813-b55cafec-50d5-47e0-aadd-3b92d360bb86.png)


  먼저 Name and Operating System 탭.

  새로 생성할 가상머신의 이름을 지정해준다. 나는 RockyLinux라고 지었다. (띄어쓰기는 없애줌)

  ![image](https://user-images.githubusercontent.com/112684409/224489211-d490237e-1875-4ee5-9d45-0f232760702b.png)

  Folder는 기본으로 설정되어있는 곳으로 진행했고,

  내가 예전에 써봤던 VirtualBox와 버전이 달라서 그런지는 모르겠는데, 그 때는 지금 단계에서 ISO image를 선택하는 게 아니라, 가상머신을 생성한 후에 Configure 메뉴에서 따로 설정해줬던 것 같은데,

  지금 사용하는 최신 버전의 VirtualBox(v.7.0.6)에서는 ISO image를 선택하는 란이 여기에 바로 있어서, 

  위에서 다운로드 받았던 Rocky Linux 의 minimal 버전 iso파일을 한번 선택해보았다.

  ![image](https://user-images.githubusercontent.com/112684409/224489347-037dcf56-ba1f-458c-9e9d-215a182b9a74.png)


  ![image](https://user-images.githubusercontent.com/112684409/224490026-92114b0b-922c-43c3-ab2f-d0f16752b75d.png)

  Rocky Linux iso 파일을 선택하고 나면 자동으로 종류가 Linux로, 버전이 Red Hat (64-bit)로 설정된다.

  Rocky Linux도 RedHat(RedHat Enterprise Linux, 이하 RHEL)을 기반으로 만들어졌기 때문에 RedHat으로 선택해도 무방한가보다. 

  (예전에 사용했던 VirtualBox에서는 리눅스 이름을 Rocky Linux로 설정하면 자동으로 가상머신의 버전이 Linux 2.6 / 3.x / 4.x / 5.x (64-bit)로 설정되었는데, 이번엔 Red Hat으로 자동설정되네?)


  다음으로 Unattended Install 탭.

  ![image](https://user-images.githubusercontent.com/112684409/224489536-b5d7530a-409d-41e6-9a40-c74b9fdf083b.png)

  기본으로 위 사진과 같이 입력되어 있는데, 나는 Username과 Password를 바꿔줬다.

  ![image](https://user-images.githubusercontent.com/112684409/224490073-6c328826-ca06-4a1e-b8d7-1c2f67df4331.png)


  다음으로 Hardware 탭.

  ![image](https://user-images.githubusercontent.com/112684409/224489675-7cf5c597-1b23-4e44-a5e8-c41edad81d30.png)

  기본적으로 위 사진과 같이 입력되어 있는데, 나는 기본 메모리는 그대로 2048MB로 뒀고, Processors는 CPU 2개로 수정해주었다.

  ![image](https://user-images.githubusercontent.com/112684409/224490148-afa6420d-acd9-4840-a052-91fe920c5a77.png)


  다음으로 Hard Disk 탭.

  ![image](https://user-images.githubusercontent.com/112684409/224489778-c77d5732-92ea-4e26-9055-b988d82fcba4.png)

  기본적으로 위 사진과 같이 입력되어 있는데, 나는 Create a Virtual Hard Disk Now 선택과 Hard Disk File Location은 그대로 두고, Size만 50GB로 늘려주었다.

  또, Hard Disk File Type을 VHD(가상 하드 디스크)로 변경했고, 고정 크기로 만들기 위해 Pre-allocate Full Size에 체크해주었다.

  ![image](https://user-images.githubusercontent.com/112684409/224490137-14b501ad-a327-43eb-9363-774e9ab93dff.png)



  참고로, 하단의 가이드 모드 버튼을 누르면 아래와 같이 각 탭의 내용을 단계별로 설정할 수 있도록 바뀐다.

  ![image](https://user-images.githubusercontent.com/112684409/224490215-b8c82e68-44ba-45b0-a70b-79d32fa48f25.png)

  단계별로 설정 후 내용을 요약해서 보여준다.

  ![image](https://user-images.githubusercontent.com/112684409/224490445-9fb19de7-8d11-4622-8325-47a691aaa0c4.png)


  zz 근데 에러남.. 역시 한 번에 잘 될 리가 없지~

  에러 원인은 디스크 용량 부족인 듯하다. ^^ ........

  ![image](https://user-images.githubusercontent.com/112684409/224490830-f9853241-1fbf-4127-aef0-a86ac171b0aa.png)
  
</details>


VirtualBox에서 새로만들기를 클릭하여 새로운 VM 생성 (VirtualBox 설치 후 자동으로 생겼던 CentOS8은 삭제해준 상태에서 진행)

![image](https://user-images.githubusercontent.com/112684409/224531671-06097555-b459-4c9c-8c29-263287bc16fb.png)

이름에 RockyLinux라고 입력, Folder는 기본 설정 그대로 두고, ISO image는 위에서 다운로드 받았던 Rocky Linux minimal버전 iso 파일을 선택해봤다.

그러면 Edition, 종류, 버전은 RedHat(64-bit)로 자동 지정되고, 변경할 수 없도록 된다. 다음 버튼을 클릭.

![image](https://user-images.githubusercontent.com/112684409/224531752-ad6afa0f-6f39-4aef-8afc-124b1429cae4.png)

다음 단계. 아래 내용은 기본적으로 입력되어 있는 내용인데,

![image](https://user-images.githubusercontent.com/112684409/224531793-288a37b1-c443-43ff-b962-4b39f8d7af22.png)

나는 Username, Password, Repeat Password 부분만 아래와 같이 변경해줬다.

![image](https://user-images.githubusercontent.com/112684409/224531819-f5466cf5-14e5-47b7-b62b-66c0cda39817.png)

다음은 RAM과 CPU 설정 부분인데, 

![image](https://user-images.githubusercontent.com/112684409/224531853-b2a93231-8742-42f0-a1ae-35a14d5304ec.png)

나는 RAM은 기본 설정 2048MB로 그대로 두고, CPU는 2개로 변경해줬다.

![image](https://user-images.githubusercontent.com/112684409/224531891-8395e8a8-1a97-40a5-b23c-36f6f102c6be.png)

다음은 가상 하드디스크를 설정하는 부분인데, 

![image](https://user-images.githubusercontent.com/112684409/224531930-405411b0-d9e1-4b6a-93e2-c50a2ba87187.png)

나는 Create a Virtual Hard Disk Now 선택은 그대로 두고, Disk Size는 40GB로 수정, Pre-allocate Full Size에 체크해주었다.

![image](https://user-images.githubusercontent.com/112684409/224531972-1fc6923a-ae19-4a5d-becb-bfe6b44db24b.png)

다음을 클릭하면 지금까지의 설정 내용을 보여준다. Finish를 클릭.

![image](https://user-images.githubusercontent.com/112684409/224531992-b2a5f2a1-1403-4efe-9476-31cd4937d481.png)

그러면 가상 머신 생성이 시작된다.

![image](https://user-images.githubusercontent.com/112684409/224532019-ecc8d190-682e-4b23-8712-4cdacf19169b.png)

![image](https://user-images.githubusercontent.com/112684409/224532192-6d2d7894-f070-4d14-afc1-cafd73a8f018.png)

(음... 생각보다 오래걸리네..~? ^^...)

![image](https://user-images.githubusercontent.com/112684409/224532221-9daa91d3-02da-4040-8ef0-55fa6fa54a91.png)

드디어 가상머신 생성 완료!!

생성된 가상머신이 클릭된 상태로 설정 버튼 클릭 > 저장소 탭에 들어가서

![image](https://user-images.githubusercontent.com/112684409/224532294-6f4847fd-00fc-4f88-885a-3e63e09595b8.png)

컨트롤러: IDE 부분 속성 - 광학 드라이브 옆 CD아이콘을 눌러, 위에서 다운로드 받았던 Rocky Linux minimal.iso 파일을 선택해준다.

![image](https://user-images.githubusercontent.com/112684409/224532353-a1a41d31-5265-4ca6-8e30-654d679aa686.png)

확인 버튼을 누르고, 표시 버튼을 눌러 가상머신을 실행해보자.

![image](https://user-images.githubusercontent.com/112684409/224532741-d14731bb-0086-40fe-aca4-de74ae0ec57f.png)

오~ 에러다... 

또 한번 쿨하게 삭제해준다^^

![image](https://user-images.githubusercontent.com/112684409/224532861-2ee45c60-ba40-45e6-822a-60f5aff3dd7b.png)


ㅠㅠ 나중에 재시도 할 예정...



<br/>
<br/>
<br/>


포트포워딩 설정은 나중에 할 것임......  

다음으로, 설정 - 네트워크 탭에서 포트 포워딩 버튼을 눌러

![image](https://user-images.githubusercontent.com/112684409/224532386-4b29431f-ab3e-4a69-886f-9257794dfc97.png)

우측의 + 아이콘을 눌러 새로운 규칙을 하나 생성해주고

![image](https://user-images.githubusercontent.com/112684409/224532540-d16f614b-ad33-4a04-9e59-1c045d1e9b99.png)

아래와 같이 설정해준다.

- 호스트 IP: 서버 PC의 IP (메인 아이피)
- 호스트 포트: 서버 PC에 할당할 포트 (서버 PC에서 중복된 포트가 없도록 변경 필요함)
- 게스트 IP: 가상머신 내 IP
- 게스트 포트: 가상머신에서의 포트






<br/>
<br/>
<br/>

음 근데 개인적으로 VirtualBox 예전 버전보다 최신 버전이 그래픽이 더 옛스러운(?) 느낌이 나는 것 같다... 😂


3. Rocky Linux 설치

<br/>
<br/>

🛠 작성 중 🛠

<br/>
<br/>



이어서 Rocky Linux에 개발환경을 구축해보고자 한다.

다음 포스트에서 이어집니다~


------------------------------------------------------------
<hr/>
## 부가설명

### .iso 파일이란?

추후 작성 예정...


------------------------------------------------------------
<hr/>

👨‍🏫 참고자료

- <[https://ko.wikipedia.org/wiki/%EA%B0%80%EC%83%81_%EB%A8%B8%EC%8B%A0](https://ko.wikipedia.org/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4)>
- <>
- <https://phoenixnap.com/kb/rocky-linux-virtualbox>
- <https://www.linuxquestions.org/questions/>
- [포트 포워딩 설정](https://devlifetestcase.tistory.com/69)


🙂 내용 중 잘못된 부분이 있을 경우 알려주시면 감사 드리겠습니다. 


