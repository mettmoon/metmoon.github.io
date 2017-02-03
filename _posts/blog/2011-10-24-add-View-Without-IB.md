---
layout: post
title: No! IB - View추가하기
category: programming
tags: [ios]

---

최종 View 위에 Object들이 보이기까지 무엇을 인스턴스해서 넣어야 할까?

아이폰 스크린 구조 : UIWindow -> Frame(Screen) -> UIViewController -> View - > Object(UIButton, UILabel 등등)

### 어떻게 코딩해야 될까? ###

1. UIWindow를 생성하여 스크린에 등장하게 한다
2. UIWindow 안의 Frame을 구성한다.
3. ViewController를 만든다.( ViewController를 생성하고 안에 View 내용을 구성한다)
4. UIWindow안에 ViewController를 넣는다.

### 코드 / 설명 ###

**AppDelegate.m**

```objective_c
#import "AppDelegate.h"
#import "RootViewController.h" //ViewController인 클래스
RootViewController *rootViewController; // 전역변수 선언. 안쓰고 메서드에서 인스턴스해도 무관
@implementation AppDelegate

@synthesize window = _window;

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
    self.window = [[UIWindow alloc] initWithFrame:[[UIScreen mainScreen] bounds]]; //UIWindow를 UIScreen으로 구성
    rootViewController = [[RootViewController alloc] init]; //viewController를 구성
    [self.window addSubview:rootViewController.view]; //viewController의 view를 가지고와 window에 view로 추가
    [self.window makeKeyAndVisible]; // 만들고 보이게함;;
    return YES;
}
```

**RootViewContoller.m**

```objective_c
- (void)viewDidLoad
{
    self.view.backgroundColor = [UIColor redColor];//뷰가 추가되었는지 확인하기 위해 배경색을 빨강으로 지정

    [super viewDidLoad];
}
```

### iOS Simulator 실행화면 ###

[Simulator 실행화면](/images/posts/simulator_01.png)

개발 환경
MacBook Air
XCODE 4.2 iOS SDK 5.0
Unused CoreData
Use Automatic Reference Counting
