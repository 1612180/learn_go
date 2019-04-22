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
UnlockUnlock
```