# Hash Map Implementation Example in Go (Map)

In Go, this structure is called a **`map`**.

```go
package main

import "fmt"

func main() {
    // 1. Creating a Hash Map (map)
    // Key will be a string (name), and Value will be an int (phone number).
    phoneBook := make(map[string]int)

    // 2. Adding Data (Key and Value)
    phoneBook["Mehmet"] = 5411234567
    phoneBook["Ayşe"] = 5329876543
    phoneBook["Ali"] = 5550001122

    fmt.Println("--- Data in the Phone Book ---")
    fmt.Println(phoneBook)

    // 3. Instant Data Access (Lookup)
    fmt.Println("\n--- Lookup Example ---")
    // The system takes the name "Mehmet," hashes it, and instantly retrieves the number.
    mehmetNumber := phoneBook["Mehmet"]
    fmt.Println("Mehmet's Number:", mehmetNumber)

    // 4. Deleting Data
    delete(phoneBook, "Ali")
    fmt.Println("\n--- After Deletion ---")
    fmt.Println("Ali was deleted. Current status of the phone book:", phoneBook)
}
```