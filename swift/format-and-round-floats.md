# Formatting & rounding floating-point numbers

To quickly format a `Double` or `Float` to a fixed number of decimal places using `String(format:)`.

```swift
let value = Double.pi

let text = String(format: "%.2f", value)
// "3.14"
```

`%.2f` means:

* `%` → start of format specifier
* `.2` → show **2 digits after the decimal**
* `f` → floating-point number

---

**Dynamic precision**

You can also control the precision at runtime:

```swift
let precision = 4
let value = Double.pi

let text = String(format: "PI = %.\(precision)f", value)
// "PI = 3.1416"
```

---

**Formatting vs rounding**

`String(format:)` only rounds the **displayed string**, not the number itself.

```swift
let value = Double.pi

let formatted = String(format: "%.2f", value)
// "3.14"

print(value)
// 3.141592653589793
```

---

**Actually rounding a Double**

If you want the *value itself* rounded:

```swift
let value = Double.pi
let rounded = (value * 100).rounded() / 100
// 3.14
```

Reusable helper:

```swift
extension Double {
    func rounded(to places: Int) -> Double {
        let factor = pow(10.0, Double(places))
        return (self * factor).rounded() / factor
    }
}

let rounded = Double.pi.rounded(to: 3)
// 3.142
```
