---
layout: post
title: Decoder로 JSON을 디코딩시 알수 없는 enum 처리
category: programming
tags: [Swift, iOS, Swift 5]

---

설계된 스트링값을 우리는 enum으로 관리한다. 그것을 활용하여 다음과 같이 Decodable한 JSON을 설계하였을 때
```swift
enum PaymentType: String, Decodable {
	case cash
	case card
	case paypal
}

struct Invoice: Decodable {
	var date: Date
	var itemName: String
	var price:Int
	var paymentType: PaymentType
}
```

만일 추후 PaymentType이 추가된다면 DecodingError가 날 것이다.

추가가 예상된다면 DecodingError를 마주하는것보다 paymentType에 대해서만 예외를 처리하고 싶을땐 Decodable을 실 구현하여 모르는 타입에 대한 예외처리를 하여 디코딩을 완수하면 된다.(하지만 이것은 예외(Exception)긴 예외이다.)


## 방법1. 옵셔널로 처리
```swift
enum PaymentType: String, Decodable {
	case cash
	case card
	case paypal
}

struct Invoice: Decodable {
	var date: Date
	var price:Int
	var paymentType: PaymentType?

	enum CodingKeys: String, CodingKey {
		case date
		case price
		case paymentType
	}

	init(from decoder: Decoder) throws {
		let container = try decoder.container(keyedBy: CodingKeys.self)
		self.date = try container.decode(Date.self, forKey: .date)
		self.price = try container.decode(Int.self, forKey: .price)
		self.paymentType = try? container.decode(PaymentType.self, forKey: .paymentType) // try?를 사용
	}
}
```

## 방법2. 모르는 타입을 추가(널처리 안해도 되서 선호함.)

```swift
enum PaymentType: String, Decodable {
	case cash
	case card
	case paypal
	case unkown // 모르는 타입 추가
}

struct Invoice: Decodable {
	var date: Date
	var price:Int
	var paymentType: PaymentType?

	enum CodingKeys: String, CodingKey {
		case date
		case price
		case paymentType
	}

	init(from decoder: Decoder) throws {
		let container = try decoder.container(keyedBy: CodingKeys.self)
		self.date = try container.decode(Date.self, forKey: .date)
		self.price = try container.decode(Int.self, forKey: .price)
        do {
            self.paymentType = try container.decode(PaymentType.self, forKey: .paymentType)
        }catch  {
            self.paymentType = .unkown // 모르는 타입일 경우 unkown으로 할당
        }
	}
}
```

## 방법3. 서버 개발자에게 API 버전을 올려달라고하자




