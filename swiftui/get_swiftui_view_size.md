# Get the size of a SwiftUI view

To figure out the size of a view in SwiftUI, you can use the [GeometryReader](https://developer.apple.com/documentation/swiftui/geometryreader). However, instead of embedding the `GeometryReader` directly around the view you want to measure (which can interfere with the view’s layout), use it within the `background` modifier. This approach allows you to access the size without modifying the layout of the original view.

```
@State private var size: CGSize = .zero

struct ContentView: View {
    var body: some View {
        Text("Size: \(size.width) x \(size.height)")
            .background(
                GeometryReader { proxy in
                    Color.clear.onAppear {
                        size = proxy.size
                    }
                }
            )
    }
}
```

## Why this works:

By placing the `GeometryReader` in the `background, you are able to read the size of the view while keeping the layout of your original content intact. The `Color.clear` ensures there’s no visual impact, and `onAppear` ensures that the size is captured once the view is rendered.
