전역 변수를 선언하는 것은 일반적으로 나쁜 습관으로 간주함.
```swift
import Foundation

let baseUrl = URL(string: "https://grape.com"
let apiPath = "/api/v2/"
let apiKey = "soiajsdfoija"
```

그렇다면 해결책? 1. 구조체를 선언해서 전역변수에서 상수를 제거
```swift
import Foundation

struct Constant {
  private init() {}

  static let baseUrl = URL(string: "https://grape.com")
  static let apiPath = "/api/v2/"
  static let apiKey = "soiajsdfoijae"
}
let constant = Constant() // 인스턴스 생성 불필요 따라서 private init() {} 으로 외부에서 인스턴스 생성 못하게 막음.
```

해결책 2. 열거형을 사용

열거형은 Swift표준 라이브러리에서 실제로 활용함
```swift
import Foundation

enum Constant {
  static let baseUrl = URL(string: "https://grape.com")
  static let apiPath = "/api/v2/"
  static let apiKey = "soiajsdfoijae"
}
```


```swift
/// Unicode.Scalar

public enum Unicode {} 

```

구조체로 선언해서 멤버들을 관리하느냐 / enum으로 관리하느냐 선호도 차이일듯. 각 접근방식에 따른 메모리 성능 차이는 추후 학습해야할듯.
