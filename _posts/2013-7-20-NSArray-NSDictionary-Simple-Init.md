---
layout: post
title: NSArray와 NSDictionary 초기화를 간다하게 하기
cateogry: programming
tags: [ios]
---

*NSArray*와 *NSDictionary*의 초기화를 간단히 하는 방법에 관한내용입니다.

*NSArray* 와 *NSDictionary*를 초기화 할때 대표적으로 *initWithObjects*와 *initWithObjectsAndKeys*으로  다음과 같은 방법을 사용하는데요


```
    NSArray *array = [[NSArray alloc] initWithObjects:@"object1",@"object2",@"object3", nil];
    NSDictionary *dictionary = [[NSDictionary alloc] initWithObjectsAndKeys:
                                @"object1",@"key1"
                                @"object2",@"key2"
                                @"object3",@"key3"
                                ,nil];

```

코드가 길고 alloc, init의 반복으로 지루한 코딩이 될수있습니다. 



다음과 같이 하면 편하게 할수있습니다.

```
    NSArray *array = @[@"object1",@"object2", @"object3"];
    NSDictionary *dictionary = @{@"key1": @"object1"
                                 , @"key2":@"object2"
                                 , @"key3":@"object3"};

```

추가적으로 와 에 있는 객체를 불러들일때 대표적으로 objectAtIndex와 objectForKey를 다음과 같이 사용하는데요 

```
    id object = [array objectAtIndex:0];
    id object = [dictionary objectForKey:@"key1"];
```

이또한 다음과 같이 간단하게 사용할수 있습니다.

```
    id object = array[0];
    id object = dictionary[@"key"];
```

그럼 즐거운 코딩 되세요^^
