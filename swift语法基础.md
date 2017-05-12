# swift语法基础

##常量和变量

### 定义常量和变量

let：定义常量
var：定义变量

```swift
let maximumNumberOfLoginAttempts = 10
var currentLoginAttempt = 0
```

### 类型标注

```swift
var welcomeMessage: String
```

定义变量welcomeMessage 是String类型的。

可以在一行中定义多个同样类型的变量：

```swift
var red, green, blue: Double
```

### 类型安全和类型推断

Swift是一个类型安全（*type safe*）的语言。会在编译时进行类型检查，并把不匹配的标记为错误。

一般情况不需要自己显式指定类型标注，Swift会根据初始赋值，推断类型。

```swift
let meaningOfLife = 42
// meaningOfLife 会被推测为 Int 类型
```

当推断浮点数的类型时，Swift 总是会选择 `Double` 而不是`Float`。

如果表达式中同时出现了整数和浮点数，会被推断为 `Double` 类型：

```swift
let anotherPi = 3 + 0.14159
// anotherPi 会被推测为 Double 类型
```

#### 类型转换

需要进行显式申明

```swift
let label = "The width is "
let width = 94
let widthLabel = label + String(width)
```

### 输出常量和变量

```swift
print(friendlyWelcome)
// 输出 "Bonjour!"
```

字符串插值，\\(friendlyWelcome) 

```swift
print("The current value of friendlyWelcome is \(friendlyWelcome)")
// 输出 "The current value of friendlyWelcome is Bonjour!

let appleSummary = "I have \(apples) apples."
// 在赋值的时候，同样可以通过字符串插值进行转换
```
## 注释

单行：

```swift
// 这是一个注释
```

多行：

```swift
/* 这是一个,
多行注释 */
```

嵌套：多行注释可以嵌套

```swift
/* 这是第一个多行注释的开头
/* 这是第二个被嵌套的多行注释 */
这是第一个多行注释的结尾 */
```

## 分号

Swift不强制要求在结尾使用分号，在一行内写多条独立语句情况，需要用分号进行分割

```swift
let cat = "🐱"; print(cat)
// 输出 "🐱"
```

## 数组及字典

```swift
var shoppingList = ["catfish", "water", "tulips", "blue paint"]
shoppingList[1] = "bottle of water"
 
var occupations = [
    "Malcolm": "Captain",
    "Kaylee": "Mechanic",
]
occupations["Jayne"] = "Public Relations"
```
使用初始化器语法来创建一个空的数组或者字典。
```swift
let emptyArray = [String]()
let emptyDictionary = [String: Float]()
```
如果类型信息能被推断，那么你就可以用[]来表示空数组，用[:]来表示空字典。举个栗子，当你给变量设置新的值或者传参数给函数的时候。
```swift
shoppingList = []
occupations = [:]
```

## 控制流

if、switch、 for-in 、 for 、while、 repeat-while 

不强制使用圆括号把条件或者循环变量括起来。 

```swift
let individualScores = [75, 43, 103, 87, 12]
var teamScore = 0
for score in individualScores {
    if score > 50 {
        teamScore += 3
    } else {
        teamScore += 1
    }
}
print(teamScore)
```

if 判断条件语句 必须是bool表达式，不在做隐式与0做判断。`if score {...}` 将会报错

switch 语句支持任意类型，不再限制整形

```swift
let vegetable = "red pepper"
switch vegetable {
case "celery":
    print("Add some raisins and make ants on a log.")
case "cucumber", "watercress":
    print("That would make a good tea sandwich.")
case let x where x.hasSuffix("pepper"):
    print("Is it a spicy \(x)?")
default:
    print("Everything tastes good in soup.")
}
```

匹配到case之后，程序会从switch语句中退出，没有必要显式标记`break`

for-in 可以遍历字典，这需要提供一对变量名来储存键值对。字典是无序集合，所以遍历也是无序的

```swift
let interestingNumbers = [
    "Prime": [2, 3, 5, 7, 11, 13],
    "Fibonacci": [1, 1, 2, 3, 5, 8],
    "Square": [1, 4, 9, 16, 25],
    ]
var largest = 0
var largestKind = ""
for (kind, numbers) in interestingNumbers {
    for number in numbers {
        if number > largest {
            largest = number
            largestKind = kind
        }
    }
}
print(largest)
print(largestKind)
```

你可以使用 ..<来创造一个序列区间：

```
var total = 0
for i in 0..<4 {
    total += i
}
print(total)
```

使用 ..<来创建一个不包含最大值的区间，使用 ... 来创造一个包含最大值和最小值的区间。

## 可选值

可选的值包括了一个值或者一个nil来表示值不存在，只有可选变量，可以赋值nil，

```swift
var optionalString: String? = "Hello"
optionalString = nil
print(optionalString == nil)

var optionalName: String? = "John Appleseed"
optionalName = nil
var greeting = "Hello!"
if let name = optionalName {
    greeting = "Hello, \(name)"
}else {
    greeting = "Hello, no name"
}
print(greeting)
```

?? 用于在可选值为nil的时候，使用默认值

```swift
let nickName: String? = nil
let fullName: String = "John Appleseed"
let informalGreeting = "Hi \(nickName ?? fullName)"
```

## 函数和闭包

