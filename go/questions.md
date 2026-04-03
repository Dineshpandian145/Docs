
# 1.What is golang?
    ➤ Golang (Go) is an open-source, statically typed, compiled programming language developed by Google.
    ➤ It is designed for building fast, scalable, and concurrent applications, especially backend systems and distributed services.

    Advantages of Golang:-

        - High Performance & Fast Compilation
        - Built-in Concurrency & Garbage Collection
        - Simple Syntax & Strong Standard Library
        - Cross-Platform Support (linux,windows,mac)
        - Static Typing & Efficient Memory Usage
        - Great for Microservices & distributed system

# 2. What are data types in Golang?
    ➤ Data types in Go define the type of data a variable can hold. Go is a statically typed language, so every variable must have a defined type at compile time. Data types help the compiler understand how to store and operate on data efficiently.

    🔸 Integer Types - Used to store whole numbers
        int, int8, int16, int32, int64
        uint, uint8, uint16, uint32, uint64

    🔸 Floating Point Types - Used to store decimal values
        float32, float64
    
    🔸 Boolean Type - Used to store true/false values
        
    🔸 String Type - Used to store text

    🔸 Advanaced types
        Array
        Slice
        Map
        Struct
        Pointer
        Function
# 3. What is the difference between var, const, and short declaration (:=) in Go?
    ➤ var is used to declare variables, const is used for immutable values, and := is a shorthand for declaring variables inside functions with type inference.

        🔹 1. var Keyword

            - Can be used inside and outside functions
            - Type can be explicit or inferred
        🔹 2. const Keyword

            - Value cannot be changed
            - Must be assigned at declaration
        🔹 3. Short Declaration (:=)

            - Only allowed inside functions
            - Type is automatically inferred

# 4. What is the difference between Array and Slice in Go?
    
    ➤ Both array and slice are used to store multiple elements of the same data type. However, an array has a fixed size, so we cannot append data once it is full. Also, an array is a value type.

    ➤ A slice does not have a fixed size, so we can append data. It automatically increases its size and capacity when needed. A slice is a reference type, so changes made inside a function will affect the original slice even if it is not returned.

    ➤ We can declare a slice using the make function by specifying its length and capacity.

# 5. What is a Pointer in Go?
    ➤ A pointer variable that holds the memory address of another variable. It allows direct access to the memory location, which helps in modifying values without copying the data.

        - Use & to get the address
        - Use * to access (dereference) the value

        ```go 
            var a int = 10

            var p *int = &a  // pointer stores address of a

            fmt.Println(*p)  // dereference → prints 10

            *p = 20          // modify value using pointer
            fmt.Println(a)   // now a = 20
        ```
# 6. What is a Struct in Go?

    ➤ struct is a user-defined data type that allows grouping multiple fields of different types into a single unit. It is commonly used to represent real-world entities and organize related data together.
    

# 2. What is a Goroutine?
    ➤ A goroutine is a lightweight thread managed by the Go runtime. It is used to execute functions concurrently with other goroutines.
    ➤ Goroutines are more efficient than OS threads because they require very less memory (around 2 KB stack) and are managed by the Go scheduler instead of the operating system.
 
 
# 3. How go routines work internally ?

    ➤ Goroutines are created by the Go program and managed by the Go runtime scheduler. They are placed in run queues, and processors (P) pick them and assign them to OS threads (M), which execute them on CPU cores. The scheduler switches between goroutines during blocking operations or preemption, enabling efficient concurrency.

        ┌──────────────────────────────┐
        │        Your Go Program       │
        │   go task1(), go task2()     │
        └──────────────┬───────────────┘
                       │ creates
                       ▼
                ┌──────────────┐
                │ Goroutines (G)│
                └──────┬───────┘
                       │ added to
                       ▼
        ┌──────────────────────────────┐
        │        Run Queues            │
        │  - Local Queue (per P)       │
        │  - Global Queue              │
        └──────────────┬───────────────┘
                       │ scheduled by
                       ▼
                ┌──────────────┐
                │ Processor (P)│
                │ (Scheduler)  │
                └──────┬───────┘
                       │ uses
                       ▼
                ┌──────────────┐
                │ Machine (M)  │
                │ OS Thread    │
                └──────┬───────┘
                       │ runs on
                       ▼
                     CPU Core

# 4. What is a Channel in Golang?
    ➤ A channel in Go is a communication mechanism used to safely pass data between goroutines. It allows goroutines to synchronize and exchange data without using explicit locks. Channels ensure that data is sent and received in a controlled and thread-safe manner.

    ```go
        ch := make(chan int)

        go func() {
            ch <- 10 // send data
        }()

        val := <-ch // receive data
    ```
# 5. Difference between buffered vs unbuffered channels in golang ?

    🔹 Buffered Channel
        ➤ A buffered channel has a fixed capacity.
        ➤ The sender can send data into the channel without waiting until the buffer becomes full.

        ➤ Once the buffer reaches its capacity, the sender will be blocked
        ➤ When the receiver reads a value, space is freed, and the sender can send more data
        
        ✅ Example Explanation
            ch := make(chan int, 6)

            If the channel capacity is 6:

            Sender can send 6 values without blocking
            If it tries to send the 7th value, it will block
            Once the receiver reads at least one value, the sender can send again

    🔹 Unbuffered Channel

        ➤ An unbuffered channel has no capacity (capacity = 0).
        ➤ It allows only one value transfer at a time, and both sender and receiver must be ready.

        ➤ The sender blocks until the receiver receives the value
        ➤ The receiver blocks until the sender sends a value
            
        ✅ Example Explanation
            ch := make(chan int)
            
            Sender sends one value
            Receiver must receive it immediately
            Only after receiving, the sender can send the next value

    