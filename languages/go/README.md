# Go Lang

In order to understand **Go**, we should see first C++. Because we can safely assume that Go is a language with better threading and distributed programming c++

## Declarations and basics

You can define variables on global scope or functional scope.

**Hint**

If you define your variable at functional level with value, you need to use. Otherwise compiler will give an error about that.

*Example*
```go
package main

import (
	"fmt"
	"reflect"
)

// this is package level variable
// var (
// 	name, course string
// 	module       float64
// )

// this is package level variable
// var (
// 	name, course, module = "Nigel", "Docker deep dive", 3.2
// )

func main() {
	name := "Nigel"

	// If the variable is not used then it will give compiler error
	// course := "Docker deep dive"

	module := 3.2

	fmt.Println("Name value is set to", name, "and the type is", reflect.TypeOf(name))
	fmt.Println("Module value is set to", module, "and the type is", reflect.TypeOf(module))
}
```

## Pointers and References

Like C++, GO has pointers and references. It works the same logic in C++. 

*Example*
```go
package main

import (
	"fmt"
)

func main() {

	module := 3.4
	ptr := &module

	course := "Docker deep dive"

	fmt.Println("Welcome to pointers")
	fmt.Println("The address of the vlaue", &module)
	fmt.Println("The address of the vlaue", ptr)
	fmt.Println("The address of the pointer of pointer", &ptr)
	fmt.Println("The vlaue with dereferencing", *ptr)

	fmt.Println("\nHi you are watching", course)

	changeCourse(&course)

	fmt.Println("\nHi you are watching different one", course)
}

func changeCourse(course *string) string {
	*course = "c# deep dive"

	fmt.Println("New course is", *course)

	return *course
}

```

### Function definition

```go
package main

import (
	"fmt"
	"strings"
)

func main() {
	module := "Docker"
	course := "Deep dive docker"

	fmt.Println(converter(module, course))
}

func converter(module string, course string) (s1 string, s2 string) {
	module = strings.Title(module)
	course = strings.ToUpper(course)

	return module, course
}

```