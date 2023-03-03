---
layout: single
title: "📝 블로그 📝 깃허브 블로그 - utterances를 이용한 댓글 기능 추가 "
categories: blog
tag: [블로그, 코딩, 깃허브, 깃허브블로그, 댓글, 댓글기능추가, utterances]
toc: true
toc_sticky: true
toc_label: 목차
---

**[blog]** utterances를 이용한 댓글 기능 추가

내 깃허브 블로그에 댓글 기능을 추가해보자.


## utterances를 이용한 댓글 기능 추가 방법

### 1. 댓글기능을 위한 Repository 생성

깃허브에 접속하여 utterances와 연결할 새로운 Repository를 public으로 만들어 준다.

(댓글 기능에 사용할만한 레포지토리가 이미 있다면 존재하는 레포지토리를 사용해도 무방하다고 한다. 즉, 그냥 깃허브 블로그 레포지토리를 사용해도 무방한 것 같다.)

![image](https://user-images.githubusercontent.com/112684409/222730950-6a02ab4c-5354-4d50-a577-e8c3ecb5d971.png)

![image](https://user-images.githubusercontent.com/112684409/222731811-ec4ee0d0-31b4-4815-bad3-026feaf9f46e.png)



## 2. Utterances 설치

https://github.com/apps/utterances

위 주소에 접속하여 utterances를 Install 한다.

![image](https://user-images.githubusercontent.com/112684409/222732100-ebe1b705-0940-41b7-8288-140cf356f9f1.png)

이 때, 댓글이 달리면 모든 Repository의 Issue에 업로드되게 할지, 혹은 특정 Repository의 Issue에만 업로드되게 할지 선택할 수 있다. 

나는 새로 생성한 댓글용 레포지토리에만 업로드되도록 하기 위해 아래와 같이 'Only select repositories' 에 체크 후 해당 레포지토리를 선택해줬다.

![image](https://user-images.githubusercontent.com/112684409/222732473-4d939d11-1185-4e1b-b992-74fba5425daf.png)


## 3. configuration 설정

install 후 아래와 같은 페이지가 뜨는데, 

![image](https://user-images.githubusercontent.com/112684409/222733953-bc60fc7a-e05e-4bc7-b0fb-3577bc8d4e65.png)

아래 표시한 부분들을 작성해주면 된다.


- Repository

![image](https://user-images.githubusercontent.com/112684409/222734126-1bcb424d-0728-466e-aa20-6b7a686b4b49.png)

깃허브 username/repository이름 을 입력해준다.

여기서 repository는 위에서 댓글 Issue가 업로드될 곳으로 선택한 repository를 적으면 된다.


- Blog Post - Issue Mapping

![image](https://user-images.githubusercontent.com/112684409/222734474-841208da-165d-4f80-8e03-0f0d58096a82.png)

여기는 댓글 Issue를 블로그 포스트와 어떻게 매핑시킬지를 정하는 부분인데, 나는 첫 번째 선택지인 page pathname을 선택했다.

매핑시킬 key는 변경되지 않는 것이 좋으므로, 고유한 성질을 가지며 가장 변경될 확률이 낮은 pathname으로 선택하는 것이 좋다기에 나도 그렇게 했다.


- Theme

![image](https://user-images.githubusercontent.com/112684409/222735233-75efb316-8e25-4c64-aa6d-28c3bc5bd1ae.png)

테마 변경은 원하는 디자인으로 해주면 된다. 

나는 Photon Dark라는 테마를 선택했다.


- Enable Utterances

  1) minimal-mistakes를 사용 중인 경우
     : 깃허브 블로그의 _config.yml 파일 내에 아래와 같이 4가지 항목을 작성해준다.
     
     ![image](https://user-images.githubusercontent.com/112684409/222737002-eb57d7a6-bff0-4e07-aaea-93c8f5de93ff.png)
     
     repository: 댓글 Issue가 올라올 곳으로 선택한 그 repository의 permalink (username/repository)를 작성
     
     comments - provider: utterances 라고 작성
     
     utterances - Theme: 위에서 골랐던 테마. 나는 Photon Dark 선택
     
     utterances - issue_term: 위에서 정했던 맵핑 방법. 나는 pathname 선택


  2) 그 외의 경우
     : 아래 코드 부분을 복사하여 댓글 구현을 담당하는 html 파일에 붙여넣어주면 된다고... 한다....
     
     ![image](https://user-images.githubusercontent.com/112684409/222735511-198ba9ac-4a87-43c4-8806-5221de71229a.png)


이렇게 하고 Commit and Push 하여 서버에 반영하면 댓글기능 추가가 완료된다.

근데..

여기까지 했는데...

안 되잖아 ? ? ?

_config.yml 파일 하단의 comments: # true 부분이 문제였음. 

아래와 같이 # 을 지워줘야 댓글 기능이 적용된다! comments: true 가 되도록!

![image](https://user-images.githubusercontent.com/112684409/222740820-58223bb2-e3f3-42b9-a584-8e2fe921da1d.png)



이제 진짜 끝~

![image](https://user-images.githubusercontent.com/112684409/222744607-4d60e353-d24d-4c1e-aff9-9835064d6afc.png)



-----------------------------------------------


## utterences의 동작 원리

utterances는 깃허브 이슈를 기반으로 댓글을 달 수 있게 해주는 깃허브 앱.

utterances가 로드되면 깃허브의 issue search API를 사용하여 url, pathname, title을 기준으로 페이지와 관련된 이슈를 찾는다. 

만약 페이지와 일치하는 이슈가 없는 경우 utterances-bot이 자동으로 이슈를 생성해준다.

깃허브 계정 로그인을 통해 댓글을 달 수 있으며, 댓글이 달리면 Github Repository의 Issue로 알림이 오는 시스템이다.



## utterances의 장점

- 광고가 없다
- 댓글에 마크다운 문법을 사용할 수 있다
- 가볍고, 설치 및 설정이 쉽다
- Github Issue와 맵핑 할 수 있다면 어느 곳에서든 사용할 수 있다
- 댓글을 남기기 위해 별도 회원가입 등을 할 필요가 없다 (깃허브 계정만 있으면 된다)
- 댓글 알림을 받을 수 있다



-----------------------------------------------

🙂 내용 중 잘못된 부분이 있을 경우 알려주시면 감사 드리겠습니다. 


