---
layout: single
title: "💻 가상머신 💻 VirtualBox - Oracle VirtualBox의 개념과 설치방법 "
categories: OS
tag: [블로그, 코딩, 깃허브, 깃허브블로그, 포스트, 운영체제, OS, 가상머신, virtualbox]
toc: true
toc_sticky: true
toc_label: 목차
published: true
---

**[가상머신]** VirtualBox의 개념과 설치방법

가상머신(virtual machine, VM)이란, 컴퓨팅 환경을 소프트웨어로 구현한 것, 즉 컴퓨터 시스템을 가상현실화하는 소프트웨어라고 한다.

이번 포스트에서는 가상화 소프트웨어에 대해 간략히 알아보고, VirtualBox를 설치해볼 것이다.



## 운영체제 가상화 소프트웨어와 VirtualBox

### 가상화 소프트웨어

컴퓨터 운영체제를 가상환경에서 실행할 수 있도록 만들어주는 프로그램을 가상화 소프트웨어라고 한다.

운영체제 가상화 소프트웨어에는 Oracle의 VirtualBox, VMWare의 Workstation, Microsoft의 VirtualPC 등이 있는데, 

Workstation과 VirtualPC는 상용 소프트웨어인 반면, VirtualBox는 오픈소스 버전이다.

VirtualBox가 Workstation, VirtualPC에 비해 기능이 부족한 편이지만, 원격 데스크톱 프로토콜, iSCSI 등 원격으로 가상 컴퓨터를 제어하는 기능을 제공한다고 한다.


### VirtualBox란?

Oracle사에서 운영하는 가상화 소프트웨어로, Oracle VM VirtualBox를 말한다.

VirtualBox는 본래 이노텍이 개발했고, 2008년에 썬 마이크로시스템즈가 이노텍을 인수한 다음, 2009년 오라클이 썬 마이크로시스템즈를 인수함에 따라 

현재는 Oracle에서 운영하게 된 것이라고 다.


### VirtualBox 설치방법 (7.0.6버전)

아래 주소로 접속 혹은 검색포털에서 VirtualBox 검색 후 다운로드 페이지로 접속하고

<https://www.virtualbox.org/wiki/Downloads>

각자 컴퓨터에 맞는 설치파일을 클릭하여 다운로드 받는다. 

나는 Windows10을 사용 중이기 때문에 가장 첫번째에 있는 Windows hosts를 클릭하여 다운받았다. 

![image](https://user-images.githubusercontent.com/112684409/224475801-dd81294c-d9f6-48e3-a213-f074dc4156a2.png)

다운받은 후 파일을 더블클릭하여 실행해준다.

![image](https://user-images.githubusercontent.com/112684409/224475839-32a99ac9-e6bb-4c90-9e34-7b5659b1da98.png)

그러면 아래와 같이 설치파일이 실행된다. Next를 클릭.

![image](https://user-images.githubusercontent.com/112684409/224475858-f2fe10a6-f0a8-44ac-b5eb-a07992239a32.png)

나는 기본으로 설정되어 있는 부분을 변경하지 않고 그대로 설치해주었다. Next를 클릭.

![image](https://user-images.githubusercontent.com/112684409/224475875-6d7c1dca-5aad-4029-b22b-46538372419d.png)

Yes 클릭.

![image](https://user-images.githubusercontent.com/112684409/224475878-ede9ccf8-2030-4911-88b8-6d7774d0927f.png)

Yes 클릭.

![image](https://user-images.githubusercontent.com/112684409/224475918-805fce67-c814-4555-b4ce-4ed3ca5ca694.png)

Install 클릭.

![image](https://user-images.githubusercontent.com/112684409/224475931-11c2a1a2-e1c8-4bb3-a062-aeb2e3992d30.png)

설치되는 중...

![image](https://user-images.githubusercontent.com/112684409/224475942-c49aaa40-1902-4039-95bb-1f5668ce1c69.png)

설치가 완료되었다. 바로 VirtualBox를 실행해보겠다. 체크박스에 체크된 상태로 Finish 클릭.

![image](https://user-images.githubusercontent.com/112684409/224475957-7e4adcb3-ca15-4b57-b2d3-59d484b2917b.png)

그러면 VirtualBox 설치 끝!

아래와 같이 실행이 된다.

![image](https://user-images.githubusercontent.com/112684409/224475984-39653e3b-e7ca-46f3-a1eb-020c6cd0decd.png)


그런데 나는 CentOS8이 하나 기본으로 있고, 접근할 수 없음으로 뜨는데, 

이건 VirtualBox 몇 버전 이상 짜리를 설치하면 자동으로 CentOS8이 하나 생기게 되는 건가? 

왜 있는지 잘 모르겠다. 


아무튼, 나는 CentOS가 아닌 Rocky Linux를 설치해보려고 한다. 

다음 포스트에 이어집니다~


------------------------------------------------------------

👨‍🏫 참고자료

- <https://ko.wikipedia.org/wiki/%EA%B0%80%EC%83%81_%EB%A8%B8%EC%8B%A0>
- <https://ko.wikipedia.org/wiki/%EB%B2%84%EC%B6%94%EC%96%BC%EB%B0%95%EC%8A%A4>


🙂 내용 중 잘못된 부분이 있을 경우 알려주시면 감사 드리겠습니다. 


