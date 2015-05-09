---
layout: post
title: 객체가 스스로 초기화 되었다??
cateogry: programming
tag: [ios]
---
`(void)viewDidLoad` 에서 해당 객체를 초기화 하고 사용했는데 다음에 다시 참조하려 하니 해당 객체가 `nil` 값이 들어있었다. 

자세한 코드는 다음과 같다.


```
@interface FavoriteSimpleNumViewCtrl : UIViewController
{
    NSMutableArray *testArray;
@end

@implementation FadvoriteSimpleNumViewCtrl
- (void)viewDidLoad {
    [super viewDidLoad];
    testArray = [NSMutableArray array];
    for(int i = 1 ; i <= 10 ; i++){
        UIButton *button = [[UIButton alloc] initWithFrame:CGRectMake(0, 0, 100, 100)];
        [testArray addObject:button];
    }
[self checkArray];
}

- (void)checkArray{
    NSLog(@"%@",testArray);
}

@end
```

자여기서 `viewDidLoad` 가 `checkArray`를 호출할때는 안이 10objects로 꽉찼지만 view로드가 완료된후 버튼이나 다른 이벤트로  `checkArray`를 호출할경우 nil객체로 되있었다.

답은 간단하였다. 객체인 `testArray`를 `alloc` 을 해주지 않았기 때문이다. `alloc` 을 안할경우 `autorelease`가 되는데 이는 함수호출이 끝났을경우 자동으로 `release`를 해준다. 


`testArray = [NSMutableArray array];`
이 줄을
`testArray = [[NSMutableArray alloc] initWithObjects:nil];`
로 바꿔주면 되겠다.





