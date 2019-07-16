# Swift-Fundamentals-3
Swift Fundamentals 3 - guard let, optional chaining, nil coalescing, class inheritance and composition, downcast types
## At the end of this module, you should be able to:

## use a guard let statement to early exit
```Swift
import UIKit
func withdrawMoney(amountString: String) {
    
    guard let amount = Double(amountString), amount > 0 else {
        print("Invalid amount to withdraw \(amountString)")
        return
    }
    
    print("Processing request to withdraw \(amount) dollars from bank account.")
}

withdrawMoney(amountString: "abc")
withdrawMoney(amountString: "-34")
withdrawMoney(amountString: "150")
```

## use optional chaining to short circuit evaluation when a value is nil
```Swift
class Kitchen {
    var oven: Oven?
    
    func sweeoFloor() {
        print("Sweeping the floor")
    }
}

class Oven {
    func bakeFood() {
        print("Baking food!")
    }
    
}

var kitchen: Kitchen? = nil

kitchen?.sweeoFloor()
kitchen?.oven?.bakeFood()

kitchen = Kitchen()
kitchen?.sweeoFloor()

kitchen?.oven = Oven()
kitchen?.oven?.bakeFood()
```
## use the nil coalescing operator to provide a default value when an expression is nil
```Swift
let userInput: String = "44"


// Try to convert userInput, or use 0 as a default value
let numberOfDogs = Int(userInput) ?? 0

print("numberOfDog: \(numberOfDogs)")

var wordOfTheDay: String? = "Butterfly"

var numberOfLetters = wordOfTheDay?.count ?? 0

print("The word of the day, \(wordOfTheDay ?? "") has \(numberOfLetters) letters")
```

##use class inheritance and composition
```Swift
class Shape {
    var color: String
    var position: CGPoint
    
    
    init(color: String, position: CGPoint = CGPoint.zero) {
        self.color = color
        self.position = position
    }
}

class Square: Shape {
    var edgeWidth: Double
    
    init(color: String, edgeWidth: Double) {
        self.edgeWidth = edgeWidth
        super.init(color: color)
    }
}

class Rectangle: Shape {
    var width: Double
    var height: Double
    
    init(color: String, width: Double, height: Double) {
        self.width = width
        self.height = height
        super.init(color: color)
    }
}

let shape = Shape(color: "Green")
let square = Square(color: "Red", edgeWidth: 5)
let rectangle = Rectangle(color: "Blue", width: 3, height: 7)

var shapes: [Shape] = []

shapes.append(contentsOf: [square, rectangle, shape])

for shape in shapes {
    print(shape.color)
}
```
## downcast types from super classes to subclasses using `as?` or `as!`
```Swift
for shape in shapes {
    if let square = shape as? Square {
        print("\(square.color) square with edge width: \(square.edgeWidth)")
    } else if let rectangle = shape as? Rectangle {
        print("\(rectangle.color) rectangle with edge width: \(rectangle.width) and height: \(rectangle.height)")
    } else {
        print("It is a \(shape.color) shape!")
    }
}

var someShape: Shape

someShape = Rectangle(color: "Orange", width: 50, height: 40)


// Force Downcasting is dangerous!!!!!!!!!
let orangeRectangle = someShape as! Rectangle
print("It's an \(orangeRectangle.color) rectangle!")

let someString = "123"
let myNumber = Int(someString)
```
