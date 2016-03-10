---
layout: page
title: Arithmetic
---
This is the `Arithmetic` protocol, using `formRemainder` for the mutating operation.  [^1]

## Usage


~~~swift
x = y.adding(z)
y.add(z)                              // y = y.adding(z)

x = y.subtracting(z)
y.subtract(z)                         // y = y.subtracting(z)

x = y.multiplied(by: z)
y.multiply(by: z)                     // y = y.multiplied(by: z)

x = y.divided(by: z)
y.divide(by: z)                       // y = y.divided(by: z)

x = y.remainder(dividingBy: z)
y.formRemainder(dividingBy: z)        // y = y.remainder(dividingBy: z)
~~~

## Declaration

~~~swift
protocol Arithmetic {
  func adding(other: Self) -> Self
  func subtracting(other: Self) -> Self
  func multiplied(by other: Self) -> Self
  func divided(by other: Self) -> Self
  func remainder(dividingBy rhs: Self) -> Self

  mutating func add(other: Self)
  mutating func subtract(other: Self)
  mutating func multiply(by other: Self)  
  mutating func divide(by other: Self)
  mutating func formRemainder(dividingBy other: Self)

  init()
}
~~~

[^1]: That’s  “arith-MEH-tic,” folks.
