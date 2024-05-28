---
layout: post
title: Exploring the defer keyword
---

The Go programming language, also known as Golang, offers various features that make it a compelling choice for many developers. One such feature is the `defer` keyword, which provides a mechanism to ensure that certain statements are executed at the end of the function, regardless of how the function exits. In this article, we'll explore how `defer` works, its use cases, and provide examples to illustrate its functionality.
<!--more-->
## What is `defer`?

The `defer` keyword in Go is used to postpone the execution of a function or statement until the surrounding function returns. This is particularly useful for tasks such as resource cleanup, closing files, or handling any kind of cleanup that should happen after the function completes.

### How `defer` Works

When you declare a `defer` statement, Go schedules the deferred function call to be executed just before the surrounding function returns. If multiple `defer` statements are present, they are executed in a last-in, first-out (LIFO) order.

### Basic Example

Here's a simple example to demonstrate the basic usage of `defer`:

```go
package main

import (
    "fmt"
)

func main() {
    fmt.Println("Start")
    defer fmt.Println("Deferred statement")
    fmt.Println("End")
}
```

**Output:**
```
Start
End
Deferred statement
```

In this example, the "Deferred statement" is printed after "End", even though the `defer` statement appears before it in the code.

### Multiple `defer` Statements

When multiple `defer` statements are used, they are executed in reverse order of their appearance:

```go
package main

import (
    "fmt"
)

func main() {
    defer fmt.Println("First")
    defer fmt.Println("Second")
    defer fmt.Println("Third")
    fmt.Println("Start")
}
```

**Output:**
```
Start
Third
Second
First
```

## Practical Use Case: Timing Function Execution

One practical use case for `defer` is to measure the execution time of a function. This can be particularly useful for performance monitoring and debugging.

### Example 1: Passing Time as Parameter

In this example, we pass the start time as a parameter to the deferred function:

```go
package main

import (
    "fmt"
    "time"
)

func trackTime(name string, start time.Time) {
    elapsed := time.Since(start)
    fmt.Printf("%s took %s\n", name, elapsed)
}

func exampleFunction() {
    defer trackTime("exampleFunction", time.Now())
    time.Sleep(2 * time.Second) // Simulate function work
}

func main() {
    exampleFunction()
}
```

In this code, `trackTime` is deferred in the `exampleFunction`. The `time.Now()` captures the start time, and when the function completes, `trackTime` calculates and prints the elapsed time.

### Example 2: Returning a Function to Track Time

This example demonstrates a more sophisticated approach where the timing function returns a closure that captures the start time:

```go
package main

import (
    "fmt"
    "time"
)

func trackExecutionTime(name string) func() {
    start := time.Now()
    return func() {
        elapsed := time.Since(start)
        fmt.Printf("%s took %s\n", name, elapsed)
    }
}

func anotherExampleFunction() {
    defer trackExecutionTime("anotherExampleFunction")()
    time.Sleep(3 * time.Second) // Simulate function work
}

func main() {
    anotherExampleFunction()
}
```

In this version, `trackExecutionTime` captures the start time and returns a function that calculates and prints the elapsed time when called. This returned function is then deferred in `anotherExampleFunction`.

## Conclusion

The `defer` keyword in Go is a powerful tool that allows developers to write cleaner and more maintainable code, especially when dealing with resource management and cleanup tasks. By deferring function calls, you can ensure that certain operations are performed no matter how the function exits. Additionally, `defer` can be effectively used to measure the execution time of functions, aiding in performance monitoring and optimization.

Understanding and utilizing `defer` effectively can greatly enhance the quality and reliability of your Go programs. Whether you're cleaning up resources or timing function execution, `defer` offers a concise and robust solution.