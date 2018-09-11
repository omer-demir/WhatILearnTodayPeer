# Swift

## Constants / Variables

**let** constant and immutable
**var** mutable variable

### Optionals

```swift
var s1:String
var s2:String?
var s3:String!
```

s1 will be just string. s2 will become a value either nil or value *Optional (value)* . s3 will be either nil or value
for s2 you need to unwrap it with **!** but for s3 you dont need to

## Value and Reference Types

Value types are 
- Structures
- Enums
- Tuples

References are
- Functions
- Classes

```swift
mport UIKit

class Person{
    var firstName:String
    var lastName:String
    var enumarationUsage:EnumTest
    
    enum EnumTest:Int{
        case Enum1
        case Enum2
        
        public func stringRepresentation()->String{
            switch self {
            case .Enum1:
                return "Enum1"
            case .Enum2:
                return "Enum2"
            }
        }
    }
    
    init(firstName:String,lastName:String) {
        self.firstName=firstName
        self.lastName=lastName
        self.enumarationUsage=EnumTest.Enum1
        
        self.enumarationUsage.stringRepresentation()
    }
    
    //Instance scope function
    func fullName() -> String {
        return "\(self.firstName) \(self.lastName)"
    }
    
    class func fullName2(person:Person) -> String {
        return "\(person.firstName) \(person.lastName)"
    }
    
    class func fullName3(person p :Person) -> String {
        return "\(p.firstName) \(p.lastName)"
    }
    
    //Closure usage
    class func closure() {
        var list=["first","ss","third","second"]
        
        list.filter(){(name:String)->Bool in
            return name.hasPrefix("L")
        }
        
        list.filter(){(name)->Bool in
            return name.hasPrefix("L")
        }
        
        list.filter(){name->Bool in
            name.hasPrefix("L")
        }
        
        list.filter(){$0.hasPrefix("L")}
    }
    
    //Class scope function
    class func fullName()->String{
        return "Hi world"
    }
}

extension String{
    func reverse()->String{
        return self;
    }
}

let kamil=Person(firstName:"kamil",lastName:"mehmet")
print(kamil.fullName())

print("Mehmet".reverse())

Person.fullName()
Person.closure()
```

## Protocols

It is much like data contracts. In other terms interface

## Properties

Stored vs Computed
Type vs Instance
```swift
struct CardDeck{
    static let count=52 //this is type prop
}

class Person{
    class var count:Int //this type prop
    var speed {
        willSet{
            //this is for observer
        }
        didSet{
            //this is for observer
        }
    }

    lazy var dbConnection:Connection=Connection()
}
```

## Generic

```swift
struct Dictionary<Key:Hashable,Value>{}
```

## Types

### Array

```swift

let user = ["Alie","Jason","John"]

names[1..<3] // will return Jason and john

user.sorted(){$0<$1} //immutable
user.sort() // mutate the resut

```