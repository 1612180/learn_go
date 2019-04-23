# Output

[fmt](https://golang.org/pkg/fmt/)

Print và Println không cần formatted strings 
```
fmt.Println("This is a test", 1, 2, "another")
fmt.Print(1, 2, 3, "This is a test")
```

Printf sử dụng formatted stirngs như %s, %d, ...
```
fmt.Printf("%d")
```

# Data types

[Types](https://www.golang-book.com/books/intro/3)

[Golang Basic Types, Operators and Type Conversion](https://www.callicoder.com/golang-basic-types-operators-type-conversion/)

## Integer
```
var a  = 6
var myUint uint = 500
var myHexNumber = 0xFF
```

## Float
```
var a = 123.45
```

## String

Double-quoted strings cannot contain newlines and they can have escape characters

Strings enclosed within back ticks are raw strings. They can span multiple lines. Moreover, Escape characters don’t have any special meaning in raw strings.
```
var a = "This is a \nstring"
var b = `This is a raw
string`
```

## Boolean
```
var isGood = false
var isBad = true
```

```
&&
||
!
```

# Function
[The anatomy of Functions in Go](https://medium.com/rungo/the-anatomy-of-functions-in-go-de56c050fe11)
```
func add(x int, y int) int {
    return x + y
}
```

```=``` is assignment operator

```:=``` is short variable declarations

## Multiple return values
```
func same(x, y int) (int, int){
    return x, y
}
```

## Named return values
```
func breakNum(num int) (a, b int) {
    a = num - 1
    b = num - 2
    return
}
```

# Iteration
```
sum := 0
for i := 0; i < 100; i++ {
    sum += i
}
```

for is while
```
s := 1
for s < 100 {
    s += s
}
```

# If, else
```
a := 1
if a == 0 {
    fmt.Println("if")
} else if a > 0 {
    fmt.Println("else if")
} else {
    fmt.Println("else")
}
```

# Pointer
Giống như C

```
// p trỏ tới a
a := 5
var p *int
p = &a
fmt.Println(*p)

// thay đổi a
*p = 4
fmt.Println(a)

// p trỏ tới b
b := 6
p = &b
fmt.Println(*p)
```

# Struct

```
type ToaDo struct {
    X int
    Y int
}
```

# Array
The type ```[n]T``` is an array of ```n``` values of type ```T```

Array is fixed-sized

```
var a [2]int
var s = [2]string{"Hello", "boii"}
```

# Slice
[Go Slices: usage and internals](https://blog.golang.org/go-slices-usage-and-internals)

The type ```[]T``` is a slice with elements of type ```T```


Slice is dynamically-sized

Slice tham chiếu đến (một phần hay toàn bộ) array

```
var arr = [6]int{1, 2, 3, 4, 5, 6}
var s []int = arr[1:6]
```

[1:6] là 1, 2, ..., 5