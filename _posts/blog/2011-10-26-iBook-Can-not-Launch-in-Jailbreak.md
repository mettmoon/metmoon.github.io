---
layout: post
title: iOS5 탈옥 - iBooks 실행불가 버그 잡기
category: digital
tags: [jailbreak,iphone,ipad]

---

iOS5를 탈옥하시고 iBooks를 실행해보셨다면 앱이 크래쉬 나는 걸 볼거에요.

왜그런지는 이유는 모르겠고 해외에서 iH8sn0w 에서 방법을 공개했네요. 생각보다 쉬워요.


탈옥에대해 어느정도 잘 아시는분은 바로 아랫글을 읽어주시구요. 초보자분들은 아래 더보기를 눌러주세요.


준비물

탈옥된 iOS5 기기

아이폰 파일 시스템 탐색기 ( 이 포스트에서는 iFile을 이용할께요)


방법
iBooks앱을 삭제 및 재설치
iBooks를 실행하지 않은채 작업진행

아이폰 파일 탐색하여 `iBooks.app` 을 복사(`var/mobile/Application/임의문자열/iBook.app` 폴더복사)

시스템 어플리케이션(`/var/stash/Application/`)폴더에 붙혀넣기

`/var/stash/Application/iBook.app/Info.plist`의 `CFBundleIdentifier`의 `string`값을 `com.apple.iBooks에서 com.apple.iBooksFix`로 수정

iFile종료 및 리스프링

iBooks어플이 2개인데 아이콘이 라운드처리된 것 삭제

각진 iBooks 실행확인


### 상세설명 ###

1\. iBooks앱을 삭제해주세요.

2\. AppStore에 들어가 iBooks를 설치해주세요.


3\. iBooks를 실행하지 마시구요, iFile을 실행시켜 iBooks어플이 설치된 폴더로 찾아갑니다. iBooks는 /var/mobile/Applications/ 폴더에 임의 문자열로 된 폴더에 있습니다. ( iFile에서는 화면 좌측하단 톱니바퀴누르셔서 Application Names 스위치를 ON으로 활성화 시키면 앱 폴더명이 보입니다. i-funbox에서는 기본적으로 보이는군요)

4\. `/var/mobile/Applications/12309712-21309123(이건 예시입니다)12983/` 폴더안에 iBooks.app 가 있을겁니다. 폴더안에 들어가지 마시구 거기서 우측 상단에 Edit 버튼을 눌러주세요.

5\. iBooks.app 폴더를 터치하여 체크후 우측하단의 클립보드모양 버튼(가장우측에있음)을 누르신후 Copy/Link 버튼을 누르고 Done을 누릅니다.

6\. `/var/stash/Apllications/` 폴더로 이동합니다.(좌측상단에 있는 상위폴더이름의 버튼을 눌러 이동 가능합니다)

7\. 우측 상단의 Edit를 누르시구 우측아래 클립보드 버튼, Paste버튼을 누르고 Done버튼을 누릅니다.

8\. iBooks.app 폴더로 들어갑니다.

9\.꾀 많은 파일중 Info.Plist를 터치합니다. Property List Viewer를 누릅니다.

10\. 항목중 CFBundleIdentity를 누릅니다.(저는 이게 길어서 CFBundleIdenti...로 짤리더군여)

10\. com.apple.iBooks라고 써있는것을 Com.apple.iBooksFix로 수정한후 좌측 상단의 Info.plist버튼을 눌러 빠져나온후 우측 상단의 Done버튼을 누릅니다.

10\. 홈버튼을 눌러 iFile을 종료한후 리스프링을 해줍니다.(SBSetting을 이용했습니다.)

11\. 리스프링이 끝나면 iBooks앱이 2개가 보이는데 태두리를 보시면 둥근것과 사각형으로 된것이 있는데 둥근것을 지워줍니다.

12\. 사각형으로된 iBooks를 실행해봅니다.


### 참고사항 ###

1\. 아이콘이 각진 사각형으로 되어있습니다. 눈에 가시가 된다면 PNG파일을 수정하는 방법이 있습니다.

2\. 아이튠즈와 동기화가 불가능하며, 북스토어에서 결제가 불가능합니다.


### 여담 ###

이걸 왜 재설치하지?라는 마음으로 재설치는 패스하고 해봤는데 안되더군요.

iBooks앱을 지웠는데 책이 그대로 있더군요~

복원할때 시스템 도큐먼트에 문서들이 저장되있었나봅니다.

북스켄이나 인터넷포스트를 pdf로 저장해서 보는 저에게는 이용하는 저는 동기화가 안되고 북스토어결제가 안되는건 불편함이 아니네요. ㅎ