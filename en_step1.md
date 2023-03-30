## Scenario 1: Use Struct Embedding to Reuse Code

#### Objective: Use struct embedding to reuse code and avoid duplication.

**Scenario**: Imagine that you're developing a Go application that involves creating different types of users with different permissions. You want to write code that is reusable and avoids duplication.

To achieve this, you can use struct embedding. You can define a User struct that contains fields that are common to all types of users:
Firstly, we need to install Go.

`apk add go`

We will use "Vim Editor" when creating pages. Let's take a quick look at shortcuts.

:q = Closes the Vim editor if the changes are saved. Otherwise, it will warn you.

:q! = Closes the editor directly without saving.

:w = Saves the changes made.

:wq = Saves the changes made and exits.

Then, let's create the first page named "hello.go" in the vim editor.

`vim struct.go`

To be able to work on the opened page, let's activate the "Insert Mode" by pressing the "i" key and write the code we want to run on the page.

```
package main

type User struct {
ID int
Name string
Email string
}
```

You can then define other structs that embed the User struct and add fields that are specific to each type of user. For example, here's code that defines a Admin struct that embeds the User struct and adds an IsAdmin field:

```
package main

import "fmt"

type User struct {
ID int
Name string
Email string
}

type Admin struct {
User
IsAdmin bool
}

func main() {
user := User{ID: 1, Name: "Vakkas Sahin", Email: "vakkas.sahin@example.com"}
admin := Admin{User: user, IsAdmin: true}
fmt.Printf("User: %+v\n", user)
fmt.Printf("Admin: %+v\n", admin)
}
```

This code defines an Admin struct that embeds the User struct and adds an IsAdmin field. It also includes a main() function that creates a User struct and an Admin struct, and prints the values of these structs using the %+v format verb to show all fields and their values.

You can save this code in a file named struct.go, and then execute it in a terminal screen using the go run command:

`go run struct.go`

```
User: {ID:1 Name:Vakkas Sahin Email:vakkas.sahin@example.com}
Admin: {User:{ID:1 Name:Vakkas Sahin Email:vakkas.sahin@example.com} IsAdmin:true}
```

Using struct embedding in this way makes your code more reusable and avoids duplication. You can define common fields and behavior in a base struct and embed it in other structs to reuse that code. This can make your code easier to read, write, and maintain.

Now, we can continue.
