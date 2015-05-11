---
layout: post
title: iOS Custom Indicator
cateogry: programming
tags: [ios]

---

커스텀 인디케이터 만드는 방법입니다.

방법은 UIImageView 의 Animation관련 Property를 이용하면 되겠습니다. 간단합니다.

**UIImageView의 헤더**

```
@property(nonatomic,copy) NSArray *animationImages;            // The array must contain UIImages. Setting hides the single image. default is nil
@property(nonatomic,copy) NSArray *highlightedAnimationImages NS_AVAILABLE_IOS(3_0);            // The array must contain UIImages. Setting hides the single image. default is nil

@property(nonatomic) NSTimeInterval animationDuration;         // for one cycle of images. default is number of images * 1/30th of a second (i.e. 30 fps)
@property(nonatomic) NSInteger      animationRepeatCount;      // 0 means infinite (default is 0)

- (void)startAnimating;
- (void)stopAnimating;
- (BOOL)isAnimating;
```

**예제**

```
    UIImageView* animatedImageView = [[UIImageView alloc] initWithFrame:self.view.frame];
    
    animatedImageView.animationImages = [NSArray arrayWithObjects:
                                         [UIImage imageNamed:@"spinner-01.png"],
                                         [UIImage imageNamed:@"spinner-02.png"],
                                         [UIImage imageNamed:@"spinner-03.png"],
                                         [UIImage imageNamed:@"spinner-04.png"],
                                         nil];
    
    animatedImageView.animationDuration = 1.0;
    animatedImageView.animationRepeatCount = 0;
    
    [animatedImageView startAnimating];

//    멈출때
//    [animatedImageView stopAnimating];
```

그럼 즐거운 코딩되세요 ^ ^
