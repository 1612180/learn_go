# Slice

length is number of ele in

capicity is number of ele in the array count - from 1st ele in slice

capacity mean how much slice can grow

create with make
```
// len(a)=5, cap(a)=5
a := make([]int, 5)

// len(b)=0, cap(b)=5
b := make([]int, 0, 5)
```

add to slice
```
var s []int
s = append(s, 0)
s = append(s, 1)
```

[Introduction to Slices in Golang](https://www.callicoder.com/golang-slices/)

# Range

Use range in slice
```
s := []int{1, 2, 3, 4, 5}
for i, v := range s {
    fmt.Println(i, v)
}
for i, _ := range s {
    fmt.Println(i)
}
for i := range s {
    fmt.Println(i)
}
```

# Map

map key to value

```
map[KeyType]ValueType
```

```
var m map[string]int
m = make(map[string]int)
m["a"] = 1
m["b"] = 2
```

[Mutating map](https://tour.golang.org/moretypes/22)

# Function can be pass

Function can be pas around like argument
```
func compute(a int, b int, fn func(int, int) int) int {
    return fn(a, b)
}

func sum(a, b int) int {
    return a + b
}

func multi(a, b int) int {
    return a * b
}

func main() {
    fmt.Println(compute(1, 2, sum))
    fmt.Println(compute(5, 6, multi))
}
```

# Anonymous function

```
sum := func(x, y int) int {
    return x + y
}
```

# Misc

Tách câu thành chữ

"this is a sentence" -> ["this", "is", "a", "sentence"]
```
import (
    "strings"
)

sentence := strings.Fields(s)
```

# Method

```
func (r Type) methodName(...) ... {
    ...
}
```

```
type ToaDo struct {
    X, Y int
}

func (t ToaDo) Show() {
    fmt.Println(t.X, t.Y)
}
```

## Pointer

When method need to change value of ```r```
```
func (r *Type) methodName(...) ... {
    ...
}
```

Why use pointer receiver
- change value
- avoid copying each time call method

# Interface

Set of methods signature

A value of interface type can hold any value that -- implement -- methods

```
type r interface{
    method1(...) ...
    method2(...) ...
}
```

```
type Shower interface {
    Show()
}

type ToaDo struct {
    X, Y int
}

func (t ToaDo) Show() {
    fmt.Println(t.X, t.Y)
}

type People struct {
    name string
}

func (p People) Show() {
    fmt.Println(p.name)
}

func main() {
    a := ToaDo{1, 2}
    b := People{"a"}
	
    var s Shower
    s = a
    s.Show()
	
    s = b
    s.Show()
}
```

## Misc

```fmt``` use this to print ```r```
```
func (r Type) String() string{
    ...
}
```

# Test

Thực hiện test theo bài viết 

- [Arrays and slices](https://quii.gitbook.io/learn-go-with-tests/go-fundamentals/arrays-and-slices)

# Đọc tìm hiểu

Goroutine is a lightweight thread

[Goroutine](https://golangbot.com/goroutines/)