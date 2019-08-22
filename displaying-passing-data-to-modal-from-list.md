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
    @State private var selectedFlag: String = ""
    
    let flags = ["🇦🇽","🇩🇿","🇵🇰","🇺🇸","🇹🇷","🇧🇷"]
    
    
    var body: some View {
        
        List {
            
            ForEach(0..<self.flags.count, id: \.self) { index in
                
                HStack {
                    Text(self.flags[index])
                        .font(.custom("Arial",size: 100))
                    Text("Flag \(index)")
                }.onTapGesture {
                    self.showModal.toggle()
                    self.selectedFlag = self.flags[index]
                }
                
            }
            
        }.sheet(isPresented: self.$showModal) {
            Text(self.selectedFlag)
                .font(.custom("Arial",size: 200))
        }
    }
}

```
