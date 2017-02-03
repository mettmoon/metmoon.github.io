---
layout: post
title: 트위터 공유기능 붙히기(iOS 5 이상)
category: programming
tags: [iOS]

---
트위터 공유기능을 넣으려고 보니까 아주 쉬워서 포스팅합니다.



프로젝트에 *Twitter.framework* 를 추가합니다.

구현을 원하는 클래스에서

```objective_c
#import <Twitter/Twitter.h>
```

해주시고

코드는 

```objective_c
    TWTweetComposeViewController *viewController = [[TWTweetComposeViewController alloc] init];
    [viewController addImage:UIImage객체];
    [self presentModalViewController:viewController animated:YES];
    [viewController release];
```

로 끝! 그결과 나오는 창.
![twitter share image](/images/posts/twitter_share_01.png)

위에서는 사진을 공유하는 기능이었습니다.
텍스트 추가, 이미지추가, URL추가하는 기능은 다음과 같으며
*TWTweetComposeViewController.h* 를 참고하면됩니다.

```objective_c
- (BOOL)setInitialText:(NSString *)text;
- (BOOL)addImage:(UIImage *)image;
- (BOOL)addURL:(NSURL *)url;
```
