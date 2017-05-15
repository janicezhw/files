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

## 整数

Swift 提供了 8，16，32 和 64 位编码的有符号和无符号整数，这些整数类型的命名方式和 C 相似，例如 8 位无符号整数的类型是 UInt8 ，32 位有符号整数的类型是 Int32 。与 Swift 中的其他类型相同，这些整数类型也用开头大写命名法。

### 整数范围

你可以通过 min 和 max 属性来访问每个整数类型的最小值和最大值：

```swift
let minValue = UInt8.min // 最小值是 0, 值的类型是 UInt8
let maxValue = UInt8.max // 最大值是 255, 值得类型是 UInt8
```
这些属性的值都是自适应大小的数字类型（比如说上边例子里的 UInt8 ）并且因此可以在表达式中与在其他相同类型值同用。

### Int

在大多数情况下，你不需要在你的代码中为整数设置一个特定的长度。Swift 提供了一个额外的整数类型： Int ，它拥有与当前平台的原生字相同的长度。

- 在32位平台上， Int 的长度和 Int32 相同。
- 在64位平台上， Int 的长度和 Int64 相同。

除非你需操作特定长度的整数，否则请尽量在代码中使用 Int 作为你的整数的值类型。

## 浮点数

*浮点数*是有小数的数字，比如 3.14159 , 0.1 , 和 -273.15。
浮点类型相比整数类型来说能表示更大范围的值，可以存储比 Int 类型更大或者更小的数字。Swift 提供了两种有符号的浮点数类型。

- Double代表 64 位的浮点数。
- Float 代表 32 位的浮点数。

> 注意
> Double 有至少 15 位数字的精度，而 Float 的精度只有 6 位。具体使用哪种浮点类型取决于你代码需要处理的值范围。在两种类型都可以的情况下，推荐使用 Double 类型。

## 数值型字面量

整数型字面量可以写作：

- 一个十进制数，没有前缀
- 一个二进制数，前缀是 `0b`
- 一个八进制数，前缀是 `0o`
- 一个十六进制数，前缀是 `0x`

下面的这些所有整数字面量的十进制值都是 17：

```swift
let decimalInteger = 17
let binaryInteger = 0b10001 // 17 in binary notation
let octalInteger = 0o21 // 17 in octal notation
let hexadecimalInteger = 0x11 // 17 in hexadecimal notation
```

## 类型别名

*类型别名*可以为已经存在的类型定义了一个新的可选名字。用typealias 关键字定义类型别名。

当你根据上下文的语境想要给类型一个更有意义的名字的时候，类型别名会非常高效，例如处理外部资源中特定长度的数据时：

```swift
typealias AudioSample = UInt16

var maxAmplitudeFound = AudioSample.min
// maxAmplitudeFound is now 0
```

## 布尔值

Swift 有一个基础的布尔量类型，就是 Bool ，布尔量被作为逻辑值来引用，因为他的值只能是真或者假。Swift为布尔量提供了两个常量值，true和false。

```swift
let orangesAreOrange = true
let turnipsAreDelicious = false
```

## 元组

*元组*把多个值合并成单一的复合型的值。元组内的值可以是任何类型，而且可以不必是同一类型。

在下面的示例中， (404, "Not Found") 是一个描述了 *HTTP状态代码* 的元组。HTTP 状态代码是当你请求网页的时候 web 服务器返回的一个特殊值。当你请求不存在的网页时，就会返回  404 Not Found

```swift
let http404Error = (404, "Not Found")
// http404Error is of type (Int, String), and equals (404, "Not Found")
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

