---
layout: single
title: "💻 저장소 💻 로컬 메이븐 레포지토리 Maven Repository .m2 폴더 용량 줄이기 "
categories: OS
tag: [블로그, 코딩, 깃허브, 깃허브블로그, 포스트, 메이븐, 저장소, 레포지토리, maven, repository, .m2, .cache, 컴퓨터용량관리]
toc: true
toc_sticky: true
toc_label: 목차
published: true
---

**[저장소]** local Maven Repository .m2 폴더 용량 줄이기

.m2 폴더가 내 컴퓨터 용량을 너무 많이 차지해서 컴퓨터 사용에 지장이 있었다. 🤦‍♀️ 

이번 포스트에서는 .m2 폴더에서 삭제해도 되는 부분을 삭제하여 컴퓨터 저장소 용량을 확보해볼 것이다.



## Local Maven Repository란?

### Local Repository (로컬 저장소)

Local Repository, 즉 로컬 저장소란, 현재 내가 사용하고 있는 내 디바이스(PC)에 저장되는 저장소를 말한다. 

내 컴퓨터에 있는 폴더를 말하는 것이다.


### Maven Repository (메이븐 저장소, Maven Global Repository) - 여기서는 메이븐 중앙 저장소를 말함

Maven Repository, 즉 메이븐 중앙 저장소란, 오픈 소스 라이브러리와 메이븐 플러그인 그리고 메이븐 아키타입을 관리하는 아파치 재단에서 운영하는 저장소이다. 

라이브러리를 공유하는 파일 서버라고 볼 수 있고, <https://mvnrepository.com/> 에 접속하여, 개발할 때 필요한 라이브러리들을 다운로드 받아 사용할 수 있다.

메이븐 중앙 저장소에는 개발자가 임의로 라이브러리를 배포할 수는 없다. 

![image](https://user-images.githubusercontent.com/112684409/224528735-b33b2d82-792d-483c-a6e1-44d1fa55618a.png)


설명 방식에 따라 메이븐 저장소를 세 가지(중앙 저장소, 원격 저장소, 로컬 저장소)로 나누어 설명하기도 한다.


### Local Maven Repository (로컬 메이븐 저장소)

Maven 설치 시 maven artifact들을 저장 및 관리하는 repository가 로컬에 자동으로 구성된다. 로컬 메이븐 저장소는 이를 말하는 것이다.

기본적으로는 C:\Documents and Settings\Administrator\.m2\repository 경로의 디렉토리에 구성되며, settings.xml에 원하는 경로를 지정하면 사용자가 변경도 가능하다.

pom.xml의 Dependencies에서 필요한 라이브러리를 추가하게 되면 네트워크를 통해 메이븐 글로벌 저장소에서 라이브러리와 해당 라이브러리 작동에 필요한 하위 라이브러리들를 내 컴퓨터의 로컬 메이븐 저장소에 cache(즉, 내 컴퓨터에 다운로드)하고, 로컬 메이븐 저장소의 라이브러리들로 클래스패스를 지정하여 프로젝트에서 사용하게 된다.

일반적으로는 개발 시 사용되는 라이브러리들을 모두 프로젝트 내부 디렉토리에 담고 경로를 설정하여 사용해야 하지만, 메이븐을 사용할 시 pom.xml에서 의존성 설정을 통해 라이브러리들을 사용 및 관리하는 것이다.


<span style="display: none;">

## Local Maven Repository의 구조

### 


### 

</span>


## .m2\repository\.cache 내의 폴더 삭제

.m2\repository\.cache\m2e\1.16.0 에 있는, 업데이트 되는 index 파일들을 모아놓은 폴더를 정기적으로 삭제해주면 용량을 많이 확보할 수 있다고 한다. 

![image](https://user-images.githubusercontent.com/112684409/224526741-1d0d1d42-9869-4671-8afc-aae572826890.png)

용량을 무려 25.5GB나 차지하고 있었다.

![image](https://user-images.githubusercontent.com/112684409/224526750-d464d3ee-ce3a-4bb1-9d98-221b2046121c.png)

해당 폴더 내부에는 이런 파일, 폴더가 있고

![image](https://user-images.githubusercontent.com/112684409/224526814-e3d3fa07-3c2b-4864-bcde-cd90d3be855c.png)

나는 이 05b0fe8524860bd73cbb07ef30fb34cc라는 폴더를 통째로 삭제해볼 것이다.


![image](https://user-images.githubusercontent.com/112684409/224526973-e919b2f4-351a-4aa6-8ec0-4f7ddf847381.png)

삭제완료.


삭제 후 sts를 다시 한번 실행해보았다.

sts 실행은 문제없이 잘 되고, 기존에 만들어 톰캣 서버에 올려둔 프로그램도 잘 작동하고,

pon.xml의 Dependencies 탭에서 Add 버튼을 눌러 Dependency 검색도 해봤는데 Repository search도 잘 되는 것 같다.

![image](https://user-images.githubusercontent.com/112684409/224528216-f21c41ad-4663-43b3-9aa4-c1e9d60dc1a1.png)

![image](https://user-images.githubusercontent.com/112684409/224528277-77d3dd02-c99d-48c0-8001-9921997d0a5e.png)



### dependency 추가 시 repository search 불가 해결방법

만약, 위에서 .m2\repository\.cache 하위 폴더를 삭제한 이후 디펜던시 추가할 때 repository search가 안 되면,

STS를 종료하고, 워크스페이스 폴더 아래에 있는 .metadata\.plugins\org.eclipse.m2e.core\nexus 내부의 파일들을 모두 지우면 된다고 한다.

![image](https://user-images.githubusercontent.com/112684409/224526920-c5204455-39a5-49cc-ba11-0c91b9dbf2c6.png)


(난 아직 repository search에 문제가 발생하지 않아서 위 방법은 시도해보지 않았음)



😬 과연 앞으로 아무 문제가 없을지... 사용하면서 지켜봐야겠다


------------------------------------------------------------

👨‍🏫 참고자료

- <https://offbyone.tistory.com/163>
- <https://cheershennah.tistory.com/151>
- <https://cornswrold.tistory.com/224>


🙂 내용 중 잘못된 부분이 있을 경우 알려주시면 감사 드리겠습니다. 


