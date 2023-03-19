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



2. VirtualBox를 실행하여 가상머신(Virtual Machine, VM) 생성 및  설정


새로운 마음으로 다시 시작... 랩탑 용량이 딸릴 것 같아서 외장하드에 설치해볼 것임.

![image](https://user-images.githubusercontent.com/112684409/226152904-e7e97494-efbc-4f80-b97b-c8f94716edf0.png)

![image](https://user-images.githubusercontent.com/112684409/226153571-f3d1c517-76e5-43dc-a011-171beea06d57.png)

![image](https://user-images.githubusercontent.com/112684409/226153515-8b37c521-12e3-43a1-a1a1-c81617b44c12.png)

![image](https://user-images.githubusercontent.com/112684409/226153579-30915057-0827-4883-8f8b-68bef76b9d03.png)

![image](https://user-images.githubusercontent.com/112684409/226153585-fe6f0bad-01d9-4cdd-a983-e93618e851f8.png)

![image](https://user-images.githubusercontent.com/112684409/226153597-8ebb1509-804c-4fe0-be70-09eb9d30b25c.png)

![image](https://user-images.githubusercontent.com/112684409/226153853-dff9aa4a-2b2c-428b-8774-a59c08bfb4e6.png)

가상머신 생성완료.

설정 해야 하는 거 깜빡하고 그냥 실행해서 오류남 ^^;

![image](https://user-images.githubusercontent.com/112684409/226153881-dcff4a63-b535-4048-bf96-2adb5a638f4c.png)

시작 전 설정

설정 > 저장소 > 저장 장치 부분의 컨트롤러 IDE 아래 비어 있는 디스크 클릭 > 오른쪽 디스크모양 아이콘 클릭해서 디스크 선택

![image](https://user-images.githubusercontent.com/112684409/226153925-704cc1bd-9c26-4f50-bba9-1d34248589e3.png)

다운받아뒀던 Rocky Linux 9 의 minimal 버전 iso 파일을 선택해줌

![image](https://user-images.githubusercontent.com/112684409/226153954-c2f883ef-2edf-447e-b739-9cfb80605019.png)

포트포워딩 설정

![image](https://user-images.githubusercontent.com/112684409/226153981-ad5cde18-4ca3-4ff0-81ed-9f0daae12d64.png)

* 참고

- 호스트 IP: 서버 PC의 IP (메인 아이피)
- 호스트 포트: 서버 PC에 할당할 포트 (서버 PC에서 중복된 포트가 없도록 변경 필요함)
- 게스트 IP: 가상머신 내 IP
- 게스트 포트: 가상머신에서의 포트


음 근데 개인적으로 VirtualBox 예전 버전보다 최신 버전이 그래픽이 더 옛스러운(?) 느낌이 나는 것 같다... 😂



3. Rocky Linux 설치


아래와 같이 설정된 상태에서 시작 버튼을 눌러 가상머신 시작.

![image](https://user-images.githubusercontent.com/112684409/226154006-97c12d80-42fc-412e-ae6f-1919e921c15d.png)

시작됨

방향키로 Install Rocky Linux 9.1 을 선택(흰색 글씨가 선택된 것임) 후 엔터

![image](https://user-images.githubusercontent.com/112684409/226154038-1e69fbb3-e850-4b42-98c1-c1e67cbf4435.png)

설치되는 중...

![image](https://user-images.githubusercontent.com/112684409/226154067-13a66295-8542-4903-9ccb-ff9df84b3f37.png)

한국어 선택

![image](https://user-images.githubusercontent.com/112684409/226154086-0c35c491-7786-4246-80cc-f05642d00b15.png)

설정하자

root 비밀번호 설정

![image](https://user-images.githubusercontent.com/112684409/226154218-8ba1e55e-9600-4ef6-9816-8491e5e34632.png)

설치 목적지는 자동으로 선택되어 있는 곳으로 하겠음. 확인

![image](https://user-images.githubusercontent.com/112684409/226154147-07bd2520-6617-494d-a793-4e32fc903023.png)

이더넷은 켜져있어야 하고, Ipv4, Ipv6 자동으로 연결되도록 설정되어 있을 것임. 확인.

![image](https://user-images.githubusercontent.com/112684409/226154174-7cbda210-703e-461f-8996-96840f4a63fd.png)

이제 설치 시작을 눌러주자

![image](https://user-images.githubusercontent.com/112684409/226154195-4ad841c4-8d0b-4395-a950-e7721a51bd9e.png)

시간 꽤 걸림 (나는 보통 여기서 기다리는 데에 10분정도씩은 걸렸음...)

![image](https://user-images.githubusercontent.com/112684409/226154236-b588d4f7-db05-40c9-845c-e3df33a5fc10.png)

됐다! 시스템 재시작

![image](https://user-images.githubusercontent.com/112684409/226154502-5079491c-19c6-47e5-b148-fe2dcf823d2b.png)

아까 설정했던 루트 비밀번호로 로그인해준다

![image](https://user-images.githubusercontent.com/112684409/226154599-d10a5518-a7f4-47fd-a6e8-f950c0357985.png)

비밀번호를 입력할 때는 원래 화면에 안 나온다. 화면엔 안 보여도 입력되고 있는 거니 당황하지 말고 입력해주자. 틀려도 다시 입력하면 된다.

![image](https://user-images.githubusercontent.com/112684409/226154617-225f3857-4ebc-406c-a91c-ebefb120c5eb.png)

화면에 이렇게 보이면 로그인 성공, Rocky Linux 9 설치가 완료된 것이다! 

![image](https://user-images.githubusercontent.com/112684409/226154779-5fd65a1b-acb2-497c-814c-f74574dbdd9e.png)


Rocky Linux 9.1 버전 설치 끝!!! 

<br />
<br />


이어서 Rocky Linux에 개발환경을 구축해보고자 한다.

다음 포스팅에서 APM 환경을 구축해보겠습니다~~ 😉


------------------------------------------------------------
<hr/>
## 부가설명

### .iso 파일이란?

🛠 추후 작성 예정... 🛠


------------------------------------------------------------
<hr/>

👨‍🏫 참고자료

- <[https://ko.wikipedia.org/wiki/%EA%B0%80%EC%83%81_%EB%A8%B8%EC%8B%A0](https://ko.wikipedia.org/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4)>
- <>
- <https://phoenixnap.com/kb/rocky-linux-virtualbox>
- <https://www.linuxquestions.org/questions/>
- [포트 포워딩 설정](https://devlifetestcase.tistory.com/69)


🙂 내용 중 잘못된 부분이 있을 경우 알려주시면 감사 드리겠습니다. 


