---
layout: post
title: String 사이사이에 문자열 추가하기
category: programming
tags: [objc,swift]

---

Objective-c 혹은 Swift에서 문자열 사이에 특정문자를 넣는 방법입니다.

extension이나 category로 구현했습니다.

### Swift
```Swift

extension String{
    func stringDashAdded() -> String{
        var strComponents = Array<String>()
        var i:Int = 0
        let splitCount:Int! = 4
        do {
            let length:Int! = min(splitCount, count(self) - i)
            let component = self.substringWithRange(Range<String.Index>(start: advance(self.startIndex, i), end: advance(self.startIndex, i + length)))
            strComponents.append(component)
            i += length
        }while(i < count(self))
        var resultString = ""
        for str in strComponents {
            if strComponents.first != str {
                resultString += "-"
            }
            resultString += str
        }
        return resultString
    }
}

```


### Objective-C
```Objective-C

@implementation NSString (AddDash)

- (NSString *)stringDashAdded{
    NSMutableArray *strComponentArray = [NSMutableArray new];
    NSInteger i = 0;
    NSInteger splitCount = 4;
    do {
        NSInteger length = MIN(splitCount, self.length - i);
        [strComponentArray addObject:[self substringWithRange:NSMakeRange(i, length)]];
        i += splitCount;
    } while (i < self.length);
    NSString *resultString = @"";
    for(NSString *str in strComponentArray){
        if(strComponentArray.firstObject != str){
            resultString = [resultString stringByAppendingString:@"-"];
        }
        resultString = [resultString stringByAppendingString:str];
    }
    return resultString;
}

@end

```