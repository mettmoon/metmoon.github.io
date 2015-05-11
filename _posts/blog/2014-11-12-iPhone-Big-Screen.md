---
layout: post
title: iOS 8의 큰 아이폰 화면 지원하기
category: programming
tags: [ios,xcode]

---

아이폰 6와 아이폰 6 플러스가 출시하고 iOS8이 출시 한지 좀 지났는데요. 큰화면을 어떻게 지원하나요~ 라는 질문들을 많이 보게 되는거같아 그 방법에 대해 포스팅 해봅니다.



아이폰5때랑 비슷하죠! 아이폰 5때는 568h 파일을 추가하면 됐었는데요~



이번엔 2가지 방법이 있습니다.



Launch Screen File을 추가하는 방법과 App Icons Source에 지원하는 이미지를 추가하여 인식하는 방법입니다.



일단 첫번째 Launch Screen File을 추가하는 방법입니다.



Xcode6이상에서 "New File"에서 "User Interface"탭에 "Launch Screen"을 추가합니다. 그리고 프로젝트 - Targets(해당앱) - General탭에 중간에 Launch Screen File에서 추가한 Launch Screen 파일을 선택해줍니다. 그럼 끝!



아래는 과정을 이미지로 첨부합니다.
![step1](/images/posts/xcode_step_01.png)
![step2](/images/posts/xcode_step_02.png)
![step3](/images/posts/xcode_step_03.png)
![step4](/images/posts/xcode_step_04.png)

두번째 방법 이미지 추가하는 방법은 어쌧을 사용할 경우 간단합니다.

아래 이미지처럼 해당 옵션을 체크해주고 각 스크린에 맞는 이미지를 넣어주시면 됩니다.
![step5](/images/posts/xcode_step_05.png)

새로운 아이폰들의 Launch Image 의 사이즈는 다음과 같습니다.

For iPhone 6:

750 x 1334 (@2x) for portrait
1334 x 750 (@2x) for landscape
For iPhone 6 Plus:

1242 x 2208 (@3x) for portrait
2208 x 1242 (@3x) for landscape




참고자료

[iOS Human Interface Guidelines: Launch Image](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/MobileHIG/LaunchImages.html)

[App Distribution Guide](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringYourApp/ConfiguringYourApp.html#//apple_ref/doc/uid/TP40012582-CH28-SW4)
