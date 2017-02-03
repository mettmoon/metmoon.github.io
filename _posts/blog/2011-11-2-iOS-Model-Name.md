---
layout: post
title: 현재 실행되고 있는 기기 이름 알아내기
category: programming
tags: [ios]

---
자기가 개발한 앱이 아이폰에서 실행될지 아이팟,아이패드가 될지 알아봅시다

소스

```objective_c
    NSString *modelName = [[UIDevice currentDevice] model];
    NSLog(@"modelName is %@",modelName);
```

콘솔창

```objective_c
2011-11-02 16:03:49.186 ClassPractice[9947:707] modelName is iPhone
```

modelName에 담기게 될 택스트는 'iPhone', 'iPod Touch', 'iPad', iPhone Simulator' 가 됩니다.
