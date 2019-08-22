<style>
    #header {
    display:none; 
  }
    
section #title .credits.right {
    display:none; 
}

section #title .credits.left {
    display:none; 
}
    
  </style>


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
