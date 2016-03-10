---
layout: page
title: SetAlgebra / Math
---

`SetAlgebra` realized using math terms. 

## Usage

~~~swift
var x: Set = [1], y: Set = [2], z: Set = [3]
let a = 10, b = 20, c = 30

x = y.union(z)
y.formUnion(z)                         // y = y.union(z)

x = y.intersection(z)
y.formIntersection(z)                 // y = y.intersection(z)

x = y.subtracting(z)
y.subtract(z)                         // y = y.subtracting(z)

x = y.symmetricDifference(z)
y.formSymmetrictDifference(z)         // y = y.symmetricDifference(z)

if x.contains(c) { ... }

y.insert(a)
y.remove(b)

if x.isSubset(of: y) 
   && y.isStrictSubset(of: z)
   && z.isDisjoint(with: x)
   && y.isSuperset(of: z)
   && x.isStrictSuperset(of: z)
   && !y.isEmpty { ... }
   
if Set.element(a, subsumes: b)
   && Set.element(b, isDisjointWith: c) { ... }
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
  func isStrictSubset(of other: Self) -> Bool
  func isDisjoint(with other: Self) -> Bool
  func isSuperset(of other: Self) -> Bool
  func isStrictSuperset(of other: Self) -> Bool

  var isEmpty: Bool { get }
  
  init<S : Sequence where S.Iterator.Element == Element>(_ sequence: S)

  static func element(a: Element, subsumes b: Element) -> Bool
  static func element(a: Element, isDisjointWith b: Element) -> Bool
}
~~~
