# Class/UML diagram
Topic: Database, Django models, Design  
Difficulty: :star: :star: :star: 

## Class/UML diagram to django models
Let's start with a given UML diagram, shown below. It has four tables and every table as some basic columns.
```mermaid
classDiagram
    Store "n"o--"m" Product : is available in
    Location "1"o--"n" Store : is located at
    Location "1"o--"n" Factory : is located at
    Product "1"o--"n" Factory : produces
    
    class Location {
            String country
            String city
     }
    class Factory {
        String street
 }
    class Store {
        String street
    }
    class Product {
        String name
        Float price
    }
```

### Exercises

* Write the **django** models, which implement the diagram
* Is there any optimization, which could be done?