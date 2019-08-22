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



import Foundation
import SwiftUI

struct Dish: Identifiable {
    
    let id = UUID()
    let name: String
    let price: Double
    let imageURL: String
    
}

extension Dish {
    
    static func all() -> [Dish] {
        
        return [
            Dish(name: "Filet Mignon", price: 35, imageURL: "e1"),
            Dish(name: "Spagetti Meatballs", price: 12, imageURL: "e2"),
            Dish(name: "Spagetti Meatballs", price: 12, imageURL: "e2"),
            Dish(name: "Sushi", price: 15, imageURL: "a1"),
            Dish(name: "Chocolate Cake", price: 8, imageURL: "d1"),
            Dish(name: "Lemon Cake", price: 10, imageURL: "d2"),
            Dish(name: "Spagetti Meatballs", price: 12, imageURL: "e2")
            
        ]
        
    }
    
}


```

```swift 


import Foundation

// https://www.hackingwithswift.com/example-code/language/how-to-split-an-array-into-chunks
extension Array {
    func chunked(into size: Int) -> [[Element]] {
        return stride(from: 0, to: count, by: size).map {
            Array(self[$0 ..< Swift.min($0 + size, count)])
        }
    }
}


```

```swift 

import SwiftUI

struct ContentView : View {
    
    let dishes = Dish.all()
    
    var body: some View {
        
        let chunkedDishes = dishes.chunked(into: 3)
        
        return List {
            
            // rows
            ForEach(0..<chunkedDishes.count) { index in
                
                HStack {
                    
                    ForEach(chunkedDishes[index]) { dish in
                        
                        Image(dish.imageURL)
                            .resizable()
                           // .frame(width: 150, height: 150)
                            .scaledToFit()
                        
                    }
                    
                }
                
            }
            
        }
        
    }
}
```
