# Review Channel

- unbuffered channel: the sender blocks until the receiver has received the value. 

- buffered chanel: the sender blocks only until the value has been copied to the buffer; if the buffer is full, this means waiting until some receiver has retrieved a value.

Deadlock code - unbuffered channel
```
func main() {
    ch := make(chan int)

    // sender is blocked because there is no goroutine to receive
    // => deadlock
    ch <- 1
    
    fmt.Println("Hello")
}
```

Not deadlock code - buffered channel
```
func main() {
    ch := make(chan int, 1)

    // channel has room for sender
    ch <- 1
    
    fmt.Println("Hello")
}
```

Deadlock code - buffered channel
```
func main() {
    ch := make(chan int, 1)

    // sender is not blocked because channel has room
    ch <- 1

    // sender is blocked beacause channel is full and no goroutine to receive
    ch <- 2
    
    fmt.Println("Hello")
}
```

A buffered channel can be used like a **semaphore**, for instance to **limit** throughput.

# Git

Luyện tập trên [Learn git branching](https://learngitbranching.js.org/)