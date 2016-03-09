`SetAlgebra` realized using an `InPlace` suffix. 

## Usage

```swift
x = y.union(z)
y.unionInPlace(of: z)                    // y = y.union(z)

x = y.intersection(z)
y.intersectionInPlace(z)                 // y = y.intersection(z)

x = y.subtracting(z)
y.subtractInPlace(z)                     // y = y.subtracting(z)

x = y.symmetricDifference(z)
y.symmetrictDifferenceInPlace(z)         // y = y.symmetricDifference(z)
```

## Declaration

```swift
protocol SetAlgebra : Equatable, ArrayLiteralConvertible {
  func union(other: Self) -> Self
  func intersection(other: Self) -> Self
  func subtracting(other: Self) -> Self
  func symmetricDifference(of other: Self) -> Self

  mutating func unionInPlace(of other: Self)
  mutating func intersectionInPlace(other: Self)
  mutating func subtractInPlace(other: Self)  
  mutating func symmetricDifferenceInPlace(other: Self)

  // --- names in question end here ---

  associatedtype Element
  
  init()
  
  func contains(member: Element) -> Bool

  mutating func insert(member: Element)
  mutating func remove(member: Element) -> Element?

  func isSubset(of other: Self) -> Bool
  func isDisjoint(with other: Self) -> Bool
  func isSuperset(of other: Self) -> Bool

  var isEmpty: Bool { get }
  
  init<S : Sequence where S.Iterator.Element == Element>(_ sequence: S)

  static func element(a: Element, subsumes b: Element) -> Bool
  static func element(a: Element, isDisjointWith b: Element) -> Bool
}
```