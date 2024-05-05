---
layout: post
title: Hello World - the main method
---

The phenomenon of "Hello, World!" as the first program in many programming books and tutorials has a deep-rooted meaning. It is the traditional way to introduce beginners to the syntax and structure of a new programming language. Writing out "Hello, World!" is usually the simplest program that can be written in a language, so it serves as a gentle introduction.

The history of "Hello, World!" dates back to the 1970s, when Brian Kernighan used this example in a guide to the B language. Later, it was also included in the book ["Programming in C"](https://www.amazon.com/Programming-Language-2nd-Brian-Kernighan/dp/0131103628) which he co-authored. This simple program has grown in popularity and has become a standard for teaching programming. It allows new programmers to quickly see how a computer performs an action on their command, which is very motivating at the beginning of learning programming.

### Hello World in Go

{% highlight go %}
package main

import "fmt"

func main() {
	fmt.Println("Hello, World!")
}
{% endhighlight %}

