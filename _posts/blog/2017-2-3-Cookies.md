---
layout: post
title: 쿠키 저장 및 불러오기
category: programming
tags: [Swift, iOS]

---

URLSession 이라던지 UIWebView라던지 앱실행시 얻은 쿠키(세션)는 앱사용시 유지되는데 앱종료시 날라간다.

쿠키를 저장하여 재활용하는 방법은 헤더에 얹혀서 보내는것도 있지만 쿠키로 관리되진않으니 HTTPCookieStorage를 건드려서 관리해야한다. 

```swift
extension HTTPCookieStorage {
    static func clear(){
        if let cookies = HTTPCookieStorage.shared.cookies {
            for cookie in cookies {
                HTTPCookieStorage.shared.deleteCookie(cookie)
            }
        }
    }
    static func save(){
        var cookies = [Any]()
        if let newCookies = HTTPCookieStorage.shared.cookies {
            for newCookie in newCookies {
                var cookie = [HTTPCookiePropertyKey : Any]()
                cookie[.name] = newCookie.name
                cookie[.value] = newCookie.value
                cookie[.domain] = newCookie.domain
                cookie[.path] = newCookie.path
                cookie[.version] = newCookie.version
                if let date = newCookie.expiresDate {
                    cookie[.expires] = date
                }
                cookies.append(cookie)
            }
            UserDefaults.standard.setValue(cookies, forKey: "cookies")
            UserDefaults.standard.synchronize()
        }

    }
    static func restore(){
        if let cookies = UserDefaults.standard.value(forKey: "cookies") as? [[HTTPCookiePropertyKey : Any]] {
            for cookie in cookies {
                if let oldCookie = HTTPCookie(properties: cookie) {
                    print("cookie loaded:\(oldCookie)")
                    HTTPCookieStorage.shared.setCookie(oldCookie)
                }
            }
        }

    }
}

```

위와 같은 extension을 작성하여 다음과 같이 사용할 수 있다.

```swift
HTTPCookieStorage.restore()//앱실행시 호출하여 기존 쿠키를 불러온다.
HTTPCookieStorage.save() //쿠키를 얻고 난후 호출하여 쿠키를 저장한다.
HTTPCookieStorage.clear() //로그아웃이나 세션 만료시 저장된 쿠키를 삭제한다.(사이트주소가 바뀐다거나 하면서 쿠키가 누적될수 있다.)
```
