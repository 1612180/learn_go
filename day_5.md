# First class function

**First class function** nghĩa là function có thể được gán vào biến,
truyền vào function khác như argument, ...

## Revise anonymous function

Chạy ```anonymous function``` không cần gán biến
```
func main() {
    func(msg string) {
        fmt.Println(msg)
    }("Hi :)")
}
```

## Define function type

function type can be defined like struct

```func_int``` là kiểu function được định nghĩa
```
type func_int func(a, b int) int

func main() {
    var sum func_int = func(a, b int) int {
        return a + b
    }
    var multi func_int = func(a, b int) int {
        return a * b
    }
}
```

## Passing to another function as argument

Hàm ```use``` nhận vào ```f``` có kiểu ```func_int```
```
func use(f func_int, a int, b int) int {
    return f(a, b)
}
func main() {
    fmt.Println(use(sum, 2, 3), use(multi, 4, 5))
}
```

## Returning function

Hàm ```play``` trả về là một hàm, chứ không sử dụng hàm ```play``` trực tiếp
```
func play() func(a, b int) int {
    f := func(a, b int) int {
        return a + b
    }
    return f
}

func main() {
    s := play()
    fmt.Println(s(1, 2))
}
```

## Revise Closure

Closure là hàm anonymous function ở trong một hàm và **truy cập được biến định nghĩa ngoài** hàm anonymous function, nhưng bị giới hạn bởi hàm bên ngoài
```
func addHello() func(s string) string {
    hello := "Hello "
    f := func(s string) string {
        return hello + s
    }
    return f
}

func main() {
    a := addHello()
    fmt.Println(a("hau"))
}
```

# Read about Dependency Injection

Dependency Injection là đưa dependency cho object hoặc framework khác lo.

Module nhỏ xử lý logic. Module lớn gọi module nhỏ bằng interface

Old code -- Hàm ```doSomething``` tạo ```p``` kiểu ```MyObject```.
Nếu ```p``` xử lý những công việc phức tạp như truy cập mạng thì khó để unit test
```
type MyObject struct {
}

func (m MyObject) about() {
    fmt.Println("Hello")
}

func doSomething() {
    p := MyObject{}
    p.about()
}

func main() {
    doSomething()
}
```

New code -- Sử dụng interface, ```MyObject``` implement method ```about()``` của ```MyInterface```
```
type MyInterface interface {
    about()
}

func doSomething(m MyInterface) {
    m.about()
}
```

**Why ?** It isolates classes during testing.

[Stackoverflow](https://stackoverflow.com/questions/130794/what-is-dependency-injection)

[Dependency Injection Demystified](https://www.jamesshore.com/Blog/Dependency-Injection-Demystified.html)