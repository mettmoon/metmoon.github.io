---
layout: post
title: foo.bar = baz 와 [foo setBar:baz] 의 차이점
category: programming
tags: [XCode]

---

오브젝티브씨에 관한 얘기다.

맥부기에서 질문이 올라와 댓글을 작성했는데 개념적으로 재밌기에 블로그로 복사해왔다.

아래는 댓글 내용이다.


질문 :

``` .xxx = yyy 와 setXxx:yyy 의 차이점이 뭔가요??```


답변 :
``` setXxx:yyy를 쉽게 사용하도록 만든게 .xxx = yyy 입니다. 

외부에서 클래스 내부 맴버에 접근이 불가능합니다. 

함수를 사용하여서 접근하도록 되어있습니다. 

프로퍼티를 선언할경우 속성에 따라 세터와 게터 함수가 자동으로 생성됩니다.(setXxx, getXxx) 

.xxx = yyy는 세터를 쉽게 사용하라고 만든거죠. 

만약 프로퍼티를 readyonly 로 설정할경우 세터는 생성이 안되어 .xxx == yyy는 사용이 불가능하게 됩니다. 
```

구조체는 클래스와 다르게 직접 접근하는 방식이다. 같은 구문을 사용하지만 동작은 둘이 다르게 하는거다. 

참고: [Dot-notation Syntax - Big Nerd Ranch](https://www.bignerdranch.com/blog/dot-notation-syntax/)

