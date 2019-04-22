# Goroutine

Goroutine là cách thực hiện nhiều task cùng một lúc

Sau khi gọi goroutine, chương trình chính tiếp tục chạy dòng tiếp theo

# Channel

```
// send v to channel ch
ch <- v

// receive v from chanel ch
v := <- ch
```

```send``` và ```receive``` block chương trình cho đến khi sẵn sàng -> cho phép đồng bộ goroutine

# Select

```
select{
    case ...:
        ...
    case ...:
        ...
    default:
        ....
}
```

```select``` block chương trình cho đến đến khi một ```case``` bất kì có thể chạy được, rồi thực hiện ```case``` đó. Nếu có nhiều case có thể chạy thì sẽ chọn ngẫu nhiên. Nếu không có ```case``` nào chạy được thì sẽ chạy ```default```

# Mutex

Channel đẻ các goroutine giao tiếp với nhau. Nếu goroutine không cần giao tiếp -> mutex

Có 2 phương thức
```
Lock
Unlock
```

# Json

Sử dụng thư viện
```
import "encoding/json"
```

## Encode

```struct``` muốn tên field được encode json phải -- viết hoa -- ở đầu

[JSON and dealing with unexported fields](https://stackoverflow.com/questions/11126793/json-and-dealing-with-unexported-fields)

```
// 
type People struct {
    Name    string
    age     int
    Address string
}

func main() {
    a := People{Name: "a", age: 1, Address: "HCM"}

    d, _ := json.Marshal(a)
    fmt.Println(string(d))
    // có Name, Adress. thiếu age 
    // {"Name":"a","Address":"HCM"}
}
```

```map``` muốn encode phải có ```key``` là ```string```
```
map[string]T
```

## Decode

```data``` được decode là ```[]byte```

```
var b People
data := []byte(`{"Name": "Bob", "Address": "HCM"}`)

err := json.Unmarshal(data, &b)
if err != nil {
    fmt.Println(err)
}
```

# Input

```
fmt.Scan()
fmt.Scanln()
fmt.Scanf()
```

# File

## Read

Read with ```io``` library
```
import "io/ioutil"

func main(){
    content, err := ioutil.ReadFile("abc.txt")
    if err != nil {
        fmt.Println(err)
    }
    fmt.Printf("content File\n%s", content)
}
```

Read with ```os``` library
```
import (
    "fmt"
    "os"
)

func main() {
    f, err := os.Open("abc.txt")
    if err != nil {
        return
    }
    defer f.Close()

    var line string
    for {
        // scan cách nhau bằng whitespace
        n, err := fmt.Fscan(f, &line)
        if err != nil {
            fmt.Println(err)
            break
        }
        fmt.Println("Read", n)
        fmt.Println(line)
    }
}
```

## Write

Write with ```io``` library
```
data := []byte("Hello\nboii\nThis is it")
err := ioutil.WriteFile("abc.txt", data, 0644)
if err != nil {
    fmt.Println(err)
}
```

Thử viết ứng dụng copy bằng go

[Copy in go](https://github.com/1612180/copy)