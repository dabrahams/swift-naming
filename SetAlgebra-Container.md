---
layout: page
title: SetAlgebra / Container
---
`SetAlgebra` realized using container-like terms. 

## Usage

~~~swift
x = y.insertingContents(of: z)
y.insertContents(of: z)

x = y.removingElements(notIn: z)
y.removeElements(notIn: z)

x = y.removingElements(in: z)
y.removeElements(in: z)

x = y.insertingContents(removingCommonElementsOf: z)
y.insertContents(removingCommonElementsOf: z)
~~~

## Declaration

~~~swift
protocol SetAlgebra : Equatable, ArrayLiteralConvertible {
  func union(other: Self) -> Self
  func intersection(other: Self) -> Self
  func subtracting(other: Self) -> Self
  func symmetricDifference(of other: Self) -> Self

  mutating func formUnion(of other: Self)
  mutating func formIntersection(other: Self)
  mutating func subtract(other: Self)
  mutating func formSymmetricDifference(other: Self)

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
