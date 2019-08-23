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

import SwiftUI

struct ContentView: View {
    
    @State private var isActive: Bool = false
    
    var body: some View {
        
        NavigationView {
            
        VStack {
                
            NavigationLink(destination: Text("Page 2"), isActive: self.$isActive) {
                Text("")
            }
            
            Button("Go to page 2") {
                self.isActive = true
            }
        }
        }
    }
}


```
