---
layout: page
title: SetAlgebra / Container
---

`SetAlgebra` realized using container-like terms. 

## Usage

~~~swift
var x: Set = [1], y: Set = [2], z: Set = [3]
let a = 10, b = 20, c = 30

x = y.insertingContents(of: z)
y.insertContents(of: z)

x = y.removingElements(notIn: z)
y.removeElements(notIn: z)

x = y.removingElements(in: z)
y.removeElements(in: z)

x = y.insertingContents(removingCommonElements: z)
y.insertContents(removingCommonElements: z)

if x.contains(c) { ... }

y.insert(a)
y.remove(b)

if x.allElementsAreContained(in: y) 
   && y.allElementsAndMoreAreContained(in: z)
   && z.hasNoElementsInCommon(with: x)
   && y.containsAllElements(of: z)
   && x.containsAllElementsAndMore(of: z)
   && !y.isEmpty { ... }
   
if Set.element(a, subsumes: b)
   && Set.element(b, isDisjointWith: c) { ... }
~~~

## Declaration

~~~swift
protocol SetAlgebra : Equatable, ArrayLiteralConvertible {
  func insertingContents(of other: Self) -> Self
  func removingElements(notIn other: Self) -> Self
  func removingElements(in other: Self) -> Self
  func insertingContents(removingCommonElements other: Self) -> Self

  mutating func insertContents(of other: Self)
  mutating func removeElements(notIn other: Self)
  mutating func removeElements(in other: Self)
  mutating func insertContents(removingCommonElement other: Self)

  associatedtype Element
  
  init()
  
  func contains(member: Element) -> Bool

  mutating func insert(member: Element)
  mutating func remove(member: Element) -> Element?

  func allElementsAreContained(in other: Self) -> Bool
  func allElementsAndMoreAreContained(in other: Self) -> Bool
  func hasNoElementsInCommon(with other: Self) -> Bool
  func containsAllElements(of other: Self) -> Bool
  func containsAllElementsAndMore(of other: Self) -> Bool

  var isEmpty: Bool { get }
  
  init<S : Sequence where S.Iterator.Element == Element>(_ sequence: S)

  static func element(a: Element, subsumes b: Element) -> Bool
  static func element(a: Element, isDisjointWith b: Element) -> Bool
}
~~~
