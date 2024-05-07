---
layout: post
title: Hello World and the main function
---

The phenomenon of _Hello World_ as the first program in many programming books and tutorials has a deep-rooted meaning. It is the traditional way to introduce beginners to the syntax and structure of a new programming language. Writing out _Hello World_ is usually the simplest program that can be written in a language, so it serves as a gentle introduction.

The history of _Hello World_ dates back to the 1970s, when [Brian Kernighan](https://en.wikipedia.org/wiki/Brian_Kernighan) used this example in a guide to the B language. Later, it was also included in the book [Programming in C](https://www.amazon.com/Programming-Language-2nd-Brian-Kernighan/dp/0131103628) which he co-authored. This simple program has grown in popularity and has become a standard for teaching programming. It allows new programmers to quickly see how a computer performs an action on their command, which is very motivating at the beginning of learning programming.
<!--more-->
### _Hello World_ in Go

An example of a working _Hello World_ program in Go.

{% highlight go %}
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
{% endhighlight %}

To run the program, run the following command:

{% highlight shell %}
go run hello-world.go
{% endhighlight %}

You should get the following output:

{% highlight shell %}
Hello, World!
{% endhighlight %}

### The _main_ function in Go

Although the above program is very simple, we can learn a little about the syntax of the language and especially about the `main` function, which is used to run programs in Go.

1. `package main`
    * in Go, all source files must start with a `package` directive, which defines which package the file belongs to
    * `main` is a special package that tells the compiler that this code contains the entry point of the program, i.e. the `main` function
    * in the `main` package, the compiler expects a function with the same name (`main`), which makes it possible to run the entire program
2. `import "fmt"`
    * `import` is an instruction that incorporates other packages into the program, allowing you to use their functions and types
    * `"fmt"` is a standard Go package that includes functions for formatting and printing text
    * functions such as `fmt.Println` come specifically from this package
3. `func main()`
    * `func` is a keyword used to define functions
    * `main` is the name of a special function in Go that is automatically run when the program starts. It is the main entry point to the program, just like `main` in other languages such as C or Java
    * empty parenthesis `()` means that the `main` function does not take any arguments
    * no returned type(s) after the parenthesis means that the `main` function does not return any value
4. `fmt.Println("Hello, World!")`
    * `fmt.Println` is a function from the `fmt` package that prints the specified string to the standard output (console in this case) and adds a newline character at the end of the
    * `"Hello, World!"` is the string of characters (string) that will be printed out

If you already know a programming language, you will notice that the `main` function in Go:
* does not take arguments
* does not return a value

<div class="message">
  Is there a difference between arguments and parameters of a method?<br>
  <ul>
    <li>The <strong>parameters</strong> of a method are the names of the variables in its declaration/definition</li>
    <li>The <strong>arguments</strong> of a method are the names of the variables passed to it when it is called</li>
</ul>
</div>

Let's see how this is the case with the `main` function in C and Java, to then learn how to pass call arguments to the `main` function and how to code the program output.

### The _main_ function in C

{% highlight C %}
#include <stdio.h>

int main(int argc, char *argv[]) {
    printf("Hello, World!\n");
    return 0;
}
{% endhighlight %}

### The _main_ function in Java

{% highlight Java %}
public class HelloWorld {
    
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
{% endhighlight %}