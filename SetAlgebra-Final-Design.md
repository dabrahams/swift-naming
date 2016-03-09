---
layout: page
title: SetAlgebra / Final
---
This is what Tony announced to swift-evolution as our final decision.[^1]

## Usage

~~~swift
x = y.insertingContents(of: z)
y.insertContents(of: z)         // y = y.insertingContents(of: z)

x = y.intersection(z)
y.intersect(z)                  // y = y.intersection(z)

x = y.removingContents(of: z)
y.removeContents(of: z)         // y = y.removingContents(of: z)

x = y.invertingIntersection(z)
y.invertIntersection(z)         // y = y.invertingIntersection(z)
~~~

## Declaration

~~~swift
protocol SetAlgebra : Equatable, ArrayLiteralConvertible {
  func insertingContents(of other: Self) -> Self
  func intersection(other: Self) -> Self
  func invertingIntersection(other: Self) -> Self
  func removingContents(of other: Self) -> Self

  mutating func insertContents(of other: Self)
  mutating func intersect(other: Self)
  mutating func invertIntersection(other: Self)  
  mutating func removeContents(of other: Self)

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
~~~

[^1]: The only change is that we added the preposition splitting specified by the guidelines and implemented by the importer, i.e. `x.isSubset(of: y)` rather than `x.isSubsetOf(y)`.
