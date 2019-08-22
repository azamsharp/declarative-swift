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

## Searching in SwiftUI List Using UISearchBar 

```swift
//
//  SearchBar.swift
//  SearchingInList
//
//  Created by Mohammad Azam on 8/21/19.
//  Copyright © 2019 Mohammad Azam. All rights reserved.
//

import Foundation
import SwiftUI

struct SearchBar: UIViewRepresentable {
    
    @Binding var text: String
    
    class Coordinator: NSObject, UISearchBarDelegate {
        
        @Binding var text: String
        
        init(text: Binding<String>) {
            _text = text
        }
        
        func searchBar(_ searchBar: UISearchBar, textDidChange searchText: String) {
            text = searchText
        }
        
    }
    
    func makeCoordinator() -> SearchBar.Coordinator {
        return Coordinator(text: $text)
    }
    
    func makeUIView(context: UIViewRepresentableContext<SearchBar>) -> UISearchBar {
        let searchBar = UISearchBar(frame: .zero)
        searchBar.delegate = context.coordinator
        return searchBar
    }
    
    func updateUIView(_ uiView: UISearchBar, context: UIViewRepresentableContext<SearchBar>) {
        uiView.text = text 
    }
    
}

```


```swift
struct ContentView: View {
    
    @State private var searchTerm: String = ""
    
    let names = ["Azam","Jake","Alex","Mary","Jack","Jerry"]
    
    var body: some View {
        List {
            
            SearchBar(text: $searchTerm)
            
            ForEach(self.names.filter {
                self.searchTerm.isEmpty ? true :
                    $0.localizedCaseInsensitiveContains(self.searchTerm)
            }, id: \.self) { name in
                Text(name)
            }
            
        }
    }
}
```
