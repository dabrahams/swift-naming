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
  func insertingContents(of other: Self) -> Self
  func removingElements(notIn other: Self) -> Self
  func removingElements(in other: Self) -> Self
  func insertingContents(removingCommonElementsOf other: Self) -> Self

  mutating func insertContents(of other: Self)
  mutating func removeElements(notIn other: Self)
  mutating func removeElements(in other: Self)
  mutating func insertContents(removingCommonElementsOf other: Self)

  associatedtype Element
  
  init()
  
  func contains(member: Element) -> Bool

  mutating func insert(x: Element)
  mutating func remove(possibleMember: Element) -> Element?

  func isSubset(of other: Self) -> Bool
  func isDisjoint(with other: Self) -> Bool
  func isSuperset(of other: Self) -> Bool

  var isEmpty: Bool { get }
  
  init<S : Sequence where S.Iterator.Element == Element>(_ sequence: S)

  static func element(a: Element, subsumes b: Element) -> Bool
  static func element(a: Element, isDisjointWith b: Element) -> Bool
}
~~~
