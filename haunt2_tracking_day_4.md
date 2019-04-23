# Review Interface

## Empty interface

Empty interface là interface không có method nào
```
interface{}
```

Hàm ```about``` nhận tham số truyền vào là interface bất kì
```
func about(i interface{}) {
    fmt.Printf("Type %T value %v\n", i, i)
}
```

## Type assertion

Lấy giá trị của interface có ```type T```

```
// i là interface
var i interface{} = 5

// nếu i là int thì lấy giá trị của i gán cho v, ok là true
// nếu i không phải int, v lấy giá trị mặc định của int là 0, ok là false
v, ok := i.(int)
```

## Type switch

Lấy ra ```type``` của interface

Tuỳ theo ```type``` của interface mà xử lý

```
var i interface{} = "haha"

switch i.(type) {
case string:
    fmt.Println("string")
case int:
    fmt.Println("int")
default:
    fmt.Println("dun know, what type?")
}
```

## Interface method

Interface, which has methods with **value receivers** accept both **pointer** and **value receivers**. Otherwise only **pointer**


```
type Abouter1 interface {
    About1()
}

type Abouter2 interface {
    About2()
}

type People struct {
    Name string
}


// value receivers
func (p People) About1() {
    fmt.Println(p.Name)
}

type Address struct {
    Name string
}

// pointer receiver
func (a *Address) About2() {
    fmt.Println(a.Name)
}

func main() {
    var a1 Abouter1

    a1 = People{Name: "p1"}
    a1.About1()

    a1 = &People{Name: "p2"}
    a1.About1()

    var a2 Abouter2

    // Address does not implement Abouter2 (About2 method has pointer receiver)
    // a2 = Address{Name: "ad1"}
    // a2.About2()

    a2 = &Address{Name: "ad2"}
    a2.About2()
}
```

## Multi interface

A type can implement multi interface

```
type Talker interface {
    Talk()
}

type Runner interface {
    Run()
}

type People struct {
    Name string
}

// implement interface Talker
func (p People) Talk() {
    fmt.Println(p.Name, "talk")
}

// implement interface Runner
func (p People) Run() {
    fmt.Println(p.Name, "run")
}

func main() {
    p := People{Name: "p"}
    var t Talker = p
    t.Talk()

    var r Runner = p
    r.Run()
}
```

## Embedding interface

Gom nhiều interface thành một interface

```
// combine Talker and Runner interface
type TalkerAndRunner interface {
    Talker
    Runner
}

func main() {
    p := People{Name: "p"}

    var tr TalkerAndRunner = p
    tr.Talk()
    tr.Run()
}
```

# Misc

Muốn sử dụng hàm, biến trong struct, ... của package khác thì tên hàm, biến đó phải viết hoa

```
lower case -> unexported
upper case -> exported
```