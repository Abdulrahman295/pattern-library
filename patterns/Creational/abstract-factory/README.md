
# Abstract Factory

## Introduction

One common creational pattern in JavaScript is the Factory Method pattern. It defines an interface for creating an object but lets subclasses decide which class to instantiate. This pattern is particularly useful when you have a set of related classes and you want to abstract away the instantiation logic from the client.

Here's an example of the Factory Method pattern in JavaScript:

### 1. Item Interface Definition 

First of all, we upgrade it to `Item class`, which will function as a means of accessing our items. And, in the case of Java and TypeScript, we would apply an interface that is not available in JavaScript; therefore, we use a base class. This place shows a constructor that uses the name of the item as an argument and the `display()` function, which displays the item name.

```javascript
class Item {
    constructor(name) {
        this.name = name;
    }

    display() {
        console.log(`Item: ${this.name}`);
    }
}
```

### 2. Concrete Item Classes

Then, two subclasses `ConcreteItem1` and `ConcreteItem2` are derived from the class Item. Both of which inherit its functionality and properties. Here, you can find a collection of different types of classes that is presented in an easy-to-grasp way. When inheriting Item, the classes receive its constructor and display (unspecified) method, but the parameter passed in the constructor of each concrete class, which calls the base class implementation `ConcreteItem1` or `ConcreteItem2`, determines its item name.

```Javascript
class ConcreteItem1 extends Item {
    constructor() {
        super("ConcreteItem1");
    }
}

class ConcreteItem2 extends Item {
    constructor() {
        super("ConcreteItem2");
    }
}
```

### 3. Class Creator

The `Creator class` – `(createItem(type))` - is the key of the Factory Method pattern. A method of this sort accepts a type parameter and subsequently decides which class of item to create and return based on its type. If the grouping does not belong to the category of the user, an error is displayed.

```Javascript
class Creator {
    createItem(type) {
        let item;
        switch (type) {
            case "type1":
                item = new ConcreteItem1();
                break;
            case "type2":
                item = new ConcreteItem2();
                break;
            default:
                throw new Error("Invalid Item Type");
        }
        return item;
    }
}
```

### 4. Use

Finally, the `Creator` class holds information that is used to generate item instances. The `Creator` class is made. Its `createItem()` method is invoked, and the different items are passed as parametres. It underlines two essential things: hiding the process of construction of different items from the client and the ability to do it without any knowledge of concrete classes. The created items are then used as arguments for the `display()` method, whose implementation prints the item's name in the console.

```Javascript
const creator = new Creator();
const item1 = creator.createItem("type1");
item1.display(); 
// Output: Item: ConcreteItem1

const item2 = creator.createItem("type2");
item2.display(); 
// Output: Item: ConcreteItem2
```

This way of separating the code responsible for making a particular object type and the code that uses this object is very convenient, facilitating object code maintenance and large-scale code extension.

## Source Code

[Java Script Code](./abstract-factory.js)  

## References

[GeeksforGeeks - Abstract Factory Pattern](https://www.geeksforgeeks.org/abstract-factory-pattern/)

[Refactoring Guru - Abstract Factory Design Pattern](https://refactoring.guru/design-patterns/abstract-factory)
