---
layout: post
title: WAV파일 CAF로 변환하기
category: programming
tags: [XCode]

---

노티피케이션를 커스텀 할경우 음원파일을 caf파일로 넣어줘야한다. 근데 보통 건내받은 파일은 mp3 혹은 wav 파일 보통 wav 파일 일것이다. wav 파일을 caf로 교체하는 방법이다. (mp3는 안알아봄)

```
/usr/bin/afconvert -f caff -d LEI16 {INPUT}.wav {OUTPUT}.caf
```

afconvert를 이용하면 된다. 애플 iOS개발 문서에 기제되어있는 내용이다.

참고: [애플 개발문서](https://developer.apple.com/library/ios/documentation/AudioVideo/Conceptual/MultimediaPG/UsingAudio/UsingAudio.html#//apple_ref/doc/uid/TP40009767-CH2-SW28)

