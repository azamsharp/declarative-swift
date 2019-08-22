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

//
//  GroceryCategory.swift
//  SectionsInCombine
//
//  Created by Mohammad Azam on 8/12/19.
//  Copyright © 2019 Mohammad Azam. All rights reserved.
//

import Foundation

struct GroceryCategory {
    let title: String
    let groceryItems: [GroceryItem]
}

extension GroceryCategory {
    
    static func all() -> [GroceryCategory] {
        
        return [GroceryCategory(title: "HEB", groceryItems: [GroceryItem(title: "Milk", price: 4.5),GroceryItem(title: "Cookies", price: 5.0)]), GroceryCategory(title: "Fiesta", groceryItems: [GroceryItem(title: "Fish", price: 10),GroceryItem(title: "Juice", price: 3.50)])]
        
    }
    
}

struct GroceryItem {
    let title: String
    let price: Double
}


```

```swift 
struct ContentView: View {
    
    private var groceryCategories = GroceryCategory.all()
    
    var body: some View {
        List {
            
            ForEach(self.groceryCategories, id: \.title) { gc in
                
                Section(header: Text(gc.title).font(.title)) {
                    ForEach(gc.groceryItems, id: \.title) { gi in
                        Text(gi.title)
                    }
                }
                
            }
            
        }.listStyle(GroupedListStyle())
    }
}
```
