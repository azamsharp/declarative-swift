
```swift
struct ContentView: View {
    
    @State private var showModal: Bool = false
    
    var body: some View {
        Button("Show Modal") {
            self.showModal.toggle()
        }.sheet(isPresented: $showModal) {
            Text("I am a Modal")
        }
    }
}

```
