before
```swift
let comment: String

if Int.random(in: 0...3).isMultiple(of: 2) {
    comment = "It`s an even integer"
} else {
    comment = "It`s an ood integer"
}

let spelledOut: String

switch Int.random(in: 0...3) {
case 0:
    spelledOut = "Zero"
case 1:
    spelledOut = "One"
case 2:
    spelledOut = "Two"
case 3:
    spelledOut = "Three"
default:
    spelledOut = "Out of range"
}

```

after
```swift
let comment = {
  if Int.random(in 0...3).isMultiple(of: 2) {
      return "It`s an even integer"
  } else {
      return "It`s an odd integer"
  }
}()

let spelledOut = {
    switch Int.random(in: 0...3) {
    case 0:
        return "Zero"
    case 1:
        return  "One"
    case 2:
        return "Two"
    case 3:
        return "Three"
    default:
        return "Out of range"
}
}()
```

after swift 5.9 
```swift
let comment = if int.random(in 0...3).isMultiple(of: 2) {
    "It`s an even integer"
} else {
    "It`s an odd integer"
}

let spelledOut = switch Int.random(in: 0...3) {
    case 0:
        "Zero"
    case 1:
         "One"
    case 2:
        "Two"
    case 3:
         "Three"
    default:
         "Out of range"
```
