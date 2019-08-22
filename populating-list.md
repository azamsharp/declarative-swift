
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

## List

```swift
struct ContentView: View {
    
    let animals = ["🐈","🦒","🐀","🐆","🦏","🐪"]
    
    var body: some View {
        List(self.animals, id: \.self) { animal in
            Text(animal)
                .font(.custom("Arial",size: 100))
        }
    }
}
```

## List Using ForEach 

```swift

struct ContentView: View {
    
    let animals = ["🐈","🦒","🐀","🐆","🦏","🐪"]
    
    var body: some View {
        List {
            
            Text("Here you can display a view")
            
            ForEach(self.animals,id: \.self) { animal in
                Text(animal)
                    .font(.custom("Arial",size: 100))
            }
            
            Text("Here you can display another")
        }
    }
}

```
