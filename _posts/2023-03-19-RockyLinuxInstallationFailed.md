---
layout: single
title: "🐧 OS 🐧 VirtualBox에 Rocky Linux 설치 실패 사례 모음(오류 모음) "
categories: OS
tag: [블로그, 코딩, 깃허브, 깃허브블로그, 포스트, 운영체제, OS, 가상머신, virtualbox, 리눅스, linux, rockylinux, 로키리눅스, 에러, 에러모음, 실패모음]
toc: true
toc_sticky: true
toc_label: 목차
published: true
---

**[OS]** Rocky Linux 설치 실패 기록

리눅스의 ㄹ 자도 몰랐던 사람이라 이번에 Rocky Linux를 설치하면서도 실패를 반복했는데... 

어떻게 실패했는지 기록해뒀던 내용은 포스팅하고자 한다.. ^ -^...

나의 설치환경은 Windows10, Oracle VirtualBox 이다.


🔻 VirtualBox 설치방법

<https://yunjuparkkr.github.io/os/virtualbox/>


🔻 Rocky Linux 설치방법 (성공사례)



### Rocky Linux 9.1 설치 실패 모음 (9.1 버전)

#### 1. iso파일 다운로드
 
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



#### 2. VirtualBox를 실행하여 가상머신(Virtual Machine, VM) 생성

##### 🤦‍♀️ 첫 번째 실패

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


##### 🤦‍♀️ 두 번째 실패

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

마우스 오른쪽 버튼 > 삭제 > 모든 파일 지우기 ^^

![image](https://user-images.githubusercontent.com/112684409/224532919-38793527-a9de-4925-bf4d-9f974b1df352.png)


##### 🤦‍♀️ 세 번째 실패..까진 아니고 작은 실수

![image](https://user-images.githubusercontent.com/112684409/226153853-dff9aa4a-2b2c-428b-8774-a59c08bfb4e6.png)

가상머신 생성완료.

설정 해야 하는 거 깜빡하고 그냥 실행해서 오류남 ㅋ

![image](https://user-images.githubusercontent.com/112684409/226153881-dcff4a63-b535-4048-bf96-2adb5a638f4c.png)

시작 전에 설정해줄 게 있다.

설정 > 저장소 > 저장 장치 부분의 컨트롤러 IDE 아래 비어 있는 디스크 클릭 > 오른쪽 디스크모양 아이콘 클릭해서 디스크 선택

![image](https://user-images.githubusercontent.com/112684409/226153925-704cc1bd-9c26-4f50-bba9-1d34248589e3.png)

다운받아뒀던 Rocky Linux 9 의 minimal 버전 iso 파일을 선택해줌

![image](https://user-images.githubusercontent.com/112684409/226153954-c2f883ef-2edf-447e-b739-9cfb80605019.png)

적어도 여기까지는 설정하고 시작해야 오류가 발생하지 않고 가상머신이 잘 실행된다~


------------------------------------------------------------

내가 캡처해둔 실패 케이스는 여기까지지만, 기록해둔 것 말고도 엄청 많은 실패가 있었다.

지금 생각해보면 대체 왜 그런 실수를 했을까, 내가 리눅스에 대해 몰라도 너무 몰랐구나 싶지만

그런 생각이 든다는 건 어쨌든 지금 나는 이전의 나보다는 좀 더 알게 된 게 많다는 뜼이겠지...? 😂

파이팅하자..!!!

------------------------------------------------------------


🙂 내용 중 잘못된 부분이 있을 경우 알려주시면 감사 드리겠습니다. 


