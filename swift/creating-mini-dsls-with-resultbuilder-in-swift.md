# Creating Mini DSLs with `@resultBuilder` in Swift

Swift's `@resultBuilder` allows you to define custom declarative syntax, just like SwiftUI. You can use it to build mini DSLs for things like HTML, config files, UI, or structured data.

---

### 🧪 Example: HTML Builder

```swift
@resultBuilder
struct HTMLBuilder {
    static func buildBlock(_ components: String...) -> String {
        components.joined(separator: "\n")
    }
}

@HTMLBuilder func page() -> String {
    "<html>",
    "<body>",
    "<h1>Hello, TIL!</h1>",
    "</body>",
    "</html>"
}

print(page())
```

## 🧠 Why It's Cool

- Gives your functions a **declarative style**.
- Powers frameworks like **SwiftUI** and **Swift Argument Parser**.
- Great for building custom structured languages in your code.

## 🔖 Pro Tip

You can add support for `if`, `for`, and `switch` blocks by implementing more static functions in your builder (`buildOptional`, `buildEither`, `buildArray`, etc).