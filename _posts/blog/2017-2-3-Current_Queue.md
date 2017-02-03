---
layout: post
title: GCD에서 호출 보낸 쓰레드로 다시 보내기 - Current Queue
category: programming
tags: [Swift, iOS]

---

GCD를 이용하다가 UI처리를 위해 메인스레드로 어싱크해서 호출해야할때가 있다. 항상 `DispatchQueue.main.asnyc` 로 날리곤했는데 간혹 백그라운드 작업중에 해당 함수를 호출하여 사용하면 해당함수가 앞과 같이 main으로 async한다. 가벼운 작업이면 무시할만하나 무거운작업중이었다면 UI가 버벅될수도있다.(~~요즘은 폰이 워낙 빠르긴하지만^^;~~)

이럴땐 호출한 스레드로 다시 되돌리면 되지않는가?

옵젝씨 시절에 `dispatch_queue_current_label`따위로 했던것같은데 이게 Swift로 넝머와서부터인가 사라진듯한 느낌이다. 구글링하다 발줴했다.
다음과 같이 쓰면 된다. currentLabel은 쓸일이 거의 없고. `DispatchQueue.current`를 인스턴스 해놨다가 리턴할때 해당 큐로 어싱크해서 보내면 된다.

```swift
extension DispatchQueue {
    class var currentLabel: String {
        return String(validatingUTF8: __dispatch_queue_get_label(nil))!
    }
    class var current:DispatchQueue {
        return DispatchQueue(label: self.currentLabel)
    }
}

```

예시
```swift
func call(_ completion:(() -> Void)){
	var postingQueue = DispatchQueue.current
	somthingMultiThreadingWorks {
		//다른 쓰레드
		postingQueue.async {
			completion()//받은 스레드로 어싱크
		}
	}
}
```


참고: [GCD : Getting current dispatch queue name with	swift 3](https://lists.swift.org/pipermail/swift-users/Week-of-Mon-20160613/002280.html)

