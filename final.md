final 키워드
클래스나 메서드에 이 키워드를 사용하면 하위 클래스화 또는 재정의가 불가능해짐.

```swift
class ViewController: UiViewContorller {
  override func viewDidLoad() {
      super.viewDidLoad()
      // ...
  }  

  func firstMethod() {
      // ...
  }

  func secondMethod() {
      // ...
  }
}
```


```swift
class ChildViewController: ViewController {
  override func secondMethod() {
      // ...
  }
}
```

상속을 받아서 메서드를 재정의할 때, 결과적으로 이러한 상속받은 메서드중 하나가 실행될 때 마다
Swift는 올바른 구현을 식별하기 위해 런타임에 호출을 동적으로 전달함. (동적 디스패치)
이 동적디스패치에는 성능저하가 있음.


```swift
final class ViewController: UiViewContorller {
  override func viewDidLoad() {
      super.viewDidLoad()
      // ...
  }  

  func firstMethod() {
      // ...
  }

  func secondMethod() {
      // ...
  }
}
```

그렇다면 final로 선언한다면?
런타임 도중에 함수호출을 결정하지 않고, compile-time에서 함수호출을 결정할 수 있게됨. 즉 정적 디스패치로 대체됨
이것은 성능향상으로 이어짐.
물론 이러한 최적화는 약간의 성능향상으로 이어지지만.
프로젝트 규모가 커지면 커질수록 비례해서 성능향상으로 이어진다!

결론
final 키워드는 override을 제한할 뿐만 아니라, Dynamic DisPatch을 줄여, 런타임 성능 향상을 가능하게 한다.
또한 접근제어자인 private/fileprivate을 통해서도 Dynamic Dispatch을 줄일 수 있다.

속도가 중요하지 않은 앱에서 런타임 성능 향상은 중요 요인이 아니지만,
속도가 중요한 앱에서 이러한 최적화는 훌륭한 UX를 만드는데 기여한다는 점은 분명함.

그래서 상속이 필요하지 않은 클래스엔 final을 작성하며, 외부에 접근이 필요 없는 클래스나 메서드 프로퍼티 또한 Private/fileprivate을 작성하는 습관 가지기!!

참고
https://developer.apple.com/swift/blog/?id=27
