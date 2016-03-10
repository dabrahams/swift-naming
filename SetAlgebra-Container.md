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

x = y.removingContents(notInCommonWith: z)
y.removeContents(notInCommonWith: z)

x = y.removingContents(inCommonWith: z)
y.removeContents(inCommonWith: z)

x = y.insertingContents(removingCommonContents: z)
y.insertContents(removingCommonContents: z)

if x.contains(c) { ... }

y.insert(a)
y.remove(b)

if x.allContentsAreContained(in: y) 
   && y.allContentsAndMoreAreContained(in: z)
   && z.hasNoContentsInCommon(with: x)
   && y.containsAllContents(of: z)
   && x.containsAllContentsAndMore(of: z)
   && !y.isEmpty { ... }
   
if Set.element(a, implies: b)
   && Set.element(b, doesNotOverlap: c) { ... }
~~~

## Declaration

~~~swift
protocol SetAlgebra : Equatable, ArrayLiteralConvertible {
  func insertingContents(of other: Self) -> Self
  func removingContents(notInCommonWith other: Self) -> Self
  func removingContents(inCommonWith other: Self) -> Self
  func insertingContents(removingCommonContents other: Self) -> Self

  mutating func insertContents(of other: Self)
  mutating func removeContents(notInCommonWith other: Self)
  mutating func removeContents(inCommonWith other: Self)
  mutating func insertContents(removingCommonContents other: Self)

  associatedtype Element
  
  init()
  
  func contains(member: Element) -> Bool

  mutating func insert(member: Element)
  mutating func remove(member: Element) -> Element?

  func allContentsAreContained(in other: Self) -> Bool
  func allContentsAndMoreAreContained(in other: Self) -> Bool
  func hasNoContentsInCommon(with other: Self) -> Bool
  func containsAllContents(of other: Self) -> Bool
  func containsAllContentsAndMore(of other: Self) -> Bool

  var isEmpty: Bool { get }
  
  init<S : Sequence where S.Iterator.Element == Element>(_ sequence: S)

  static func element(a: Element, implies b: Element) -> Bool
  static func element(a: Element, doesNotOverlap b: Element) -> Bool
}
~~~
