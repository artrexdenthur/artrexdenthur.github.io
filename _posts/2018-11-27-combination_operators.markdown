---
layout: post
title:      "Combination Operators"
date:       2018-11-27 23:25:25 +0000
permalink:  november_27_combination_operators
---


One of the great puzzles in designing a readable programming language is setting the right balance between readability in compactness. On one extreme, 'readability' can go so far that code is too verbose to actually read (and especially write) quickly. On the other, intentionally making code compact eventually results in longer periods for both reading and writing as well, since compressed symbols become arbitrary and difficult to remember.

One of my favorite readable compressions of symbols is the double operator, a pattern which is used in various languages and not just Ruby. Ruby specifically uses the generally applied suite of assignment operators which combine the = operator with another operator to expand like this:
`x (op)= y #=> x = x (op) y`
The most elementary use of this would be for iterators, for instance:

```
x = 0
while x < 10
  x += 1
end
```

This construction saves only a few characters in this case, but sacrifices almost no readability thanks in part to the widespread acceptance of this idiom across languages. Therefore even the more uncommon examples like %= read easily and are quickly called to mind. This specific construction also sees much use, even in Ruby where enumerables can often take its place.

But the double operator also takes another excellent form in Ruby. The ||= operator is the first example of Ruby's boolean assignment operators I came across, and it functions like this (at least for local variables):

`x ||= y #=> x || x = y`

The specific use case that I found it for streamlines the simple task of creating an empty variable for a loop, where code like this:

```
x = []
array.each do |string|
  # string operations...
  x << string
end
```

Can become:

```
array.each do |string|
  x ||= []
  # string operations...
  x << string
end
```

Making it just slightly clearer that the x array is meant specifically as a tool for the loop.

An even more clever use of this operator, however, is as a Ruby-native version of one of the best-loved Haskell monads: the 'maybe' monad. The full definition of a monad is a topic for another day, but the upshot of the maybe monad is that it is meant to gracefully handle values that may not exist and functions that may fail. Functions that return nil upon failure, in particular, can be used in combination with ||= and &&= to replace if...else statements with a more functional flair:

```
def chained_functions(input)
  a = try_this_first(input)
  a ||= try_this_on_failure(input)
  a ||= try_one_last_thing_if_nec(input)
end
```

The three 'try' functions are prioritized, and the later ones are only called if the earlier ones failed. All this is done in just a few lines, and with a functional paradigm reminiscent of the maybe monad.
