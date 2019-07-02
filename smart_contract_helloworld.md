Hello, World example
 
    // File: test.tgo
    // Message: string
    // Success: bool
     
    even := import("even")
     
    default := func() {
        str := "Hello, World!"
        even.println(str)
    }
