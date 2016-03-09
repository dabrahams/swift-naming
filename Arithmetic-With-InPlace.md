---
layout: page
title: Arithmetic / InPlace
---
This is the `Arithmetic` protocol, using an `InPlace` suffix.[^1]

Usage
-----

~~~swift
x = y.adding(z)
y.addInPlace(z)                       // y = y.adding(z)

x = y.subtracting(z)
y.subtractInPlace(z)                  // y = y.subtracting(z)

x = y.multiplied(by: z)
y.multiplyInPlace(by: z               // y = y.multiplied(by: z)

x = y.divided(by: z)
y.divideInPlace(by: z)                // y = y.divided(by: z)

x = y.remainder(dividingBy: z)
y.remainderInPlace(dividingBy: z)     // y.remainder(dividingBy: z)
~~~

Declaration
-----------

~~~swift
protocol Arithmetic {
  func adding(other: Self) -> Self
  func subtracting(other: Self) -> Self
  func multiplied(by other: Self) -> Self
  func divided(by other: Self) -> Self
  func remainder(dividingBy rhs: Self) -> Self

  mutating func addInPlace(other: Self)
  mutating func subtractInPlace(other: Self)
  mutating func multiplyInPlace(by other: Self)  
  mutating func divideInPlace(by other: Self)
  mutating func remainderInPlace(dividingBy other: Self)

  init()
}
~~~

[^1]: That’s  “arith-MEH-tic,” folks.
